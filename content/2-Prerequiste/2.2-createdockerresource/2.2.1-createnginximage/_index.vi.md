---
title : "Tạo Nginx Image"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---

#### Tạo Nginx Image

Trong thư mục gốc, ta tạo 1 file mới và đặt tên là Dockerfile với nội dung sau:
```bash
#vi Dockerfile
FROM nginx:latest

WORKDIR /usr/share/nginx/html

COPY . .

RUN rm /etc/nginx/conf.d/default.conf

COPY ./nginx.conf /etc/nginx/conf.d

ENTRYPOINT [ "nginx" , "-g" , "daemon off;" ]
```

Cùng tìm hiểu ý nghĩa từng dòng lệnh:

1. Chọn base image cho container. Ở dòng này chúng ta sử dụng phiên bản chính thức mới mất của Nginx image từ Docker Hub.

```
FROM nginx:latest
```
2. Đặt thư mục làm việc bên trong container thành /usr/share/nginx/html. Đây là vị trí mặc định nơi Nginx phục vụ các tệp tĩnh, bất kỳ lệnh nào tiếp theo sẽ được thực thi trong thư mục này. Nếu thư mục này không tồn tại, Docker sẽ tạo nó.
```
WORKDIR /usr/share/nginx/html
```
3. Sao chép tất cả các files còn lại trong thư mục server vào thư mục làm việc vừa cài đặt ở bước 2 (/usr/share/nginx/html)
```
COPY . .
```

4. Xóa file cài đặt mặc định của Nginx.
```
RUN rm /etc/nginx/conf.d/default.conf
```

5. Sao chép file cài đặt của chúng ta vào trong container.
```
COPY ./nginx.conf /etc/nginx/conf.d
```

6. Chạy Nginx ở chế độ nền (daemon off;), điều này cần thiết cho các container vì chúng sẽ kết thúc khi tiến trình chính của chúng bị dừng. Chế độ nền giữ cho máy chủ Nginx luôn được chạy.
```
ENTRYPOINT [ "nginx", "-g", "daemon off;" ]:
```

Kết thúc.