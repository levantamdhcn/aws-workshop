---
title : "Create EC2 Instance"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 2.4.4 </b> "
---

1. Truy cập [EC2 service management console](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click **Launch instances**.
  
![EC2](/images/2.prerequisite/022-createec2.png)

2. Ở mục **Step 1: Choose an Amazon Machine Image (AMI)**.
  + Click **Quick Start** và chọn **Ubuntu**.
  + Tại **Amazon Machine Image**, chọn **Ubuntu Server 24.04 LTS (free tier eligible)**.
  
![EC2](/images/2.prerequisite/028-createec2.png)

3. Kéo đến phần **Instance Type**.
 + Chọn **t2.micro**.
 + Click **Create new key pair** tại mục **Key pair (login)**.

![EC2](/images/2.prerequisite/030-createec2.png)

4. Trong **Create key pair** popup.  
 + Tại mục **Key pair name** ta nhập **chat-app**.
 + Tại mục **Key pair type** chọn **RSA**.
 + Tại mục **Private key file format** ta chọn **.pem**.
 + Click **Create key pair**.
 
![EC2](/images/2.prerequisite/029-createec2.png)

5. Kéo xuống phần **Network settings**, click vào **Edit**
  + Trong phần **Network** ta chọn **ASG**.
  + Tại mục **Subnet** ta chọn **Public Subnet**.
  + Tại mục **Auto-assign Public IP** ta chọn **Use subnet setting (Enable)**
  + Tại mục **Common security groups** ta chọn **Public SG**

![EC2](/images/2.prerequisite/031-createec2.png)

6. Kéo xuống phần **Advance details** và mở rộng phần này ra.
  + Ở phần IAM Instance profile, chọn **EC2S3ReadPermission** Policy mà chúng ta tạo tại bước [Create IAM Role](/2-Prerequiste/2.3-createiamrole/).
![EC2](/images/2.prerequisite/032-createec2.png)

7. Giữ các cài đặt khác ở chế độ mặc định vào kéo xuống dưới.
  + Click **Launch**.

8. Click vào **View Instances** để trở lại trang quản lý EC2 instances.