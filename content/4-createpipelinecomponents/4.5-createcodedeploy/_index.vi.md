---
title : "Tạo AWS CodeDeploy"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 4.5 </b> "
---

#### Tạo CodeDeploy Application

1. Truy cập vào [CodeDeploy - AWS Developer Tools management console](https://eu-west-2.console.aws.amazon.com/codesuite/codedeploy/start)
  + Click vào **Create application**.
  
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/017-codedeploy.png)

2. Tại mục **Application configuration**.
  + Ở phần **Application name** ta nhập **ChatAppCodeDeploy**.
  + Ở phần **Compute platform**, ta chọn **EC2/On-premises**.
  + Click vào **Create application**.
  
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/018-codedeploy.png)

3. Quay trở lại phần **Application Detail** mà ta vừa tạo.
  + Click vào **Create deployment group**
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/019-codedeploy.png)

4. Ở phần **Deployment group name**
  + Nhập **ChatAppDeploymentGroup**
  + Ở phần **Service Role**, ta chọn **ChatAppCodeDeploy** ta đã tạo ở bước [Create IAM Role](/2-Prerequiste/2.3-createiamrole/)
  + Ở phần **Deployment Type**, ta chọn **In-place**.
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/020-codedeploy.png)

5. Kéo xuống dưới phần **Environment configuration**.
  + Chọn vào **Amazon EC2 instances**.
  + Nhập **Key: Name - Value: ChatApp** để dễ dàng quản lý hơn.

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/021-codedeploy.png)

6. Kéo xuống dưới phần **Load balancer**.
  + Bỏ chọn **Enable load balancing**.
  + Click vào **Create deployment group**.

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/022-codedeploy.png)


#### Tạo Deployment
1. Đi tới trang **Detail page** của Application chúng ta vừa tạo
  + Click vào **Create deployment**

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/023-codedeploy.png)

2. Ở phần **Deployment setting**:
  + Mục **Revision type**, ta chọn **My application is stored in Amazon S3**.
  + Mục **Revision location**, sao chép URI của artifact trong S3 Bucket và dán ở đây.
  + At **Revision file type**, select **.zip**

![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/024-codedeploy.png)

3. Kéo xuống phía dưới, click vào **Create deployment**

4. Chờ đợi cho đến khi quá trình deploy thành công.
![CodeDeploy](https://tamlv.buzz/aws-workshop/images/4.pipeline/025-codedeploy.png)