---
layout: post
title: "Build Web App"
date: 2020-05-09 17:00:00 -0400
categories: build
---

Recap:<BR>
Project Name: WildAid<BR>
Cluster name: OceanWatchData<BR><BR>


Build the web app:
1. Get the code<BR>
   git clone https://github.com/mongodb-appeng/ocean-watch-web.git
<BR>for now, <A HREF="/assets/files/ocean-watch-web.tar.gz">click here</A>
1. cd `ocean-watch-web`
1. edit src/.env/config.js 
1. npm run build
1. In the Stitch UI in your browser, click on "Hosting" on the left-hand side under "MANAGE"
    SHOW SCREEN SHOT
1. Enable hosting
1. Drag and drop the contents of the build folder onto the Stitch window. There should be about 10 files and folders in the directory when you are done. It is OK to overwrite existing files.
1. Run Actions/Flush CDN Cache
1. Make note of the URL on the Hosting page, this is your website!

Proceed to the next step when the blue bar no longer appear saying "Your site is in the process of being created, which may take up to 15 minutes."


const config = {
    appName: 'WildAidApp',
    stitchAppId: 'wildaidapp-jfupd',
    stitchDatabase: 'wildaid',
    stitchBaseUrl: 'https://realm-dev.mongodb.com'
}
