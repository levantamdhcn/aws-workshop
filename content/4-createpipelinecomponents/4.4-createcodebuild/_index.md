---
title : "Create AWS CodeBuild"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### Prepare CodeBuild project

1. Access [CodeBuild management console](https://eu-west-2.console.aws.amazon.com/codesuite/codebuild)
  + Click the **Create project** tab. 
![CodeBuild](images/4.pipeline/002-codebuild.png)

2. At **Project name**, Enter **chat-app-build**
![CodeBuild](images/4.pipeline/003-codebuild.png)

3. Scroll down to **Source -> Source 1 - Primary** section:
  + At **Source provider**, select **Github**.
  + At **Credential**, select **Custom source credential**.
  + At **Credential type**, select **GitHub App**.
  + Click **create a new GitHub connection**.
![CodeBuild](images/4.pipeline/004-codebuild.png)

4. At **Create connection popup**
  + At **Connection name**, enter **chat-app-connection**
  + Click **Connect to Github**.
![CodeBuild](images/4.pipeline/005-codebuild.png)

5. Click **Install a new app**
![CodeBuild](images/4.pipeline/006-codebuild.png)

6. Click **Sign In to Github**
![CodeBuild](images/4.pipeline/007-codebuild.png)

7. After sign in, scroll down to **Repository access**:
  + Select **Only select repositories**.
  + Select **chat-app**.
  + Click **Save**.
![CodeBuild](images/4.pipeline/008-codebuild.png)

8. Return to **Create connection popup**
  + Click **Connect**
![CodeBuild](images/4.pipeline/009-codebuild.png)

9. Return to **Source 1 - Primary** section
  + At **Connection**, select connection we have just created.
  + At **Repository**, select **Repository in my Github account** and choose **chat-app** repository.
![CodeBuild](images/4.pipeline/010-codebuild.png)

10. At **Primary source webhook events**
  + Check **Rebuild every time a code change is pushed to this repository** to enable.
  + Select **Single build**
![CodeBuild](images/4.pipeline/011-codebuild.png)

11. Scroll down to **Environment**
  + At **Service Role**, select **Existing service role**.
  + At **Role ARN**, select **ChatAppBuildRole**.
  + At **Build Spec -> Build specifications**, select **Use a buildspec file**.
  + At **Buildspec name - optional**, enter **buildspec.yml** - this is name of file we created from [Create buildspect.yml file](/4-CreatePipelineComponents/4.3-createbuildspecfile/)

![CodeBuild](images/4.pipeline/012-codebuild.png)

12. Scroll down to **Artifacts -> Artifact 1 - Primary**
  + At **Type**, select **Amazon S3**.
  + At **Bucket name**, select **tamlv-chat-app-bucket**.
  + At **Name**, enter **chatAppBuildArtifact**
  + At **Artifacts packaging**, select **Zip**

![CodeBuild](images/4.pipeline/013-codebuild.png)

13. Scroll down to **Logs**
  + Check on **CloudWatch logs - optional** to enable logging.
  + At **Group name - optional**, enter **aws/codebuild/chat-app-build**.
  + Click **Create build project**.

![CodeBuild](images/4.pipeline/014-codebuild.png)


#### Check **Build process** in **CodeBuild**

1. Go to [Build projects management](https://eu-west-2.console.aws.amazon.com/codesuite/codebuild/projects)
  + Click on the name of the project we created for the lab.

2. Click on **Start build**

![CodeBuild](images/4.pipeline/015-codebuild.png)

3. Waiting for build success.

![CodeBuild](images/4.pipeline/016-codebuild.png)