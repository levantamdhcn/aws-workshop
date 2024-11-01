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
  
![Clean](images/5.clean/001-clean.png)

#### Xóa S3 bucket

1. Truy cập [giao diện quản trị dịch vụ System Manager - Session Manager](https://console.aws.amazon.com/systems-manager/session-manager).
  + Click vào S3 bucket mà chúng ta đã tạo cho bài lab này. (Example: tamlv-chat-app-bucket )
  + Click **Empty**.
  + Điền **permanently delete**, sau đó click **Empty** để tiến hành xóa object trong bucket.
  + Click **Exit**.

3. Sau khi xóa hết object trong bucket, click **Delete**

![Clean](images/5.clean/002-clean.png)

4. Điền tên S3 bucket, sau đó click **Delete bucket** để tiến hành xóa S3 bucket.

![Clean](images/5.clean/003-clean.png)

#### Xóa VPC

1. Truy cập [VPC service management console](https://console.aws.amazon.com/vpc/home)
   + Click **Your VPCs**.
   + Chọn VPC ta đã tạo cho bài lab: **ASG**.
   + Click **Actions**.
   + Click **Delete VPC**.

![Clean](images/5.clean/004-clean.png)

2. Trong ô xác nhận, nhập **delete**.
   + Click **Delete** để tiến hành xóa VPC.
   + Hành động này cũng sẽ xóa Internet Gateway, Security Group, Subnet, Route Table được gắn với VPC này.

![Clean](images/5.clean/005-clean.png)
3. Nhấn vào nút refresh, kiểm tra xem VPC đã xóa thành công hay chưa trước khi sang bước tiếp theo.

![Clean](images/5.clean/006-clean.png)

#### Xoa CodePipeline
1. Go to [CodePipeline service management console](https://console.aws.amazon.com/codesuite/codepipeline/pipelines)
   + Select the Pipeline we created for the lab: **ChatAppCodePipeline**.
   + Click **Delete Pipeline**.
![Clean](images/5.clean/007-clean.png)
2. In the confirm box, enter **delete**.
   + Click **Delete** to proceed with deleting Pipeline.
![Clean](images/5.clean/008-clean.png)

3. Click the refresh icon, check that CodePipeline have been deleted before proceeding to the next step.
![Clean](images/5.clean/009-clean.png)

#### Delete CodeDeploy
1. Go to [CodeBuild Applications management console](https://console.aws.amazon.com/codesuite/codebuild/projects)
   + Click on the Application we created for the lab: **ChatAppCodeDeploy**.
![Clean](images/5.clean/010-clean.png)
2. In the detail page, click **Delete Application**.
![Clean](images/5.clean/011-clean.png)

3. In the confirm box, enter **delete**.
   + Click **Delete** to proceed with deleting CodeDeploy Application.
![Clean](images/5.clean/012-clean.png)

4. Return to Applications list page, make sure the **ChatAppCodeDeploy** is deleted before move to next section.
![Clean](images/5.clean/013-clean.png)

#### Delete CodeBuild
1. Go to [CodeBuild Projects management console](https://console.aws.amazon.com/codesuite/codebuild/projects)
   + Click on the Project we created for the lab: **chat-app-build**.
   + Click **Actions**
   + Click **Delete**
![Clean](images/5.clean/014-clean.png)
2. In the detail page, click **Delete Application**.
![Clean](images/5.clean/011-clean.png)

3. In the confirm box, enter **delete**.
   + Click **Delete** to proceed with deleting CodeBuild Project.
![Clean](images/5.clean/015-clean.png)

4. Return to Projects list page, make sure the **chat-app-build** is deleted before move to next section.
![Clean](images/5.clean/016-clean.png)

#### Delete Github Connections
1. Go to [CodeSuit Connection management console](https://console.aws.amazon.com/codesuite/settings/connections)
   + Click on the connection we created for the lab: **chat-app-connection**.
   + Click **Delete**
![Clean](images/5.clean/017-clean.png)

2. In the confirm box, enter **delete**.
   + Click **Delete** to proceed with deleting connection.
![Clean](images/5.clean/018-clean.png)