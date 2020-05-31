---
layout: post
title: "Data Import"
date: 2020-05-09 13:00:00 -0400
categories: build
---

Now that you've created your Atlas database, import the sample dataset:

1. Get the mock data and import
   1. git clone URL<BR>
   For now, extract <A HREF="/assets/files/CodeForGoodDataSet.tar.gz">CodeForGoodDataSet.tar.gz</A>.
   1. Note the path to the directory CodeForGoodbackup, which contains a directory called "wildaid".
1. Get connection string
   1. Click CONNECT in the cluster itself (or as previously on the "all clusters" page for the project):
<img src="/assets/images/CONNECT.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click on Connect using MongoDB Shell, then "I have the mongo shell installed "
<img src="/assets/images/Click_Already_Have.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Copy the connection string
<img src="/assets/images/Copy_Connection_String.png" style="border:1px solid black" width="100%"><BR><BR>

1. Import with mongorestore using the path and connection string, dropping any existing tables. Make sure to add your username in place of USER in the connection string, followed by @ and then the CLUSTER:
   1. `mongorestore --drop --uri "mongodb+srv://USER@CLUSTER.mongodb.net/wildaid" /PATH/TO/CodeForGoodbackup`
1. Check with Data Explorer
   1. Go to <code>Collections</code> in the Atlas UI:
<img src="/assets/images/Atlas_Data_Explorer.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click on the BoardingReports collection and verify there are records: 
<img src="/assets/images/Verify_data.png" style="border:1px solid black" width="100%"><BR><BR>

Great work, now you're ready to hook up Realm...
