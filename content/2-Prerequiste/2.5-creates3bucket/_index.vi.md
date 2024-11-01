---
title : "Tạo S3 Bucket"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---

Chúng ta cần tạo 1 bucket để lưu các build artiface từ CodeBuild.

1. Truy cập [S3 service management console](https://eu-west-2.console.aws.amazon.com/s3/home)
  + Click vào **Buckets**.
  + Click vào **Create Bucket**.
![S3](/images/2.prerequisite/042-createbucket.png)

2. Tại mục **Bucket Name** ta nhập **chat-app-bucket**
![S3](/images/2.prerequisite/043-createbucket.png)

3. Các mục khác ta để mặc định sau đó kéo xuống dưới và click **Create Bucket**
![S3](/images/2.prerequisite/044-createbucket.png)

4. Trở lại trang chính và kiểm tra xem bucket đã tạo thành công hay chưa.
![S3](/images/2.prerequisite/045-createbucket.png)

Ta đã tạo thành công bucket cần thiết, chuyển sang bước tiếp theo!