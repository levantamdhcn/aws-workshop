---
title : "Create AWS CodePipeline"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 4.6 </b> "
---

#### Create AWS CodePipeline

1. Access [S3 Management Console](https://eu-west-2.console.aws.amazon.com/s3/home?region=eu-west-2)
  + Click **Buckets** in the left navigation.
  + Select **tamlv-chat-app-bucket**.
  + Check on **chat-app-build**, and click **Copy S3 URI**. We need this key to put on CodePipeline setup.

2. Access [CodePipeline - Pipelines management console](https://eu-west-2.console.aws.amazon.com/codesuite/codepipeline/pipelines)
  + Click **Create Pipeline**.
  
![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/026-codepipeline.png)

3. Scroll down, at **Pipeline settings**.
  + Enter **ChatAppCodePipeline** at **Pipeline name**.
  + At **Execution mode**, select **Queued (Pipeline type V2 required)**.
  + At **Service role**, select **New service role**. We gonna let AWS created new Role for our CodePipeline with name **ChatAppCodePipelineRole**.
  + Check on **Allow AWS CodePipeline to create a service role so it can be used with this new pipeline**.
  
![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/027-codepipeline.png)

4. Scroll down to **Primary source webhook events**.
  + Check on **Rebuild every time a code changes is pushed to this repository**. This option make sure that our pipeline will run every time new code pushed.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/028-codepipeline.png)

5. Click **Next**, we move to **Add source stage**.
  + At **Source provider**, select Amazon S3.
  + At **Bucket**, select **tamlv-chat-app-bucket**, where CodeBuild store the artifact.
  + At **S3 object key**, paste S3 URI we copied from step 1. Keep **ChatAppBuildArtifact/chat-app-build.zip**
  + At **Change detection options**, select **AWS CodePipeline**.
  + Click **Next**.
![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/029-codepipeline.png)

6. We move to **Build** section.
  + At **Build provider**, choose **Other build providers**.
  + Select **AWS CodeBuild**.
  + Select **chat-app-build** at **Project name** section.
  + Scroll down, click **Next**.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/030-codepipeline.png)

7. We move to **Deploy** section.
  + At **Deploy provider**, choose **AWS CodeDeploy**.
  + At **Input artifacts**, select **SourceArtifact**.
  + At **Application name**, select **ChatAppCodeDeploy**.
  + At **Deployment group**, select **ChatAppDeploymentGroup**.
  + Click **Next**.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/031-codepipeline.png)

8. At **Review** section, re-check all information and click **Create pipeline**.

#### Check **Our Pipeline**.
1. Push new commit to Github Repository.

2. See that pipeline go through each stage.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/032-codepipeline.png)

3. All the stage success.

![CodePipeline](https://tamlv.buzz/aws-workshop/images/4.pipeline/033-codepipeline.png)