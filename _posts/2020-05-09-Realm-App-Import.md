---
layout: post
title: "Realm App Install and Import"
date: 2020-05-09 14:00:00 -0400
categories: build
---

Recap:<BR>
Project Name: WildAid<BR>
Cluster name: OceanWatchData<BR><BR>


NOTE TO COPY PUBLIC KEY
TAKE OUT HOSTING FROM THE stitch.json

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
   1. Install stitch-cli - see instructions for manual install or install via `npm` at <A HREF="https://docs.mongodb.com/stitch/deploy/stitch-cli-reference/" _target="blank">https://docs.mongodb.com/stitch/deploy/stitch-cli-reference</A><BR><BR>
   1. Connect your commandline with Realm using `stitch-cli login`:<BR>
      `stitch-cli login --api-key="PUBLIC_API_KEY" --private-api-key="PRIVATE_API_KEY" --base-url=https://realm-dev.mongodb.com`<BR><BR>
      It works when the output is <BR>`you have successfully logged in as PUBLIC_API_KEY`<BR><BR>
   1. If you are connecting your instance with an external AWS environment, add your AWS secret key as the `--value` in this command. If you are not connecting your instance with AWS, you still need to run this command but `--value` can be set to any string. 
   You will need your Realm application ID (example: wildaidapp-xxxxx)<BR>
      `stitch-cli secrets add --app-id=wildaidapp-xxxxx --name=AWS-secret-key --value=my-aws-secret-api-key --base-url=https://realm-dev.mongodb.com`<BR><BR>
      It works when the output is <BR>`New secret created: AWS-secret-key`<BR><BR>
1. Import the Realm code
      1. Get the Realm code to import - in your terminal, `git clone Realm_repo` <BR>
      For now, download and extract <A HREF="/assets/files/WildAidRealm.tar.gz">WildAidRealm.tar.gz</A>.<BR><BR>
      1. `cd WildAidDemo`
      1. Edit `stitch.json` change "name" to your Realm application name (example is wildaidapp-xxxxx) 
      1. Edit `services/RealmSync/config.json services/mongodb-atlas/config.json`<BR> and change "ClusterName" to your cluster's name (example is WildAid)<BR>
      1. Edit the following files if using AWS and fill in all the variables. If not, you can leave the files as-is.<BR>
       `values/awsRegion.json values/destinationEmailAddress.json values/sourceEmailAddress.json`<BR><BR>
      1. Set accessKeyID if using AWS (leave unedited if not using) in the file: <BR>
        `WildAidDemo/services/AWS/config.json`<BR><BR>
      1. Do the import, confirm with 'y' when prompted to confirm changes. You will need your Realm application ID:
        `stitch-cli import --app-id=wildaidapp-xxxxx --strategy=replace --include-dependencies --base-url=https://realm-dev.mongodb.com`<BR><BR>
      1. Verify the code got imported by going to the Realm App and clicking "Functions" on the left-hand side. You should see several functions, as below:
        <img src="/assets/images/Functions.png" style="border:1px solid black" width="100%"><BR><BR>


You have successfully set up a Realm serverless application! You may get emails like "A Database Trigger has been Suspended", do not worry about that for now. It's time to connect Realm to your data with a user!
