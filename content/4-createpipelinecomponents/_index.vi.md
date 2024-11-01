---
title : "Tạo các thành phần của Pipeline"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

The CI/CD Pipeline is built from automate the build, deploy task. With cloud-native tools, we need help from CodeBuild, CodeDeploy, CodePipeline services.
In this section, we will proceed to create CodeBuild, CodeDeploy, CodePipeline and configure the our pipeline.

Pipeline CI/CD được xây dựng để tự động hóa các quá trình build và deploy. Với các dịch vụ cloud-native, chúng ta sử dụng các dịch vụ CodeBuild, CodeDeploy, CodePipeline.
Trong phần này, chúng ta sẽ tiến hành tạo CodeBuild, CodeDeploy, CodePipeline và cấu hình pipeline của chúng ta.

![port-fwd](images/arc-log.png) 

### Content:

   - [Tạo Scripts Files](/4-CreatePipelineComponents/4.1-createscriptfiles/)
   - [Tạo AppSpec file reference](/4-CreatePipelineComponents/4.2-createcodedeployymlfile/)
   - [Tạo Build specification reference](/4-CreatePipelineComponents/4.3-createbuildspecfile)
   - [Tạo CodeBuild](/4-CreatePipelineComponents/4.4-createcodebuild/)
   - [Tạo CodeDeploy](/4-CreatePipelineComponents/4.5-createcodedeploy/)
   - [Tạo CodePipeline](/4-CreatePipelineComponents/4.6-createcodepipeline/)