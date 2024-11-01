+++
title = "Dọn dẹp tài nguyên  "
date = 2021
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.

#### Xóa EC2 instance

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Chọn **ChatApp** instance.
  + Click **Instance state**.
  + Click **Terminate instance**, sau đó click **Terminate** để xác nhận.

2. Truy cập [giao diện quản trị dịch vụ IAM](https://console.aws.amazon.com/iamv2/home#/home)
  + Click **Roles**.
  + Tại ô tìm kiếm, tìm kiếm các tên sau: **ChatAppBuildRole**, **ChatAppCodeDeploy**, **ChatAppCodePipelineRole**, **EC2S3ReadPermission**
  + Click **Delete**
  
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/001-clean.png)

#### Xóa S3 bucket

1. Truy cập [giao diện quản trị dịch vụ System Manager - Session Manager](https://console.aws.amazon.com/systems-manager/session-manager).
  + Click vào S3 bucket mà chúng ta đã tạo cho bài lab này. (Example: tamlv-chat-app-bucket )
  + Click **Empty**.
  + Điền **permanently delete**, sau đó click **Empty** để tiến hành xóa object trong bucket.
  + Click **Exit**.

3. Sau khi xóa hết object trong bucket, click **Delete**

![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/002-clean.png)

4. Điền tên S3 bucket, sau đó click **Delete bucket** để tiến hành xóa S3 bucket.

![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/003-clean.png)

#### Xóa VPC

1. Truy cập [VPC service management console](https://console.aws.amazon.com/vpc/home)
   + Click **Your VPCs**.
   + Chọn VPC ta đã tạo cho bài lab: **ASG**.
   + Click **Actions**.
   + Click **Delete VPC**.

![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/004-clean.png)

2. Trong ô xác nhận, nhập **delete**.
   + Click **Delete** để tiến hành xóa VPC.
   + Hành động này cũng sẽ xóa Internet Gateway, Security Group, Subnet, Route Table được gắn với VPC này.

![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/005-clean.png)
3. Nhấn vào nút refresh, kiểm tra xem VPC đã xóa thành công hay chưa trước khi sang bước tiếp theo.

![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/006-clean.png)

#### Xoa CodePipeline
1. Truy cập [CodePipeline service management console](https://console.aws.amazon.com/codesuite/codepipeline/pipelines)
   + Chọn Pipeline mà ta đã tạo cho bài lab: **ChatAppCodePipeline**.
   + Click **Delete Pipeline**.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/007-clean.png)
2. Trong ô xác nhận, nhập **delete**.
   + Click **Delete** để tiến hành xóa Pipeline.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/008-clean.png)

3. Click vào nút refresh, kiểm tra xem CodePipeline đã được xóa thành công hay chưa.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/009-clean.png)

#### Xóa CodeDeploy
1. Truy cập [CodeBuild Applications management console](https://console.aws.amazon.com/codesuite/codebuild/projects)
   + Click vào Application ta đã tạo cho bài lab: **ChatAppCodeDeploy**.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/010-clean.png)
2. Ở trang chi tiết, click **Delete Application**.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/011-clean.png)

3. Ở ô xác nhận, nhập **delete**.
   + Click **Delete** để tiến hành xóa CodeDeploy Application.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/012-clean.png)

4. Quay trở về trang danh sách Applications, kiểm tra xem **ChatAppCodeDeploy** đã xóa thành công chưa.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/013-clean.png)

#### Xóa CodeBuild
1. Truy cập [CodeBuild Projects management console](https://console.aws.amazon.com/codesuite/codebuild/projects)
   + Click vào Project chúng ta đã tạo cho bài lab: **chat-app-build**.
   + Click **Actions**
   + Click **Delete**
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/014-clean.png)
2. Ở trang chi tiết, click **Delete Application**.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/011-clean.png)

3. Ở ô xác nhận, nhập **delete**.
   + Click **Delete** để tiến hành xóa CodeBuild Project.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/015-clean.png)

4.  Quay trở về trang danh sách Projects, kiểm tra **chat-app-build** đã được xóa trước khi sang bước tiếp theo.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/016-clean.png)

#### Xóa Github Connections
1. Truy cập [CodeSuit Connection management console](https://console.aws.amazon.com/codesuite/settings/connections)
   + Click vào connection ta đã tạo cho bài lab: **chat-app-connection**.
   + Click **Delete**
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/017-clean.png)

2. Ở ô xác nhận, ta nhập **delete**.
   + Click **Delete** để tiến hành xóa connection.
![Clean](https://tamlv.buzz/aws-workshop/images/5.clean/018-clean.png)