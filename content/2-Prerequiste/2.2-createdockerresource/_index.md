---
title : "Preparing Docker Resources"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---
In this step, we will need to create 2 Dockerfile to build our images. Then create docker-compose.yml file to manage all our images.

{{% notice info %}}
A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image
Some reference we can learn about this file: [Documents](https://docs.docker.com/reference/dockerfile/#:~:text=A%20Dockerfile%20is%20a%20text,line%20to%20assemble%20an%20image).
{{% /notice %}}

The folder structure overview after you complete this step will be as follows:

![Docker](/images/2.prerequisite/002-docker.png)

### Content
  - [Create Server's Dockerfile](2.1.1-createserverimage/)
  - [Create Nginx's Dockerfile](2.1.2-createnginximage)