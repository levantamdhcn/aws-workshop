---
title : "Create docker-compose.yml file"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.2.3 </b> "
---

#### Create docker-compose.yml file

Docker Compose is a tool for defining and running multi-container application in a single YAML file. This simplifies the complex architecture. Make it easier to manager and replicate your application environment. Docker Compose can create a configuration that easy to share among developers and team.

{{% notice info %}}
Remember, this is a YAML file, so the formatting must be consistent (otherwise the build will fail).
{{% /notice %}}

![Docker Compose](/images/2.prerequisite/046-createdockercompose.png)

In root folder, create file named docker-compose.yml with following content:
```bash
#vi docker-compose.yml
version: '3.7'

services:
  nginx_app:
      container_name: nginx_app
      build:
        context: ./nginx
        dockerfile: Dockerfile
      ports:
        - 80:80
      restart: always
      depends_on:
        - node_app
  node_app:
    container_name: node_app
    build:
      context: ./server
      dockerfile: Dockerfile
    restart: always
    expose:
      - 4000
    ports:
      - "4000:4000"
    env_file: ./server/.env
```

Let's break down the configuration:

1. This instructs Docker Compose that we’re using version 3.7 of the tool. Version 3.7 is suitable for Docker Engine 19.03.0 and higher.

```
version: '3.7'
```
2. Start define our services.
```
services:
```
3. A service architecture will contains
```
nginx_app:
      container_name: nginx_app
      build:
        context: ./nginx
        dockerfile: Dockerfile
      ports:
        - 80:80
      restart: always
```

3.1. A service name
```
  nginx_app:
```

3.2. Name of the container after build.
```
    container_name: nginx_app
```

3.3. Instruction how to build the image
```
    build:
```

3.4. Specifies the build context as ./nginx, which means Docker will look for the Dockerfile and other resources in that directory
```
        context: ./nginx
```

3.5. Maps port 80 of the host to port 80 of the container, making the Nginx server accessible from the host.
```
        ports:
            - 80:80
```

3.6. Configures the container to always restart unless explicitly stopped.
```
        restart: always
```

4. For more information of how to write a docker-compose file, you can refer to this [Document](https://docs.docker.com/reference/compose-file/)