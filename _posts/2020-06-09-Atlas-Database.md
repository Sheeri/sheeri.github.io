---
layout: post
title: "0. Atlas Database"
date: 2020-05-09 00:00:00 -0400
categories: build
---

The first step is to set up the Atlas database - this is the foundation data layer that serve data to the mobile apps, charts, and web apps.

1. Login to <A HREF="https://cloud.mongodb.com" target="_blank">cloud.mongodb.com</A> - create a free login if needed.<BR><BR>
1. If needed, create an organization (example: Code For Good). <BR><BR>
1. Create a project (example: WildAid). Fill in the "Project Name" on the template with this value.<BR><BR>
1. Click Access Manager, then Organization Access:
<img src="/assets/images/Atlas_Project_Access.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click EDIT PERMISSIONS (get screenshot)
   1. Give yourself all permissions, not just Owner, and click the green checkmark.<BR><BR>
<img src="/assets/images/Atlas_Access_Permissions.png" style="border:1px solid black" width="100%"><BR><BR>

1. Create a 4.4 Cluster:
   1. Click "projects" (they're on the access permissions page)
   1. Click "WildAid"
   1. Click Create a Cluster
   1. Choose a path - choose the FREE Shared Clusters on the left: 
<img src="/assets/images/Atlas_Choose_Path.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Choose Cloud Provider and Region
<img src="/assets/images/Atlas_Cloud_Region.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Choose Cluster Tier - choose M0, the free tier
<img src="/assets/images/Atlas_Tier.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Select a Version - 4.4
<img src="/assets/images/Atlas_Version.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Cluster Name - take note of this in template under "Atlas Cluster Name".
<img src="/assets/images/Atlas_Cluster_Name.png" style="border:1px solid black" width="100%"><BR><BR>
   1. Click "Create Cluster" - this will take a few minutes <BR><BR>

Congratulations, you have set up an Atlas database!
