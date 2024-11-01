---
title : "Tạo appspec.yml file"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---
Ở bước này, chúng ta sẽ tạo file appspecyml được đọc bởi AWS CodeDeploy để quản lý tiến trình deployment.

{{% notice info %}}
Cần chú ý đây là file YAML, vì vậy ta cần tuân thủ chặt chẽ định dạng về cách lùi đầu dòng cũng như tên của từng section.
{{% /notice %}}

Một vài tài liệu liên quan đến AppSpec Reference file:
- [CodeDeploy AppSpec file reference](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file.html)
- [AppSpec File structure](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure.html)
- [AppSpec 'hooks' section](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html)

#### Tạo file **appspec.yml**

Đầu tiên, chúng ta tạo 1 file ở thư mục gốc của dự án đặt tên appspec.yml với nội dung sau:
```bash
#vi appspec.yml

version: 0.0
os: linux
files:
  - source: /
    destination: /home/ubuntu/chat-app
permissions:
  - object: scripts/
    mode: 777
    type:
      - directory
hooks:
  AfterInstall:
    - location: scripts/stop.sh
      timeout: 300
      runas: root
  ApplicationStart:
    - location: scripts/start.sh
      timeout: 300 
      runas: ubuntu
```

1. Với file này, ta định nghĩa các thông tin cần thiết cho quá trình Deploy như hệ điều hành, các quyền truy cập tài nguyên và các scripts sẽ được sử dụng trong từng giai đoạn như AfterInstall, ApplicationStart.

2. Trong mục permissions, ta chỉnh mode về 777, cho phép đọc, ghi và thực thi cho tất cả các người dùng cho thư mục scripts và tất cả các file bên trong.

3. Trong mục này, ta chỉ định phiên bản của file AppSpec. Đây là phần bắt buộc và không nên thay đổi.
```
version: 0.0
```

4. Ta cần chạy file stop.sh ở bước AfterInstall để sao chép các file build của frontend để Nginx có thể sử dụng trước khi chúng ta build container.

Tiếp theo, chúng ta sẽ tạo Build Spec Reference file.