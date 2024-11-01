---
title : "Create security groups"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.4.3 </b> "
---

#### Create security groups

In this step, we will proceed to create the security groups used for our instances.

#### Create security group for Linux instance located in public subnet

1. Go to [VPC service management console](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.
  + Click **Create security group**.

![SG](images/2.prerequisite/018-createscgroup.png)

3. In the **Security group name** field, enter **Public SG**.
  + In the **Description** section, enter **Allow SSH and Ping to Server**.
  + In the **VPC** section, click the **X** to reselect the **ASG** you created for this lab.

![SG](images/2.prerequisite/020-createsg.png)

4. In the **Inbound rules** field, click **Add rule**, we need to set 2 rules for our instance.
  + Type **SSH** - Source **My IP** - Description **Allow SSH and Ping to Server**. Allow my IP access server with SSH protocol.
  + Type **HTTP** - Source **Anywhere-IPv4** - Description **Allow access to Server**. Allow everyone can access our website with HTTP protocol.

![SG](images/2.prerequisite/021-createsg.png)

5. Keep **Outbound rule**, drag the mouse to the bottom.
  + Click **Create security group**.

So we are done creating the necessary security groups for EC2 instances.