---
layout: post
title: "Data Import"
date: 2020-05-09 13:00:00 -0400
categories: build
---

Now that you've created your Atlas database, import the sample database:

1. Get the mock data and extract a mongodump
   git clone URL
1. Get connection string
   1. Click CONNECT on the "all clusters" page or in the cluster itself
   1. Click on Connect using MongoDB Compass
   1. Copy the connection string
1. Import with mongorestore
   1. `mongorestore --uri "mongodb+srv://user@oceanwatchdatat.vsyzz.mongodb-dev.net/wildaid" /Users/sheeri/wildaid_demo/build/CodeForGoodbackup`
1. Check with Data Explorer
 
