---
title : "Tạo các security groups"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.4.3 </b> "
---

#### Tạo các security groups

Ở bước này, ta sẽ tiến hành tạo các security groups cho instances của mình.

#### Tạo security group cho Linux instance được đặt trong public subnet

1. Truy cập [VPC service management console](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.
  + Click **Create security group**.

![SG](https://tamlv.buzz/aws-workshop/images/2.prerequisite/018-createscgroup.png)

3. Ở mục **Security group name** ta nhập **Public SG**.
  + ở mục **Description** ta nhập **Allow SSH and Ping to Server**.
  + Ở phần **VPC** ta chọn **X** để chọn VPC có tên **ASG** mà ta đã tạo ở bước trước.

![SG](https://tamlv.buzz/aws-workshop/images/2.prerequisite/020-createsg.png)

4. Ở mục **Inbound rules**, click vào **Add rule**, chúng ta cần cài 2 rules cho instance của mình.
  + Chọn Type **SSH** - Source **My IP** - Description **Allow SSH and Ping to Server**. Allow my IP access server with SSH protocol.
  + Type **HTTP** - Source **Anywhere-IPv4** - Description **Allow access to Server**. Allow everyone can access our website with HTTP protocol.

![SG](https://tamlv.buzz/aws-workshop/images/2.prerequisite/021-createsg.png)

5. Giữ nguyên cài đặt của **Outbound rule**.
  + Click **Create security group**.

Chúng ta đã hoàn thành tạo Security Group cho EC2 instance của mình.