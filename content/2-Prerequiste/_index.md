---
title : "Preparation "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

{{% notice info %}}
We need to learn some basics of Docker, Nginx to perform this lab.
{{% /notice %}}

#### Nginx
nginx (engine x) is an HTTP server, reverse proxy, content cache, load balancer, TCP/UDP proxy server. In this workshop, we use nginx as a reverse proxy.

To learn what is Nginx, how to Nginx works, Nginx basic concepts and how to configure a simple Nginx server:
  - [Nginx for beginner](https://nginx.org/en/docs/beginners_guide.html)
  - [Nginx with Docker](https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/)

#### Docker
Docker is an open platform for developing, shipping, and running applications.

Learn basic concepts of Docker:
  - [Docker for beginner](https://docs.docker.com/get-started/)
  - [Containerize Nodejs App](https://docs.docker.com/guides/language/nodejs/containerize/)

### Content
  - [Preparing Nginx Config](2.1-createnginx/)
  - [Preparing Docker Resources](2.2-createdocker/)
  - [Create IAM Role](2.3-createiamrole/)
  - [Preparing VPC and EC2](2.4-createec2/)
  - [Create S3 Bucket](2.5-creates3bucket/)
  - [Preparing spec files](2.6-createspecfiles/)
  - [Create CodeBuild service](2.7-createcodebuild/)
  - [Create CodeDeploy service](2.8-createcodedeploy/)
  - [Create CodePipeline service](2.9-createcodepipeline/)