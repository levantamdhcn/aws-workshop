---
title : "Kiểm tra Image"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

Ở bước này, chúng ta sẽ tiến hành kiểm tra các tài nguyên Docker đã tạo ở bước [Prepare Docker resources](/2-Prerequiste/2.2-createdockerresource/).

### A. Build
1. Mở terminal trong thư mục gốc của dự án, nhập **docker compose up** và nhấn Enter. Docker Compose sẽ bắt đầu build các services ta đã định nghĩa trong docker-compose.yml.
![BuildAndTest](https://tamlv.buzz/aws-workshop/images/3.buildandtest/01-buildandtest.png)

2. Mở một terminal khác, nhập **docker image ls** và nhấn Enter, kiểm tra 2 images chúng ta vừa tạo.
![BuildAndTest](https://tamlv.buzz/aws-workshop/images/3.buildandtest/02-buildandtest.png)

3. Mở browser, trên thanh địa chỉ, ta nhập **localhost:4000**, nếu nhận được error **Cannot GET /** tức là backend của ta đã chạy trên cổng 4000.
![BuildAndTest](https://tamlv.buzz/aws-workshop/images/3.buildandtest/03-buildandtest.png)

4. Mở browser, trên thanh địa chỉ, ta nhập **localhost**, ta sẽ thấy trang mặc định của nginx bởi vì chúng ta chưa đẩy file cấu hình vào trong nginx context phía trong container.
![BuildAndTest](https://tamlv.buzz/aws-workshop/images/3.buildandtest/04-buildandtest.png)

Tất cả các container đã hoạt động. Chúng ta có thể chuyển sang bước tiếp theo.