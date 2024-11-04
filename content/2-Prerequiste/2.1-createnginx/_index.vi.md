---
title : "Thiết lập cài đặt nginx"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.1 </b> "
---

Cấu trúc thư mục của dự án:
![ConnectPrivate](https://tamlv.buzz/aws-workshop/images/folder_structure.png)
Tạo 1 file mới đặt tên là nginx.conf năm trong thư mục nginx ở cấp ngoài cùng với nội dung sau:
```bash
server {
    listen 80;
    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri /index.html =404;
    }

    location /api {
        proxy_pass http://localhost:4000;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $host;
        proxy_redirect off;
  }
}
```

Chi tiết các cài đặt:

1. Tạo 1 server ảo, mỗi server có thể lắng nghe request từ cổng hoặc máy chủ khác nhau.

```
server {}
```
2. Chỉ định block server này sẽ lắng nghe các request từ cổng 80, cổng mặc định của HTTP traffic.
```
listen 80;
```
3. Chỉ định thư mục chứa các files mà nginx sẽ trả về cho các connection hợp lệ.
```
root /usr/share/nginx/html;
```

4. Chỉ định file mặc định được trả về khi có request từ client.
```
index index.html;
```

5. Định nghĩa một block địa chỉ bao gồm các cài đặt để xử lý các request có dạng (/).
```
location / {}
```

6. Nếu request có địa chỉ $uri không tồn tại, trả về file mặc định (/index.html) trong root folder đã cài đặt ở block server. Nếu cả $uri và file index.html đều không tồn tại thì trả về trang 404.
```
try_files $uri /index.html =404;
```

7. Định nghĩa một block địa chỉ bao gồm các cài đặt để xử lý các request có dạng (/api). Trong dự án này, chúng ta sử dụng tiền tố /api để phân loại các request đến Backend. Bằng cách này ta có thể chạy cả Backend và Frontend trên cùng 1 ec2 instance.
```
location /api
```

8. proxy_pass directive điều hướng các requests phù hợp với dạng địa chỉ (/api) to đến một server khác (cụ thể ở đây là cùng server đó nhưng ở 1 cổng cụ thể - 4000). 
```
proxy_pass http://localhost:4000;
```
9. Chỉ định các thuộc tính của HTTP headers
```
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header Host $host;
proxy_redirect off;
```

Kết thúc. Phần chuẩn bị cài đặt cho Nginx đến đây là hoàn thành.