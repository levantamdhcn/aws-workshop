---
title : "Create Public Subnet"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.4.2 </b> "
---

#### Create Public Subnet

1. Click **Subnets**.
  + Click **Create subnet**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/003-createsubnet.png)

2. At the **Create subnet** page.
  + In the **VPC ID** section, click **ASG**.
  + In the **Subnet name** field, enter **Public Subnet**.
  + In the **Availability Zone** section, select the first Availability zone.
  + In the field **IPv4 CIRD block** enter **10.10.1.0/24**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/004-createsubnet.png)

3. Scroll to the bottom of the page, click **Create subnet**.

4. Click **Public Subnet**.
  + Click **Actions**.
  + Click **Edit subnet settings**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/005-createsubnet.png)

5. Click **Enable auto-assign public IPv4 address**.
  + Click **Save**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/006-createsubnet.png)

6. Click **Internet Gateways**.
  + Click **Create internet gateway**.
  
![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/007-createigw.png)

7. At the **Create internet gateway** page.
  + In the **Name tag** field, enter **IGW**.
  + Click **Create internet gateway**.
  
![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/008-createigw.png)

8. After successful creation, click **Actions**.
  + Click **Attach to VPC**.
 
![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/009-createigw.png)

9. At the **Attach to VPC** page.
  + In the **Available VPCs** section, select **ASG**.
  + Click **Attach internet gateway**.
  + Check the successful attaching process as shown below.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/010-createigw.png)

10. Next we will create a custom route table to assign to **Public Subnet**.
  + Click **Route Tables**.
  + Click **Create route table**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/011-creatertb.png)

11. At the **Create route table** page.
  + In the **Name** field, enter **Public Route Table**.
  + In the **VPC** section, select **VPC**.
  + Click **Create route table**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/012-creatertb.png)

12. After creating the route table successfully.
  + Click **Edit routes**.
  
![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/013-creatertb.png)

13. At the **Edit routes** page.
  + Click **Add route**.
  + In the **Destination** field, enter 0.0.0.0/0
  + In the **Target** section, select **Internet Gateway** and then select **IGW**.
  + Click **Save changes**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/014-creatertb.png)
![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/015-creatertb.png)

14. Click the **Subnet associations** tab.
  + Click **Edit subnet associations** to proceed with the associate custom route table we just created in **Public Subnet**.


![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/016-creatertb.png)

15. At the **Edit subnet associations** page.
  + Click on **Public Subnet**.
  + Click **Save associations**.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/017-creatertb.png)

16. Check that the route table information has been associated with **Public Subnet** and the internet route information has been pointed to the Internet Gateway as shown below.

![VPC](https://tamlv.buzz/aws-workshop/images/2.prerequisite/018-creatertb.png)