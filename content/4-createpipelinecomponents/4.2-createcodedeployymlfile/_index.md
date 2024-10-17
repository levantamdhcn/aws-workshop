---
title : "Create S3 Bucket"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---
In this step, we will create a appspec.yml file which used by AWS CodeDeploy to manage the deployment process.

{{% notice info %}}
Remember, this is a YAML file, so the formatting must be consistent (otherwise the build will fail).
{{% /notice %}}

#### Create **appspec.yml** file

1. Create appspec.yml inside root directory of project with following content.
```bash
#vi appspec.yml

version: 0.0
os: linux
files:
  - source: /
    destination: /home/ubuntu/chat-app
permissions:
  - object: scripts/
    mode: 777
    type:
      - directory
hooks:
  AfterInstall:
    - location: scripts/stop.sh
      timeout: 300
      runas: root
  ApplicationStart:
    - location: scripts/start.sh
      timeout: 300 
      runas: ubuntu
```

![S3](/images/4.s3/005-s3.png)

2. At the **Create bucket** page.
  + In the **Bucket name** field, enter the bucket name **lab-yourname-bucket-0001**
  + In the **Region** section, select **Region** you are doing the current lab.

![S3](/images/4.s3/006-s3.png)

 {{%notice tip%}}
The name of the S3 bucket must not be the same as all other S3 buckets in the system. You can substitute your name and enter a random number when generating the S3 bucket name.
{{%/notice%}}

3. Scroll down and click **Create bucket**.

![S3](/images/4.s3/007-s3.png)

 {{%notice tip%}}
When we created the S3 bucket we did **Block all public access** so our EC2 instances won't be able to connect to S3 via the internet.
In the next step, we will configure the S3 Gateway Endpoint feature to allow EC2 instances to connect to the S3 bucket via the VPC's internal network.
{{%/notice%}}