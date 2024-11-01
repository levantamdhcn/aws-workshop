---
title : "Tạo buildspec.yml file"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.3 </b> "
---
Trong bước này, chúng ta sẽ tạo file buildspec.yml, file này sẽ được sử dụng bởi AWS CodeBuild. Builspec là một tập hợp các lệnh build và các cài đặt liên quan, viêt dưới định dạng YAML.

{{% notice info %}}
Cần chú ý đây là file YAML, vì vậy ta cần tuân thủ chặt chẽ định dạng về cách lùi đầu dòng cũng như tên của từng section.
{{% /notice %}}

Một vài tài liệu chúng ta có thể tìm hiểu thêm về file buildspec:
- [Build specification reference for CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html)
- [How CodeBuild works](https://docs.aws.amazon.com/codebuild/latest/userguide/concepts.html#concepts-how-it-works)

![Build Spec](/images/4.s3/001-builspec.png)

#### Tạo **buildspec.yml** file

Đầu tiên, ta tạo 1 file ở trong thư mục gốc của dự án, đặt tên buildspec.yml với nội dung sau:
```bash
#vi buildspec.yml

version: 0.2
phases:
  install:
    commands:
      - echo "the installation phase begins"
  pre_build:
    commands:
      - echo "the prebuild phase begins"
      - cd client
      - npm install
  build:
    commands:
      - echo "the build phase begins"
      # - echo `pwd`
      - npm run build
      # - echo `ls -la`
  post_build:
    commands:
      - echo "the post build phase. navigating back to root path"
      - cp -R build/ ../
artifacts:
  files:
    - build/**/*
    - appspec.yml
    - server/**/*
    - nginx/*
    - scripts/*
    - docker-compose.yml
    - Dockerfile
```

1. Trong phần đầu tiên, chúng ta định nghĩa thông tin cho quá trình Build cho các các stage, lệnh nào sẽ chạy trong mỗi stage (install, pre_build, build, post_build).

2. ``artifacts/files`` là các tài nguyên cho quá trình build.

Tiếp theo, chúng ta sẽ tiến hành tạo AWS CodeBuild.