---
title : "Tạo IAM Role"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.3 </b> "
---

### Tạo IAM Role cho EC2

Ở bước này, chúng ta sẽ tiến hành tạo IAM Role cho EC2. Trong IAM Role, chúng ta sẽ tiến hành gán policy **AmazonS3ReadOnlyAccess**, policy này cho phép EC2 server lấy artifact từ S3 Bucket và tiến hành triển khai.

1. Đi tới [IAM service administration interface](https://console.aws.amazon.com/iamv2/)
2. Ở thanh điều hướng phía bên trái, chọn vào **Roles**.

![createpolicy](/images/2.prerequisite/038-iamrole.png)

3. Chọn **Create role**.

![createpolicy](/images/2.prerequisite/039-iamrole.png)

4. Chọn **AWS service**, tiếp theo chọn **EC2**.
  + Chọn vào **Next: Permissions**.

![createpolicy](/images/2.prerequisite/041-iamrole.png)

5. Tại ô tìm kiếm, nhập **S3** và bấm Enter để tìm policy.
  + Chọn vào policy có tên **AmazonS3ReadOnlyAccess**.
  + Chọn vào **Next: Tags.**

![createpolicy](/images/2.prerequisite/040-iamrole.png)

6. Chọn **Next: Review**.
7. Đặt tên Role **EC2S3ReadPermission** tại trường Role Name
  + Click vào **Create Role** \.

![namerole](/images/2.prerequisite/042-iamrole.png)

### Create IAM Role For AWS CodeDeploy
1. Quay lại màn hình **Roles**.
2. Click vào **Create role**.
![createpolicy](/images/2.prerequisite/039-iamrole.png)
3. Click vào **AWS service** và chọn vào **CodeDeploy**.
  + Click vào **Next: Permissions**.
![createpolicy](/images/2.prerequisite/043-iamrole.png)
4. Đặt tên Role **ChatAppCodeDeploy** tại trường Role Name
  + Click vào **Create Role** \.
![createpolicy](/images/2.prerequisite/044-iamrole.png)

Tiếp theo, chúng ta sẽ tiếp tục tạo **VPC** và **EC2** để triển khai ứng dụng.