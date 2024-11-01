+++
title = "Clean up resources"
date = 2024
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

We will take the following steps to delete the resources we created in this exercise.

#### Delete EC2 instance

1. Go to [EC2 service management console](https://console.aws.amazon.com/ec2/v2/home)
   + Click **Instances**.
   + Select **ChatApp** instances.
   + Click **Instance state**.
   + Click **Terminate instance**, then click **Terminate** to confirm.

2. Go to [IAM service management console](https://console.aws.amazon.com/iamv2/home#/home)
   + Click **Roles**.
   + In the search box, search for these roles: **ChatAppBuildRole**, **ChatAppCodeDeploy**, **ChatAppCodePipelineRole**, **EC2S3ReadPermission**
   + Click **Delete**, then enter the role name **SSM-Role** and click **Delete** to delete the role.

![Clean](images/5.clean/001-clean.png)

#### Delete S3 bucket
1. Go to [S3 service management console](https://s3.console.aws.amazon.com/s3/home)
   + Click on the S3 bucket we created for this lab. (Example: tamlv-chat-app-bucket )
   + Click **Empty**.
   + Enter **permanently delete**, then click **Empty** to proceed to delete the object in the bucket.
   + Click **Exit**.

3. After deleting all objects in the bucket, click **Delete**

![Clean](images/5.clean/002-clean.png)

4. Enter the name of the S3 bucket, then click **Delete bucket** to proceed with deleting the S3 bucket.

![Clean](images/5.clean/003-clean.png)

#### Delete VPC

1. Go to [VPC service management console](https://console.aws.amazon.com/vpc/home)
   + Click **Your VPCs**.
   + Select the VPC we created for the lab: **ASG**.
   + Click **Actions**.
   + Click **Delete VPC**.

![Clean](images/5.clean/004-clean.png)

2. In the confirm box, enter **delete**.
   + Click **Delete** to proceed with deleting VPC.
   + This action will also delete Internet Gateway, Security Group, Subnet, Route Table attached to this VPC.

![Clean](images/5.clean/005-clean.png)
3. Click the refresh icon, check that VPC have been deleted before proceeding to the next step.

![Clean](images/5.clean/006-clean.png)

#### Delete CodePipeline
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