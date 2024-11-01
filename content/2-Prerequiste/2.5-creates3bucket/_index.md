---
title : "Create S3 Bucket"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---

We need a bucket to store our build artifact from CodeBuild.

1. Go to [S3 service management console](https://eu-west-2.console.aws.amazon.com/s3/home)
  + Click **Buckets**.
  + Click **Create Bucket**.
![S3](images/2.prerequisite/042-createbucket.png)

2. At **Bucket Name**, enter **chat-app-bucket**
![S3](images/2.prerequisite/043-createbucket.png)

3. Leave other settings as default, scroll down and click **Create Bucket**
![S3](images/2.prerequisite/044-createbucket.png)

4. Return the list and see that our bucket is created.
![S3](images/2.prerequisite/045-createbucket.png)

We have a bucket now. Let's move to next section!