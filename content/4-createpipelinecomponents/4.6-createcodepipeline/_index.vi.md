---
title : "Tạo AWS CodePipeline"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 4.6 </b> "
---

#### Tạo AWS CodePipeline

1. Truy cập vào [S3 Management Console](https://eu-west-2.console.aws.amazon.com/s3/home?region=eu-west-2)
  + Click vào **Buckets** ở menu điều hướng bên tay trái.
  + Chọn bucket **tamlv-chat-app-bucket**.
  + Chọn vào **chat-app-build**, và click vào **Copy S3 URI**. Ta cần URI này khi cấu hình CodePipeline.

2. Truy cập [CodePipeline - Pipelines management console](https://eu-west-2.console.aws.amazon.com/codesuite/codepipeline/pipelines)
  + Click vào **Create Pipeline**.
  
![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/026-codepipeline.png)

3. Kéo xuống phía dưới phần **Pipeline settings**.
  + Ta nhập **ChatAppCodePipeline** ở mục **Pipeline name**.
  + Ở phần **Execution mode** ta chọn **Queued (Pipeline type V2 required)**.
  + Ở phần **Service role** ta chọn **New service role**. Ta sẽ để AWS tạo 1 Role mới cho CodePipeline với tên **ChatAppCodePipelineRole**.
  + Chọn vào **Allow AWS CodePipeline to create a service role so it can be used with this new pipeline**.
  
![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/027-codepipeline.png)

4. Kéo xuống phía dưới phần **Primary source webhook events**.
  + Chọn vào **Rebuild every time a code changes is pushed to this repository**. Lựa chọn này đảm bảo rằng pipeline của chúng ta sẽ được trigger mỗi khi ta push code mới lên repository.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/028-codepipeline.png)

5. Click **Next**, ta chuyển tới phần **Add source stage**.
  + Ở mục **Source provider**, ta chọn Amazon S3.
  + Ở mục **Bucket**, ta chọn **tamlv-chat-app-bucket**, đây là bucket lưu artifact.
  + Ở mục **S3 object key**, dán S3 URI mà ta đã sao chép từ bước 1. Chỉ giữ lại **ChatAppBuildArtifact/chat-app-build.zip**
  + Ở mục **Change detection options**, ta chọn **AWS CodePipeline**.
  + Click vào **Next**.
![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/029-codepipeline.png)

6. Chuyển tới phần **Build**.
  + Ở mục **Build provider**, chọn **Other build providers**.
  + Chọn **AWS CodeBuild**.
  + Chọn **chat-app-build** ở phần **Project name**.
  + Kéo xuống dưới, click vào **Next**.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/030-codepipeline.png)

7. Ta chuyển tới phần **Deploy**.
  + Ở mục **Deploy provider**, ta chọn **AWS CodeDeploy**.
  + Ở mục **Input artifacts**, ta chọn **SourceArtifact**.
  + Ở mục **Application name**, ta chọn **ChatAppCodeDeploy**.
  + Ở mục **Deployment group**, ta chọn **ChatAppDeploymentGroup**.
  + Click vào **Next**.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/031-codepipeline.png)

8. Tại trang **Review**, ta kiểm tra lại tất cả thông tin một lượt rồi sau đó click vào **Create pipeline**.

#### Kiểm tra **Pipeline**.
1. Chúng ta đẩy một commit tới đến Github Repository.

2. Kiểm tra từng stage của pipeline.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/032-codepipeline.png)

3. Tất cả các stage đã thành công.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/tamlv.buzz/aws-workshop/images/4.pipeline/033-codepipeline.png)