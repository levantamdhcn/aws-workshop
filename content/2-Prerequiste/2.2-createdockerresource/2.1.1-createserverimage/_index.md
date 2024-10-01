---
title : "Create Server's Dockerfile"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
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

1. Defines a virtual server that Nginx will handle. Each server can listen on different ports or hostnames.

```
FROM node:18.17.0-alpine3.18
```
2. Specifics that server should listen for incomming connections at port 80, which is a default port for HTTP traffic. It means when we type http://serverip, it equal to http://serverip:80.
```
listen 80;
```
3. Specifics a root folder let Nginx know where to find files to serve the incomming connection.
```
root /usr/share/nginx/html;
```

4. Defines default file which will be served when client request.
```
index index.html;
```

5. This begins a location block for handling requests to the root URL (/). It defines how requests matching this location will be processed.
```
location / {}
```

6. Try to serve $uri (incomming request URL), if file is not exist, serve index.html in root folder instead. Neither files exist, return 404 page.
```
try_files $uri /index.html =404;
```

7. This begins a location block for handling requests to the root URL (/api). We use /api as prefix for all of our APIs. Using this location block will help us to server both BE and FE requests on the same EC2 instance by redirect all requests begin with /api to BE App port.
```
location /api
```

8. The proxy_pass directive forwards requests matching this location to another server. In this case, we forward API requests to our backend service which running on port 4000.
```
proxy_pass http://localhost:4000;
```
9. Configure HTTP headers attribute
```
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header Host $host;
proxy_redirect off;
```

End.

![VPC](/images/2.prerequisite/002-createvpc.png)