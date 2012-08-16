---
author: admin
date: '2006-01-11 09:08:00'
layout: post
slug: getting-the-latlong-for-a-zipcode
status: publish
title: Getting the Lat/Long for a Zipcode
wordpress_id: '30'
categories:
- GIS
- Programming
- Ruby
---

I've uploaded a short Ruby script which uses Google maps to obtain the
lat/long given a zipcode. I needed this since the
[Cartographer](http://wiki.rubyonrails.com/rails/pages/Plugins) RoR
plug-in takes coordinates in the form of lat/long and my customers will
only provide me with their zipcodes or complete addresses. Obviously in
my Rails web-app I'm storing the lat/long in the DB so I don't
repeatedly query Google Maps. The class simply returns a hash and is
trivial to use:

~~~~ {lang="ruby"}
coords = GMap.to_latlng("90210")
lat = coords[:lat]
lng = coords[:lng]
~~~~

Download
[zipcode.zip](http://seanmountcastle.com/wp-content/uploads/2007/04/zipcode.zip)
**Updated 2007**: This has basically been supplanted by the excellent
[GeoKit for Rails](http://geokit.rubyforge.org/).
