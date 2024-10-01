---
title : "Preparing Docker Resources"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.2 </b> "
---

In this step, we will need to create 2 Dockerfile to build our images. Then create docker-compose.yml file to manage all our images.

The folder structure overview after you complete this step will be as follows:

![Docker](/images/2.prerequisite/002-docker.png)

### Content
  - [Create Server's Dockerfile](2.1.1-createserverimage/)
  - [Create Public Subnet](2.1.2-createpublicsubnet/)
  - [Create Private Subnet](2.1.3-createprivatesubnet/)
  - [Create security group](2.1.4-createsecgroup/)
  - [Create public Linux server](2.1.5-createec2linux/)
  - [Create private Windows server](2.1.6-createec2windows/)