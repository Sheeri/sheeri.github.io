---
layout: post
title: "Data Import"
date: 2020-05-09 13:00:00 -0400
categories: build
---

Now that you've created your Atlas database, import the sample dataset:

1. Get the mock data and import
   1. git clone URL<BR>
   For now, download and extract <A HREF="/assets/files/CodeForGoodDataSet.tar.gz">CodeForGoodDataSet.tar.gz</A>.
   1. Note the path to the directory CodeForGoodbackup, which contains a directory called "wildaid".  <BR><BR>
1. Get connection string
   1. Click CONNECT in the cluster itself (or as previously on the "all clusters" page for the project):
<img src="/assets/images/CONNECT.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click on Connect using MongoDB Shell, then "I have the mongo shell installed "
<img src="/assets/images/Click_Already_Have.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Copy the connection string
<img src="/assets/images/Copy_Connection_String.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click "Close"

1. In a terminal window, use the mongorestore utility with the `mongodb+srv` link you just copied in the connection string. Make sure to add the username you just created in place of USER in the connection string, followed by @ and then the rest of the mongodb+srv link - this example's link is "ofish-xxxxx.mongodb.net/test":
   1. `mongorestore --drop --uri "mongodb+srv://USER@ofish-xxxxx.mongodb.net/test" /PATH/TO/CodeForGoodbackup`<BR><BR>
1. Check with Data Explorer
   1. Go to <code>Collections</code> in the Atlas UI:
<img src="/assets/images/Atlas_Data_Explorer.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click on the BoardingReports collection and verify there are records: 
<img src="/assets/images/Verify_data.png" style="border:1px solid black" width="100%"><BR><BR>

Great work, now you're ready to hook up Realm...
