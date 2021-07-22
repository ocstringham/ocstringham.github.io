---
layout: post
title: "Working with PostgreSQL and PostGIS [SQL Database Tutorial]"
author: Oliver C. Stringham
date: 2021-07-19
tags: sql postgres postgresql postgis gis
categories: sql-database
---

## Introduction

I used MySQL for the past 3 years now as my SQL database manager of choice. However, I have two reasons for wanting to learn a new SQL RDMS (relational database management system). First, I will be looking for work soon as a data scientist, and would like to be proficient in more than one SQL RDMS. Also, since diving into GIS and the spatial world, I would like to learn PostgreSQL since it supports  storing spatial files in an SQL table using the extension PostGIS. In particular, this aspect of PostgreSQL offers much more than most (free) database systems. I think the ability to query using SQL based on spatial operation can be very powerful, especially considering spatial files usually take up a lot space - thus querying to only retrieve needed records is desirable. Also, if storing and retrieving spatial data online (e.g., for web applications), then using SQL is must to save money on data retrieval and processing time. Here is one example of a spatial query: to select all the polygons within a certain distance of a location, one can use the following SQL statement:

~~~~sql
SELECT population_total
FROM census
WHERE ST_DWithin(
        geom,
        ST_GeomFromText('POINT(583571 4506714)',26918),
        10000
      );
~~~~

which will return all the shapes (e.g., points/lines/polygons) within 10 km (10,000 m) from the Statue of Liberty (coordinate X, Y). I'll get into the details either later in the post or in future posts. But, hopefully this gives a glimpse of the power of a spatial query. This is what I will work up to in this tutorial - from nothing to being able to run spatial queries.

<!--more-->

## Getting started with PostgreSQL and PostGIS

### Installation

First step is to install PostgreSQL (or postgres for short) on your either your local computer or a remote server. For personal use and learning, I recommend installing to your local computer. Visit postgres' [website](https://www.postgresql.org/download/) and select the installation file that matches your operating system. Run the installer, following all the defaults. You need to provide a password - don't forget it! Once, installation of postgres is complete, it should auto-launch a window to select additional extensions to install. Select then PostGIS extension from the list and follow the prompts to install. That's it - postgres and PostGIS are now installed on your computer. Next thing is to set it up to store data.

### Storing Data in Tables

Data is stored in tables. Postgres and other RDMS have a tiered structure of different entities. For postgres, it's desirable to have one 'database' that contains different 'schema', each 'schema' can have its own tables. One can use schemas to keep tables organized. For instance, one schema might contain census data tables and another schema might contain weather data tables. Think of a schema as a collection of tables.

#### Creating Schemas

Before we can store our data in a table(s), we need to create a schema. I'm interested in working with US census data, which is publicly available, so let's start with that.

##### Using pgAdmin 4

 Postgres comes with a GUI interface called pgAdmin 4, which allows one to interact with postgres in a point and click manner, which I prefer. On startup of pgAdmin 4 it will ask for the password you provided upon installing postgres. 

![pgAdmin 4 on startup](/assets/images/blog/postgres-intro/2021-07-19 21_41_43-pgAdmin 4.png "pgAdmin 4 on startup")

Postgres comes with a 'database' built by default called postres (highlighted in image). Now is about time where the terminology becomes confusing, but a database is higher than a schema, so a database can be a collection of schema. I drew a diagram for this: 

![postgres structure](/assets/images/blog/postgres-intro/db-schema-table.png "postgres structure")

For most data science work, all you need to worry about is schema tables. If all your data tables are in the same 'database' then they can be queried in the same SQL statement (even if in different schema). So, let's just stick with the default 'database' called postgres. 

Now, let's add a new schema. Right click the postgres database > Create > Schema ... . Type in the desired name, in my case it will be called __us_census__, and click Save. 

![postgres create new schema](/assets/images/blog/postgres-intro/pgAdmin-create-schema.png "postgres create new schema")

Now, there exists a new schema called __us_census__, where we can create data tables to store our data!

![postgres view new schema](/assets/images/blog/postgres-intro/pgAdmin-new-schema.png "postgres view new schema")

---
**NOTE**

Alternatively to pgAdmin 4, one can use psql, a command-line like interface that comes installed alongside postgres. For this tutorial, I'll stick with pgAdmin 4, but I wanted to introduce it in case others find that more familiar. 

---


