---
layout: post
title: "Realm App Install and Import"
date: 2020-05-09 14:00:00 -0400
categories: build
---

Recap:<BR>
Project Name: WildAid<BR>
Cluster name: OceanWatchData<BR><BR>

Now that you've populated your Atlas database, this page will walk you through creating the Realm App and import all the code associated with it (e.g. functions, triggers):

1. Create the WildAid Realm application:
   1. In the Atlas UI, click the "Realm" icon:
<img src="/assets/images/Click_Realm.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click "Skip questions and start new app"
<img src="/assets/images/Skip.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Configure Realm: Give the Realm App a name (our example uses WildAidApp) and link your cluster, then click "Create Realm Application". (Sheeri - fix this picture!)
<img src="/assets/images/Realm_Config.png" style="border:1px solid black" width="100%"><BR><BR>

1. In order to import the Realm App, we need to authenticate with an API key.
   1. Click Access Manager, then Project Access:
<img src="/assets/images/Atlas_Project_Access.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click "API Keys"
<img src="/assets/images/API_Key.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click "Create API Key" on the right-hand side of your screen
<img src="/assets/images/Click_Create_API_Key.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Add in a description (we used "To Import Realm (one-time)") and allow all but the read-only permissions. Click "Next".
<img src="/assets/images/API_Key_Options.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Copy your private key and save it, you'll need it shortly and click "Add Whitelist Entry".
<img src="/assets/images/Copy_Private_Key.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Add your current IP to the whitelist and click "Save".
<img src="/assets/images/Add_IP_API_Key_Whitelist.png" style="border:1px solid black" width="100%"><BR><BR>
1. stitch-cli setup
   1. Install stitch-cli- see instructions for manual install or install via `npm` at https://docs.mongodb.com/stitch/deploy/stitch-cli-reference/<BR><BR>
   1. Connect your commandline with Realm using `stitch-cli login`:<BR>
      `stitch-cli login --api-key="PUBLIC_API_KEY" --private-api-key="PRIVATE_API_KEY" --base-url=https://realm-dev.mongodb.com`<BR><BR>
      It works when the output is <BR>`you have successfully logged in as PUBLIC_API_KEY`<BR><BR>
   1. Add the AWS secret - if not using AWS, use a dummy string; otherwise the Realm import will not work. You will need your application ID (example: wildaidapp-xxxxx)
      `stitch-cli secrets add --app-id=wildaidapp-xxxxx --name=AWS-secret-key --value=my-aws-secret-api-key --base-url=https://realm-dev.mongodb.com`<BR><BR>
1. Import the Realm code
      1. Get the Realm code to import - `git clone Realm_repo` <BR>
      For now, download and extract <A HREF="/assets/files/WildAidRealm.tar.gz">WildAidRealm.tar.gz</A>.<BR><BR>
      1. Edit files: change "name" to your application name (wildaidapp-xxxxx) and "ClusterName" to your cluster's name (example is WildAid)<BR>
       `stitch.json services/RealmSync/config.json services/mongodb-atlas/config.json`<BR><BR>
      1. Edit files: change AWS service info (leave unedited if not using): <BR>
       `values/awsRegion.json values/destinationEmailAddress.json values/sourceEmailAddress.json`<BR><BR>
      1. Set accessKeyID if using AWS (leave unedited if not using): <BR>
        `WildAidDemo/services/AWS/config.json`<BR><BR>
      1. Do the import, confirm with 'y' when prompted:
        `stitch-cli import --app-id=wildaidapp-xxxxx --strategy=replace --include-dependencies --base-url=https://realm-dev.mongodb.com`<BR><BR>
      1. Verify the code got imported by going to the Realm App and clicking "Functions" on the left-hand side. You should see several functions, as below:
        <img src="/assets/images/Functions.png" style="border:1px solid black" width="100%"><BR><BR>

Now that you have set up Realm, it's time to connect Realm to your data with a user!
