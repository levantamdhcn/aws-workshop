---
title : "Build and test"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

In this step, we will test out Docker resources created in [Prepare Docker resources](/2-Prerequiste/2.2-createdockerresource/)

### A. Build
1. Open terminal inside root project, type **docker compose up**. Docker Compose will start build each services
![BuildAndTest](images/3.buildandtest/01-buildandtest.png)

2. Open another terminal, type **docker image ls**, check for 3 images we have just created
![BuildAndTest](images/3.buildandtest/02-buildandtest.png)


3. Open browser, at address bar, enter **localhost:4000**, we can see and error **Cannot GET /**. Our backend is successfully running on port 4000.
![BuildAndTest](images/3.buildandtest/03-buildandtest.png)

4. Open browser, at address bar, enter **localhost**, we can see default page of nginx because we did not copy any built files into nginx context yet.
![BuildAndTest](images/3.buildandtest/04-buildandtest.png)

All of our container works. We can move to the next section.
