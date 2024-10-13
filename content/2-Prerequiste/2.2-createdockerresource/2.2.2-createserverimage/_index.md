---
title : "Create Server's Dockerfile"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.2.2 </b> "
---


#### Create Dockerfile
Inside server folder, create file named Dockerfile with following content:
```bash
# Build node server
FROM node:18.17.0-alpine3.18

# Working directory
WORKDIR /src

COPY package*.json ./

### Installing dependencies

RUN npm ci

# copy local files to app folder
COPY . .

EXPOSE 4000

CMD ["npm", "run dev"]
```

Let's break down the configuration:

1. Specifies the base image for the container. Here, we are using Node.js version 18.17.0 on an Alpine Linux 3.18 image. Alpine is a lightweight Linux distribution, which helps keep the image size small.

```
FROM node:18.17.0-alpine3.18
```
2. Sets the working directory inside the container to /src. Any subsequent commands will be executed in this directory. If it doesn't exist, Docker will create it.
```
WORKDIR /src
```
3. Copies package.json and package-lock.json (if it exists) from server's folder into the /src directory of the container
```
COPY package*.json ./
```

4. Run npm ci inside container to install packages in package.json. With npm ci, keep all version of package same as package-lock.json.
```
RUN npm ci
```

5. Copies all the remaining files from server's directory into the working directory (/src) of the container
```
COPY . .
```

6. This command tells Docker that the container listens on port 4000 at runtime (it doesn't actually publish the port).
```
EXPOSE 4000
```

7. Sets the default command to be run when the container starts.
```
CMD ["npm", "run dev"]
```

{{% notice info %}}
Last step, we make a new file named .dockerignore inside server folder with following content:
```
/node_modules
```
Command COPY . . will skip this folder when building image (This folder too large, npm ci will auto generate this folder).
{{% /notice %}}

End.