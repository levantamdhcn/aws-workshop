---
title : "Create EC2 Instance"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.4.4 </b> "
---

1. Go to [EC2 service management console](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click **Launch instances**.
  
![EC2](/images/2.prerequisite/022-createec2.png)

2. On the **Step 1: Choose an Amazon Machine Image (AMI)** section.
  + Click **Quick Start** to select **Ubuntu**.
  + At **Amazon Machine Image**, select **Ubuntu Server 24.04 LTS (free tier eligible)**.
  
![EC2](/images/2.prerequisite/028-createec2.png)

3. Scroll down to **Instance Type** section.
 + Click on Instance type **t2.micro**.
 + Click **Create new key pair** at Key pair (login) section.

![EC2](/images/2.prerequisite/030-createec2.png)

4. At the **Create key pair** popup.  
 + In the **Key pair name** field, enter **chat-app**.
 + In the **Key pair type** field, select **RSA**.
 + In the **Private key file format** field, select **.pem**.
 + Click **Create key pair**.
 
![EC2](/images/2.prerequisite/029-createec2.png)

5. Scroll down to **Network settings** section, click **Edit**
  + In the **Network** section, select **ASG**.
  + In the **Subnet** section, select **Public Subnet**.
  + In the **Auto-assign Public IP** section, select **Use subnet setting (Enable)**
  + In the **Common security groups**, select **Public SG**

![EC2](/images/2.prerequisite/031-createec2.png)

6. Scroll down to **Network settings** section, click **Edit**
  + In the **Network** section, select **ASG**.
  + In the **Subnet** section, select **Public Subnet**.
  + In the **Auto-assign Public IP** section, select **Use subnet setting (Enable)**
  + In the **Common security groups**, select **Public SG**

![EC2](/images/2.prerequisite/031-createec2.png)

7. Scroll down to **Advance details** section and expand that.
  + At IAM Instance profile, choose **EC2S3ReadPermission** Policy that we create from [Create IAM Role](/2-Prerequiste/2.3-createiamrole/).
![EC2](/images/2.prerequisite/032-createec2.png)

8. Keep default settings for other section, scroll down to bottom.
  + Click **Launch**.

9. Click **View Instances** to return to the list of EC2 instances.

Next, we will do the same to create an EC2 Instance Windows running in the Private subnet.