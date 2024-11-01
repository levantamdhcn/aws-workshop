---
title : "Tạo docker-compose.yml file"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.2.3 </b> "
---

#### Tạo docker-compose.yml file

Docker Compose là 1 công cụ được dùng để định nghĩa và chạy nhiều container trong cùng 1 file YAML. Bằng cách này, ta có thể viết lại những cấu trúc phức tạp một cách dễ nhìn, dễ hiểu. Việc quản lý và tái tạo lại môi trường cho ứng dụng của ta trở nên dễ dàng hơn rất nhiều. Ngoài ra, việc sử dụng Docker Compose cũng hỗ trợ rất nhiều trong việc chia sẻ kiến trúc ứng dụng cũng như triển khai ứng dụng giữa các lập trình viên và giữa các team trở nên chính xác và dễ dàng hơn.

{{% notice info %}}
Cần chú ý đây là file YAML, vì vậy ta cần tuân thủ chặt chẽ định dạng về cách lùi đầu dòng cũng như tên của từng section.
{{% /notice %}}

![Docker Compose](https://tamlv.buzz/aws-workshop/images/2.prerequisite/046-createdockercompose.png)

Tại thư mục gốc của dự án, tạo 1 file mới đặt tên docker-compose.yml với nội dung sau:
```bash
#vi docker-compose.yml
version: '3.7'

services:
  nginx_app:
      container_name: nginx_app
      build:
        context: ./nginx
        dockerfile: Dockerfile
      ports:
        - 80:80
      restart: always
      depends_on:
        - node_app
        - mongo_db
  node_app:
    container_name: node_app
    build:
      context: ./server
      dockerfile: Dockerfile
    restart: always
    expose:
      - 4000
    ports:
      - "4000:4000"
    links:
      - mongo_db
    env_file: ./server/.env
    depends_on:
      - mongo_db
  mongo_db:
    container_name: mongo_db
    image: mongo
    volumes:
      - mongo_volume:/data/db
    expose:
      - 27017
    ports:
      - 27017:27017
volumes:
  mongo_volume:
```

Cùng đi sâu và tìm hiểu về nội dung cài đặt:

1. Chỉ định phiên bản định dạng của Docker Compose. Hiện tại phiên bản 3.7 được khuyến nghị cho Docker Engine 19.03.0 và cao hơn.

```
version: '3.7'
```
2. Start define our services.
```
services:
```
3. Cấu trúc của 1 service cơ bản sẽ như sau:
```
nginx_app:
      container_name: nginx_app
      build:
        context: ./nginx
        dockerfile: Dockerfile
      ports:
        - 80:80
      restart: always
```

3.1. Tên của service:
```
  nginx_app:
```

3.2. Tên của container:
```
    container_name: nginx_app
```

3.3. Định nghĩa các thành phần sử dụng để dựng image:
```
    build:
```

3.4. Chỉ định thư mục chính để dựng image, Docker sau đó sẽ tìm kiếm DockerFile và các tài nguyên khác trong thư mục này.
        context: ./nginx
```

3.5. Maps cổng 80 của máy chủ với cổng 80 của container, điều này cho phép máy chủ truy cập Nginx qua cổng 80.
```
        ports:
            - 80:80
```

3.6. Container sẽ luôn chạy lại trừ khi nó hoàn toàn bị dừng lại.
```
        restart: always
```

4. Đọc thêm về cách xây dựng 1 docker-compose file [Document](https://docs.docker.com/reference/compose-file/)