---
title : "Tạo Script Files"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---
Tại bước [Tạo AppSpec Reference File](/4-CreatePipelineComponents/4.2-createcodedeployymlfile/) ta tạo 1 file chứa các hướng dẫn giúp CodeDeploy triển khai ứng dụng của chúng ta. Chúng ta cần định nghĩa những câu lệnh để khởi động / dừng các containers, trong bước này, ta sẽ tạo file scripts để định nghĩa các lệnh đó.

{{% notice info %}}
  Bạn có thể xem các định nghĩa cơ bản của shell script [tại đây](https://docs.fileformat.com/programming/sh/) 
{{% /notice %}}

Đầu tiên, tạo 1 folder đặt tên scripts ở trong thư mục gốc của dự án. Bên trong, ta tạo thêm 2 file start.sh và stop.sh với nội dung tương ứng:

#### start.sh file
File này được dùng để khởi động các containers.

```bash
#start.sh
#!/bin/sh
cd /home/tamlv/chat-app

docker-compose up -d
```

1. Thay đổi thư mục làm việc sang thư mục gốc của dự án.
```
  cd /home/tamlv/chat-app
```

2. Lệnh này thực hiện công việc của các lệnh docker-compose build và docker-compose run. Nó build các images nếu chúng không có sẵn và khởi động các container. Nếu các images đã được build, nó sẽ khởi động container mà không cần build lại.
```
  docker-compose up -d
```

#### stop.sh file
```bash
#stop.sh

#!/bin/sh

cd /home/tamlv/chat-app
sudo cp -r build/* nginx

if ! docker info > /dev/null 2>&1; then
    service docker start
fi

docker-compose down
echo $?
```
1. Navigate to root directory of project
```
  cd /home/tamlv/chat-app
```

2. Sao chép tất cả file build của frontend vào trong nginx context.
```
  sudo cp -r build/* nginx
```

3. Kiểm tra xem docker service đã được khởi chạy hay chưa, nếu chưa, khởi chạy service.
```
  if ! docker info > /dev/null 2>&1; then
    service docker start
  fi
```

Tiếp theo chúng ta chuyển sang bước tạo appspec.yml file.