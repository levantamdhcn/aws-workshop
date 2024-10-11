---
title : "Test Connection"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.4.5 </b> "
---

{{% notice info %}}
In this phase, we check if our instance works with VPC, Subnet and Security Group we attached.
{{% /notice %}}

To learn how to connect EC2 instances, you can refer to the lab:

- [Test EC2 Connection](https://www.youtube.com/watch?v=wWu67GyrUNY&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=42)
- [EC2 Instance Connect Endpoint Guide](https://www.youtube.com/watch?v=7NjNTnXon5s&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=44)

We use .pem file created at [Create EC2 Instance](2.4.4-createec2linux/) to establish a connection to the EC2 instance.

### A. Using Terminal without GUI
1. Open Terminal (or PowerShell, Git Bash,...)
    + Insert **cd /path-to-pem-file**
2. 
