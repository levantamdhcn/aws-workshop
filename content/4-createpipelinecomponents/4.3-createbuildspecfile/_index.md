---
title : "Create buildspec.yml file"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 4.3 </b> "
---
In this step, we will create a buildspec.yml file which used by AWS CodeBuild. A buildspec is a collection of build commands and related settings, in YAML format, that CodeBuild uses to run a build.

{{% notice info %}}
Remember, this is a YAML file, so the formatting must be consistent (otherwise the build will fail).

Some documents we can refer:
- [Build specification reference for CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html)
- [How CodeBuild works](https://docs.aws.amazon.com/codebuild/latest/userguide/concepts.html#concepts-how-it-works)
{{% /notice %}}

![Build Spec](/images/4.s3/001-builspec.png)

#### Create **buildspec.yml** file

First, create an buildspec.yml file with the following contents inside the project's root directory.
```bash
#vi buildspec.yml

version: 0.2
phases:
  install:
    commands:
      - echo "the installation phase begins"
  pre_build:
    commands:
      - echo "the prebuild phase begins"
      - cd client
      - npm install
  build:
    commands:
      - echo "the build phase begins"
      # - echo `pwd`
      - npm run build
      # - echo `ls -la`
  post_build:
    commands:
      - echo "the post build phase. navigating back to root path"
      - cp -R build/ ../
artifacts:
  files:
    - build/**/*
    - appspec.yml
    - server/**/*
    - nginx/*
    - scripts/*
    - docker-compose.yml
    - Dockerfile
```

1. In first section, we define informations for Build process about phases, which command to run in each phase (install, pre_build, build, post_build).

2. ``artifacts/files`` represents the locations that contain the build output artifacts in the build environment. Contains a sequence of scalars, with each scalar representing a separate location where CodeBuild can find build output artifacts.

Next, we will proceed to create CodeBuild service.