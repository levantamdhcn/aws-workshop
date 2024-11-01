---
title : "Tạo AWS CodeBuild"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### Tạo AWS CodeBuild

1. Truy cập [CodeBuild management console](https://eu-west-2.console.aws.amazon.com/codesuite/codebuild)
  + Click vào tab **Create project**.  
![CodeBuild](/images/4.s3/010-s3.png)

2. Scroll down, at **S3 logging**, click **Enable**.
  + Uncheck **Allow only encrypted S3 buckets**.
  + Click **Choose a bucket name from the list**.
  + Select the S3 bucket you created.
  
![CodeBuild](/images/4.s3/011-s3.png)

3. Scroll down, click **Save** to save the configuration.

4. Access [System Manager - Session Manager service management console](https://console.aws.amazon.com/systems-manager/session-manager)
  + Click **Start session**.
  + Click **Private Windows Instance**.
  + Click **Start session**.

5. Type the command **ipconfig**.
  + Type the command **hostname**.
  + Click **Terminate** to exit the session, click **Terminate** again to confirm.

![CodeBuild](/images/4.s3/012-s3.png)


#### Check **Session logs** in **S3**

1. Go to [S3 service management console](https://s3.console.aws.amazon.com/s3/home)
  + Click on the name of the S3 bucket we created for the lab.

2. Click on the object name sessions log

![CodeBuild](/images/4.s3/013-s3.png)

3. On the objects detail page, click **Open**.

![CodeBuild](/images/4.s3/014-s3.png)

4. Object logs will be opened in a new tab in the browser. You can view the stored commands in session logs.

![CodeBuild](/images/4.s3/015-s3.png)