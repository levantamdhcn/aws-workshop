---
title : "Create Script Files"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

In [Create AppSpec Reference File](/4-CreatePipelineComponents/4.2-createcodedeployymlfile/)  we create a file provide instruction for CodeDeploy to deploy our application. We need a set of command to start/stop our containers, in this step, we will file scripts file contain these commands.

{{% notice info %}}
  You may need to learn some basic concept of shell script [here](https://docs.fileformat.com/programming/sh/) 
{{% /notice %}}

First, create a folder named scripts inside root directory of our project. Inside that, create each file below with corresponding content.

#### start.sh file
This file will be used to start the containers.

```bash
#start.sh
#!/bin/sh
cd /home/tamlv/chat-app

docker-compose up -d
```

1. Navigate to root directory of project
```
  cd /home/tamlv/chat-app
```

2. This command does the work of the docker-compose build and docker-compose run commands. It builds the images if they are not located locally and starts the containers. If images are already built, it will fork the container directly
```
  docker-compose up -d
```

#### stop.sh file
```bash
#stop.sh

#!/bin/sh

cd /home/tamlv/chat-app
sudo cp -r build/* nginx

if ! docker info > /dev/null 2>&1; then
    service docker start
fi

docker-compose down
echo $?
```
1. Navigate to root directory of project
```
  cd /home/tamlv/chat-app
```


2. Copy all frontend's built files into nginx context to be served.
```
  sudo cp -r build/* nginx
```

3.
```
  if ! docker info > /dev/null 2>&1; then
    service docker start
  fi
```

Next, we will proceed to create an S3 bucket to store session logs.