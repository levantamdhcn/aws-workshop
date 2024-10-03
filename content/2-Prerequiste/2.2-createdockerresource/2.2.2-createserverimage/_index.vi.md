---
title : "Viết Dockerfile cho Server"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---

#### Tạo Dockerfile
Trong thư mục server, tạo 1 file mới và đặt tên là Dockerfile với nội dung sau:
```bash
# Build node server
FROM node:18.17.0-alpine3.18

# Working directory
WORKDIR /src

COPY package*.json ./

### Installing dependencies

RUN npm ci

# copy local files to app folder
COPY . .

EXPOSE 4000

CMD ["npm", "run dev"]
```

Cùng đi sâu và tìm hiểu ý nghĩa của từng dòng lệnh:

1. Chọn base image cho container. Ở dòng này, ta sẽ sử dụng Node.js runtime phiên bản 18.17.0 trên hệ điều hành Alpine Linux 3.18. Alpine là một một bản phân phối Linux nhẹ, giữ cho kích thước của image được tối ưu.

```
FROM node:18.17.0-alpine3.18
```
2. Cài đặt working directory trong container là /src. Mọi commands sau này sẽ được thực thi tại thư mục này. Nếu thư mục này chưa tồn tại, Docker sẽ tự động tạo mới.
```
WORKDIR /src
```
3. Chép 2 files package.json và package-lock.json (nếu tồn tại) từ thư mục server vào trong đường dẫn /src bên trong container
```
COPY package*.json ./
```

4. Thực thi lệnh npm ci bên trong container để cài đặt các gói, thư viện được liệt kê trong file package.json. Với lệnh npm ci, ta đảm bảo rằng sẽ cài đặt chính xác phiên bản của các gói, thư viện đã được cài lần trước đó trong package-lock.json.
```
RUN npm ci
```

5. Copy tất cả các files còn lại trong thư mục server vào trong đường dẫn /src trong container.
``` 
COPY . .
```

6. Lệnh này dùng để cài đặt cho container sẽ lắng nghe trên cổng 4000. Cho pháp các container khác trong cùng mạng có thể liên lạc qua với container này qua cổng 4000.
```
EXPOSE 4000
```

7. Chỉ định lệnh mặc định được chạy khi container được khởi tạo.
```
CMD ["npm", "run dev"]
```

{{% notice info %}}
Bước cuối cùng, ta tạo thêm 1 file đặt tên .dockerignore trong thư mục server với nội dung sau:
```
/node_modules
```
Khi build image, lệnh COPY . . sẽ bỏ qua thư mục này (do rất nặng, ta sẽ tạo ra thư mục này bên trong container với lệnh npm ci)
{{% /notice %}}

Kết thúc.