---
layout: post
title: "Atlas Database"
date: 2020-05-29
---

Now that you've created your Atlas database, create the Realm App and import all the code associated with it (e.g. functions, triggers).


Realm:
[ ] 1. Create Realm app, called WildAidApp, link database
[ ] 1. Access Manager, Project, create API key
[ ] 1. Give permissions
[ ] 1. Store private key safely
[ ] 1. Blur out private key in video
[ ] 1. Add API whitelist (blur in video)
[ ] 1. Install stitch-cli (web or commandline)
[ ] 1. stitch-cli login 
[ ] 1. stitch-cli login --api-key=my-api-key --private-api-key="my-private-api-key" --base-url=https://realm-dev.mongodb.com
[ ] 1. stitch-cli add AWS secret, dummy string if not needed
[ ] 1. stitch-cli secrets add --app-id=wildaidapp-jfupd --name=AWS-secret-key --value=my-aws-secret-api-key --base-url=https://realm-dev.mongodb.com
[ ] 1. Git clone the Realm repo (if we didn’t already do it in the Data step)
[ ] 1. Edit files: to add cluster name: stitch.json services/RealmSync/config.json services/mongodb-atlas/config.json
[ ] 1. Edit files: for S3 services (leave unedited if not using): values/awsRegion.json values/destinationEmailAddress.json values/sourceEmailAddress.json
[ ] 1. Set accessKeyID if using S3 (leave unedited if not using: WildAidDemo/services/AWS/config.json
[ ] 1. Import Realm functions - stitch-import
[ ] 1. Verify by looking at functions/triggers in Realm
[ ] 1. Add a Realm user: Create a global administrative user in Realm and note the Realm ID.

