---
layout: post
title: "Connect Realm With Data"
date: 2020-05-09 15:00:00 -0400
categories: build
---

Recap:<BR>
Project Name: WildAid<BR>
Cluster name: OceanWatchData<BR><BR>

You have imported your Realm app!  Now, let's create a Realm user...

1. Add a Realm user - this will be the global administrative user who logs into your application.
      1. In the Realm UI, click on Users under Data Access & Security, and then click on the green "Add New User" button.
        <img src="/assets/images/Add_Realm_User.png" style="border:1px solid black" width="100%"><BR><BR>
      1. Add an email address as the username and a password. I used my own email as the global administrative login, you can use your email or whatever login you want for the global administrative user. This email is only used if you forget your password:
        <img src="/assets/images/Realm_User_Details.png" style="border:1px solid black" width="100%"><BR><BR>
      1. Note the Realm ID
        <img src="/assets/images/Copy_Realm_User_ID.png" style="border:1px solid black" width="100%"><BR><BR>
1. Add a new document to the wildaid.User collection (using Compass, mongo shell or code studio integration). Set the email and RealmUserID as per the previous step, and set the agency and first and last names as appropriate.<BR>
`use wildaid;`<BR>
`db.User.insertOne({`<BR>
`"email":"sheeri.cabral@mongodb.com",`<BR>
`"RealmUserID": {"$oid":"xxxxxxxxxxxxxxxxxxxxx"},`<BR>
`"agency": {"name":"MongoDB", "admin":false},`<BR>
`"global": {"admin":true},`<BR>
`"name": {"first":"Sheeri", "last":"Cabral"}`<BR>
`})`

Fantastic!
