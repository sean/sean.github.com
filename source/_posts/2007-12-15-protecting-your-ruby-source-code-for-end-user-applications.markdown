---
author: admin
date: '2007-12-15 17:54:41'
layout: post
slug: protecting-your-ruby-source-code-for-end-user-applications
status: publish
title: Protecting Your Ruby Source Code for End User Applications
wordpress_id: '132'
categories:
- C/C++
- Programming
- Ruby
---

If you want to distribute your Ruby applications while still protecting
your intellectual property you could use an obfuscation tools such as
[ZenObfuscate](http://blog.zenspider.com/archives/2006/07/zenobfuscate_no.html)
or try to write your own. But in this article, I'm going to show a
different approach that's been used by several different companies
producing commercial products written in Ruby. The method is not
specific to Ruby and should work for any interpreted language in which
you need to distribute your source code with the application.

The secret is to encrypt your Ruby source, store it in a database and
then modify the Ruby interpreter to look for your code in the database
and decrypt it on the fly. I should note that there is no way to
completely protect a product which is distributed to your
customers--with enough diligence any security measures can be broken.

These instructions are for Unix operating systems (include MacOS X).
Unfortunately (or fortunately, for me), I don't own a Windows machine.

If you don't already have Berkeley DB (BDB) installed on your system you
can download it
[here](http://www.oracle.com/technology/software/products/berkeley-db/index.html).
You will need to follow the instructions which come with BDB which
explain how to build and install it. Originally, I was going to use
[OpenSSL](http://openssl.org/) to encrypt our Ruby source code before
inserting it into the database and decrypt it after retrieving it from
the database. Thankfully, the latest version of BDB includes
[AES](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard) support
which allows you to maintain an encrypted database very easily.

You will also need to obtain a fresh copy of the [Ruby source
code](http://www.ruby-lang.org/en) so that we can build our own private
version which knows how to pull classes out of our BDB instance. So
let's start by creating a directory for us to work in:

    mkdir -p ~/RubyProject/deploy

You should unpack the Ruby source in the *\~/RubyProject* directory
(this should create directory which looks like
*\~/RubyProject/ruby-1.8.6-p111*). Go into that directory and run the
configure script as follows:

    ./configure --prefix=~/RubyProject/deploy --with-static-linked-ext

This will enable us to build a stand alone Ruby interpreter which has
everything it needs statically linked in.

To find out where we need to hook in our handler which loads missing
classes from the database, you can *grep* through the source code
looking for const\_missing like this:

    grep const_missing *.c

This turned up two files *object.c* and *variable.c*. Looking at the
output, I could see that the ***const\_missing*** function is actually
defined in *variable.c*. Jumping in, I searched for the code executed
when a constant cannot be found. This led me to the
***rb\_const\_get\_0*** function which walks up the class hierarchy
looking for the specified constant. If it cannot be found, it returns
the result of the ***const\_missing*** function. So right before that
final return, I added the following hook:

        /* At this point we haven't found the class so we must look
           inside of the BerkeleyDB for it, see dbloader.c */
        value = load_from_db(id);
        if (value != Qundef) return value;

Now I just had to implement the load\_from\_db function which should
look inside of the encrypted BDB instance for the file. Looking at how
the ***rb\_const\_get\_0*** function works, I knew my new method had to
return a Ruby *VALUE*:

    VALUE
    load_from_db(id)
         ID id;
    {
        DBT k;
        DBT d;

        memset(&k, 0, sizeof(DBT));
        memset(&d, 0, sizeof(DBT));

        verify_database_state();

        k.data = rb_id2name(id);
        k.size = strlen(k.data);

        d.flags = DB_DBT_MALLOC;

        if (bdb->get(bdb, NULL, &k, &d, 0) == 0) {
          rb_eval_string((const char *)d.data);
          free(d.data);
          return rb_eval_string(rb_id2name(id));
        }
        return Qundef;
    }

You'll note that if we find the class in the database, we first evaluate
it using ***rb\_eval\_string***. Since this returns *nil*, we need
evaluate the class name so that we can pass back a Ruby *VALUE*. If the
class doesn't exist in the database, we return *Qundef* and
***const\_missing*** gets called as usual.

The ***verify\_database\_state*** function ensures that the password for
the BDB instance was passed and the database opened so that the
***get*** call can access it. It is implemented like so:

    /* a simple way to obfuscate the password in memory */
    #define A(c)             (c) - 0x1d
    #define ENCRYPT_PWD(str) do { char * p = str; while (*p) *p++ -= 0x1d; } while (0)
    #define DECRYPT_PWD(str) do { char * p = str; while (*p) *p++ += 0x1d; } while (0)

    static void
    verify_database_state()
    {
      /* don't forget to NULL terminate this array! */
      static char info[] =
        { A('1'), A('2'), A('3'), A('4'), A('5'),
           A('6'), A('7'), A('8'), A('9'), A('0'),
           0 };

      const char * database_file = "data.db";

      if (bdb == NULL) {
        db_env_create(&bdbenv, 0);
        db_create(&bdb, bdbenv, 0);

        DECRYPT_PWD(info);
        bdbenv->set_encrypt(bdbenv, info, DB_ENCRYPT_AES);
        ENCRYPT_PWD(info);
        bdbenv->open(bdbenv, ".", DB_INIT_MPOOL | DB_CREATE | DB_PRIVATE, 0600);
        bdb->set_flags(bdb, DB_ENCRYPT);
        bdb->open(bdb, NULL, database_file, NULL, DB_BTREE, 0, 0644);
      }
    }

You'll notice that the password is hard coded into the binary along with
the location of the BDB instance. If you are going use this code, you'll
want to change the default password (which needs to match the password
you used when storing your Ruby source in the database) and perhaps the
location of the database. To deter those looking to decrypt our Ruby
source, I've written C macros which performs a transformation on the
password. It is fairly simple to circumvent, so you should research
other methods of securely storing passwords within applications.

Finally, you'll need to remember to close the BDB instance before the
Ruby interpreter exits. To do this we simply open up *main.c* and add
the following line immediately following the call to ***ruby\_run***:

    close_database();

The implementation of ***close\_database*** is trivial, so you can just
look in the patch I've provided for it.

The patch to the Ruby source code is included in [this zipped
attachment](http://seanmountcastle.com/wp-content/uploads/2007/12/ruby-load-db.zip)
along with another utility I wrote to load all of your Ruby source into
the encrypted BDB instance (along with its Makefile). Here is a
transcript which shows how to use the tools and your new Ruby
interpreter:

    ~RubyProject/tools> ./rb_store data.db *.rb
    Enter database password:
    Stored Example (131) bytes

    ~RubyProject/tools> ./rb_load data.db
    Enter database password:
    Hit CTRL+C to quit.
    Enter a class name: Example
    Found: 

    class Example
      def initialize
        puts "Hello from the Example class"
      end

      def aMethod
        puts "Called aMethod"
      end
    end

    Enter a class name: Foo
    No such class
    Enter a class name: ^C

    ~RubyProject/ruby-1.8.6-p111> ./ruby -e "e = Example.new"
    Hello from the Example class

    ~RubyProject/ruby-1.8.6-p111> ./ruby -e "f = Foo.new"
    -e:1: uninitialized constant Foo (NameError)

This implementation doesn't deal with multiple classes of the same name
residing in different directories. Also, the way in which the *rb\_load*
tool determines the name of the class is rather naive and can screw it
up. I've wanted to write this for over a year now after hearing [Rich
Kilmer](http://richkilmer.blogs.com/) talk about the way in which
[InfoEther](http://infoether.com/) distributes its Ruby applications. So
this is more of a proof-of-concept for myself than anything else.
Hopefully you learned from this tutorial and can put it to good use.
