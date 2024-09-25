---
title : "Preparing Nginx Config "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.1 </b> "
---

Our project folder structure:

We will create new file named nginx.conf inside nginx folder from root directory of project.
```bash
server {
    listen 80;
    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri /index.html =404;
    }

    location /api {
        proxy_pass http://localhost:4000;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $host;
        proxy_redirect off;
  }
}
```

Let's break down the configuration:

```
server {}
```
Defines a virtual server that Nginx will handle. Each server can listen on different ports or hostnames.

```
listen 80;
```
Specifics that server should listen for incomming connections at port 80, which is a default port for HTTP traffic. It means when we type http://serverip, it equal to http://serverip:80.

```
root /usr/share/nginx/html;
```
Specifics a root folder let Nginx know where to find files to serve the incomming connection.

```
index index.html;
```
Defines default file which will be served when client request.

```
location / {}
```
This begins a location block for handling requests to the root URL (/). It defines how requests matching this location will be processed.

```
try_files $uri /index.html =404;
```
Try to serve $uri (incomming request URL), if file is not exist, serve index.html in root folder instead. Neither files exist, return 404 page.

```
location /api
```
This begins a location block for handling requests to the root URL (/api). We use /api as prefix for all of our APIs. Using this location block will help us to server both BE and FE requests on the same EC2 instance by redirect all requests begin with /api to BE App port.

```
proxy_pass http://localhost:4000;
```
The proxy_pass directive forwards requests matching this location to another server. In this case, we forward API requests to our backend service which running on port 4000.

```
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header Host $host;
proxy_redirect off;
```