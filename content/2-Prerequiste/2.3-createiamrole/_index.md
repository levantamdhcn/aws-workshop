---
title : "Create IAM Role"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

### Create IAM Role For EC2

In this step, we will proceed to create IAM Role. In this IAM Role, the policy **AmazonS3ReadOnlyAccess** will be assigned, this is the policy that allows the EC2 server to read artifact from S3 Bucket to Deploy.

1. Go to [IAM service administration interface](https://console.aws.amazon.com/iamv2/)
2. In the left navigation bar, click **Roles**.

![createpolicy](/images/2.prerequisite/038-iamrole.png)

3. Click **Create role**.

![createpolicy](/images/2.prerequisite/039-iamrole.png)

4. Click **AWS service** and click **EC2**.
  + Click **Next: Permissions**.

![createpolicy](/images/2.prerequisite/041-iamrole.png)

5. In the Search box, enter **S3** and press Enter to search for this policy.
  + Click the policy **AmazonS3ReadOnlyAccess**.
  + Click **Next: Tags.**

![createpolicy](/images/2.prerequisite/040-iamrole.png)

6. Click **Next: Review**.
7. Name the Role **EC2S3ReadPermission** in Role Name
  + Click **Create Role** \.

![namerole](/images/2.prerequisite/042-iamrole.png)

### Create IAM Role For AWS CodeDeploy
1. Back to **Roles** section.
2. Click **Create role**.
![createpolicy](/images/2.prerequisite/039-iamrole.png)
3. Click **AWS service** and click **CodeDeploy**.
  + Click **Next: Permissions**.
![createpolicy](/images/2.prerequisite/043-iamrole.png)
4. Name the Role **ChatAppCodeDeploy** in Role Name
  + Click **Create Role** \.
![createpolicy](/images/2.prerequisite/044-iamrole.png)

Next, we will create **VPC** and **EC2** to hold our application.