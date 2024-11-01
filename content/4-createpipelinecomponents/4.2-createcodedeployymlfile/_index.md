---
title : "Create appspec.yml file"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---
In this step, we will create a appspec.yml file which used by AWS CodeDeploy to manage the deployment process.

{{% notice info %}}
Remember, this is a YAML file, so the formatting must be consistent (otherwise the build will fail).
{{% /notice %}}

Some documents we can refer:
- [CodeDeploy AppSpec file reference](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file.html)
- [AppSpec File structure](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure.html)
- [AppSpec 'hooks' section](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html)

#### Create **appspec.yml** file

First, create an appspec.yml file with the following contents inside the project's root directory.
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

1. With this file, we define informations for Deploy process about operating system, permissions for sources and scripts to be used during stages like AfterInstall, ApplicationStart.

2. In the permissions section, we set the mode to 777, which grants read, write, and execute permissions to everyone for the scripts folder and all the files inside it.

3. This section specifies the version of the AppSpec file. Do not change this value. It is required. Currently, the only allowed value is 0.0. It is reserved by CodeDeploy for future use.
```
version: 0.0
```

4. We need to run stop.sh during the AfterInstall stage, even though this stage occurs before ApplicationStart. In stop.sh, we copy the built files into the destination folder, which will be used by the Nginx container. This container will start during the ApplicationStart stage.

Next, we will proceed to create Build Spec Reference file.