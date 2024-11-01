---
title : "Chuẩn bị tài cho Docker"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---
Ở bước này, chúng ta sẽ tạo 2 Dockerfile để dựng images cho các thành phần tạo nên Chat App. Sau đó chúng ta tạo 1 file docker-compose.yml để quản lý tất cả các images đó.

{{% notice info %}}
Dockerfile là 1 file văn bản được dùng để định nghĩa tất cả các dòng lệnh mà người dùng sẽ thực thi để tạo nên 1 image. Có thể gọi đây là 1 sách hướng dẫn để Docker dựng image.
Một vài tài liệu liên quan bạn có thể tìm hiểu thêm: [Documents](https://docs.docker.com/reference/dockerfile/#:~:text=A%20Dockerfile%20is%20a%20text,line%20to%20assemble%20an%20image).
{{% /notice %}}

Dưới đây là tổng quan về cấu trúc thư mục của chúng ta sau khi hoàn thành toàn bộ bước 2:

![Docker](https://tamlv.buzz/aws-workshop/images/2.prerequisite/002-docker.png)

### Nội dung
  - [Tạo Dockerfile cho Server](2.1.1-createserverimage/)
  - [Tạo Dockerfile cho máy chủ Nginx](2.1.2-createnginximage)