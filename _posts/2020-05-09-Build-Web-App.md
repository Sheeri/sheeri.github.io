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
1. Go to the Hosting tab for the Stitch app
1. https://realm-dev.mongodb.com/groups/5e5f73d4b19df941b9221044/apps/5e60d0f82b41db10af8dca5c/hosting/assets
1. Enable hosting
1. Drag and drop the contents of the build folder onto the Stitch window and accept that files will be overwritten
1. Run Actions/Flush CDN Cache
1. Go to web page when DNS has propagated

