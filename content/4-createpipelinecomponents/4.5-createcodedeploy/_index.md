---
title : "Create AWS CodeDeploy"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 4.5 </b> "
---

#### Prepare CodeDeploy Application

1. Access [CodeDeploy - AWS Developer Tools management console](https://eu-west-2.console.aws.amazon.com/codesuite/codedeploy/start)
  + Click **Create application**.
  
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/017-codedeploy.png)

2. At **Application configuration**.
  + At **Application name**, enter **ChatAppCodeDeploy**.
  + At **Compute platform**, select **EC2/On-premises**.
  + Click **Create application**.
  
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/018-codedeploy.png)

3. Return to **Application Detail** we have just created.
  + Click **Create deployment group**
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/019-codedeploy.png)

4. At **Deployment group name**
  + Enter **ChatAppDeploymentGroup**
  + At **Service Role**, select **ChatAppCodeDeploy** we created from [Create IAM Role](/2-Prerequiste/2.3-createiamrole/)
  + At **Deployment Type**, we use **In-place** for now (will have downtime).
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/020-codedeploy.png)

5. Scroll down to **Environment configuration**.
  + Check on **Amazon EC2 instances**.
  + Enter **Key: Name - Value: ChatApp** for better management.

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/021-codedeploy.png)

6. Scroll down to **Load balancer**.
  + Uncheck on **Enable load balancing**, we don't need it for now.
  + Click **Create deployment group**.

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/022-codedeploy.png)


#### Create Deployment
1. Go to **Detail page** of Application we have just created
  + Click **Create deployment**

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/023-codedeploy.png)

2. At **Deployment setting**:
  + At **Revision type**, select **My application is stored in Amazon S3**.
  + At **Revision location**, copy URI of artifact in S3 Bucket and paste here.
  + At **Revision file type**, select **.zip**

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/024-codedeploy.png)

3. Scroll down, click **Create deployment**

4. Waiting for deployment process success.
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/025-codedeploy.png)