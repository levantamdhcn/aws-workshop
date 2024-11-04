---
title : "Create Nginx Image"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.2.1 </b> "
---

#### Create Nginx Image
In root folder, create file named Dockerfile with following content:
```bash
#vi Dockerfile
FROM nginx:latest

WORKDIR /usr/share/nginx/html

COPY . .

RUN rm /etc/nginx/conf.d/default.conf

COPY ./nginx.conf /etc/nginx/conf.d

ENTRYPOINT [ "nginx" , "-g" , "daemon off;" ]
```

Let's break down the configuration:

1. Specifies the base image for the Docker image being built. It uses the latest version of the official Nginx image from Docker Hub.

```
FROM nginx:latest
```
2. Sets the working directory inside the container to /usr/share/nginx/html. Which is the default location where Nginx serves static files, any subsequent commands will be executed in this directory. If it doesn't exist, Docker will create it.
```
WORKDIR /usr/share/nginx/html
```
3. Copies all the remaining files from server's directory into the working directory (/usr/share/nginx/html) of the container
```
COPY . .
```

4. This command removes the default Nginx configuration file.
```
RUN rm /etc/nginx/conf.d/default.conf
```

5. Copy our customized configuration file into container. Which we have created from [Preparing Nginx Config](/2.1-createnginx/)
```
COPY ./nginx.conf /etc/nginx/conf.d
```

6. Runs Nginx in the foreground (daemon off;), which is necessary for containers since they terminate when their main process exits. This keeps the Nginx server running.
```
ENTRYPOINT [ "nginx", "-g", "daemon off;" ]:
```

End.