---
layout: post
title: "Working with PostgreSQL and PostGIS [SQL Database Tutorial]"
author: Oliver C. Stringham
date: 2021-09-19
tags: sql postgres postgresql postgis gis
categories: sql-database
---

I used MySQL for the past 3 years now as my SQL database of choice. I use mySQL frequently and have since understand it and enjoy it. However, I have two reasons for wanting to learn a new SQL RDMS (relational database management system). First, I will be looking for work soon as a data scientist, and would like to be proficient in more than one SQL RDMS. Also, since diving into GIS and the spatial world, I would like to learn PostgreSQL since it supports  storing spatial files in an SQL table using the extension PostGIS. In particular, this aspect of PostgreSQL offers much more than most (free) database systems. I think the ability to query using SQL based on spatial operation can be very powerful, especially considering spatial files usually take up a lot space - thus querying to only retrieve needed records is desirable. For example, to select all the polygons within a certain distance of a point, one can use the following SQL:

~~~~sql
select * from census_blocks
    ST_within 
~~~~

which will return all the shapes (e.g., points/lines/polygons) within 1 km (1,000 m) from the Statue of Liberty point ()


