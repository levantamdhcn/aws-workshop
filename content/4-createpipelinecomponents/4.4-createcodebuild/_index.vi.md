---
title : "Chuẩn bị AWS CodeBuild"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### Chuẩn bị CodeBuild project

1. Truy cập [CodeBuild management console](https://eu-west-2.console.aws.amazon.com/codesuite/codebuild)
  + Click vào tab **Create project**. 
![CodeBuild](images/4.pipeline/002-codebuild.png)

2. Ở mục **Project name** ta nhập **chat-app-build**
![CodeBuild](images/4.pipeline/003-codebuild.png)

3. Kéo xuống dưới phần **Source -> Source 1 - Primary**:
  + Ở mục **Source provider**, chọn **Github**.
  + Ở mục **Credential**, chọn **Custom source credential**.
  + Ở mục **Credential type**, chọn **GitHub App**.
  + Click vào **create a new GitHub connection**.
![CodeBuild](images/4.pipeline/004-codebuild.png)

4. Ở mục **Create connection popup**
  + Ở mục **Connection name**, ta nhập **chat-app-connection**
  + Click vào **Connect to Github**.
![CodeBuild](images/4.pipeline/005-codebuild.png)

5. Click vào **Install a new app**
![CodeBuild](images/4.pipeline/006-codebuild.png)

6. Click vào **Sign In to Github**
![CodeBuild](images/4.pipeline/007-codebuild.png)

7. Sau khi đăng nhập thành công, kéo xuống phía dưới tới mục **Repository access**:
  + Chọn **Only select repositories**.
  + Chọn **chat-app**.
  + Click vào **Save**.
![CodeBuild](images/4.pipeline/008-codebuild.png)

8. Quay trở lại **Create connection popup**
  + Click vào **Connect**
![CodeBuild](images/4.pipeline/009-codebuild.png)

9. Quay trở lại mục **Source 1 - Primary**.
  + Ở mục **Connection**, chọn kết nối mà ta vừa tạo ở bước trên.
  + Ở mục **Repository**, chọn **Repository in my Github account** và chọn repo **chat-app**.
![CodeBuild](images/4.pipeline/010-codebuild.png)

10. Ở mục **Primary source webhook events**
  + Chọn vào **Rebuild every time a code change is pushed to this repository** để bật tự động build lại.
  + Chọn **Single build**
![CodeBuild](images/4.pipeline/011-codebuild.png)

11. Kéo xuống phần **Environment**
  + Ở mục **Service Role**, chọn **Existing service role**.
  + Ở mục **Role ARN**, chọn **ChatAppBuildRole**.
  + Ở mục **Build Spec -> Build specifications**, ta chọn **Use a buildspec file**.
  + Ở mục **Buildspec name - optional**, ta nhập **buildspec.yml** - đây là tên của buildspec referecne file chúng ta đã tạo từ bước [Create buildspect.yml file](/4-CreatePipelineComponents/4.3-createbuildspecfile/)

![CodeBuild](images/4.pipeline/012-codebuild.png)

12. Kéo xuống dưới phần **Artifacts -> Artifact 1 - Primary**
  + Ở mục **Type**, ta chọn **Amazon S3**.
  + Ở mục **Bucket name**, ta chọn **tamlv-chat-app-bucket**.
  + Ở mục **Name**, ta nhập **chatAppBuildArtifact**
  + Ở mục **Artifacts packaging**, ta chọn **Zip**

![CodeBuild](images/4.pipeline/013-codebuild.png)

13. Kéo xuống dưới đến phần **Logs**
  + Check on **CloudWatch logs - optional** to enable logging.
  + At **Group name - optional**, enter **aws/codebuild/chat-app-build**.
  + Click **Create build project**.

![CodeBuild](images/4.pipeline/014-codebuild.png)


#### Kiểm tra **Build process** của **CodeBuild**

1. Truy cập [Build projects management](https://eu-west-2.console.aws.amazon.com/codesuite/codebuild/projects)
  + Click vào tên của project mà ta đã tạo cho lab này ở bên trên.
2. Click vào **Start build**

![CodeBuild](images/4.pipeline/015-codebuild.png)

3. Chờ cho quá trình build thành công.

![CodeBuild](images/4.pipeline/016-codebuild.png)