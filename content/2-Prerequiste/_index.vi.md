---
title : "Các bước chuẩn bị "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

{{% notice info %}}
We need to learn some basics of Docker, Nginx to perform this lab.
{{% /notice %}}

#### Nginx
nginx (engine x) là một máy chủ HTTP, reverse proxy, content cache, load balancer, TCP/UDP proxy server. Trong workshop này, chúng ta sử dụng nginx như là một reverse proxy.

Để tìm hiểu xem Nginx là gì, Ngix hoạt động như thế nào, các concepts cơ bản của Nginx và cách cấu hình một máy chủ Nginx cơ bản, ta có thể xem các hướng dẫn sau:
  - [Nginx cho người mới](https://nginx.org/en/docs/beginners_guide.html)
  - [Nginx với Docker](https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/)

#### Docker
Docker là một platform mã nguồn mở hỗ trợ phát triển, chia sẻ và chạy các ứng dụng với container.

Tìm hiểu các định nghĩa cơ bản của Docker:
  - [Docker cho người mới](https://docs.docker.com/get-started/)
  - [Containerize Nodejs App](https://docs.docker.com/guides/language/nodejs/containerize/)

### Content
  - [Chuẩn bị cấu hình Nginx](2.1-createnginx/)
  - [Chuẩn bị tài nguyên cho Docker](2.2-createdocker/)
  - [Tạo IAM Role](2.3-createiamrole/)
  - [Chuẩn bị VPC và EC2](2.4-createec2/)
  - [Tạo S3 Bucket](2.5-creates3bucket/)