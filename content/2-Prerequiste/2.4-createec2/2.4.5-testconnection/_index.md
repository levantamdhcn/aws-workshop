---
title : "Test Connection"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.4.5 </b> "
---

{{% notice info %}}
In this phase, we check if our instance works with VPC, Subnet and Security Group we attached.
{{% /notice %}}

To learn how to connect EC2 instances, you can refer to the lab:

- [Test EC2 Connection](https://www.youtube.com/watch?v=wWu67GyrUNY&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=42)
- [EC2 Instance Connect Endpoint Guide](https://www.youtube.com/watch?v=7NjNTnXon5s&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=44)

We use .pem file created at [Create EC2 Instance](/2-Prerequiste/2.4-createec2/2.4.4-createec2linux/) to establish a connection to the EC2 instance.

### A. Using Terminal without GUI
1. Open Terminal (or PowerShell, Git Bash,...)
    + Insert **cd /path-to-pem-file**
2. Insert **ssh -i /path-to-pem-file ubuntu@public-ip**
    + On first connection, OS ask for continue with new IP Address, type **yes**
![Test Connect](images/2.prerequisite/032-testconnect.png)
3. See the result. We are in.
![Test Connect](images/2.prerequisite/033-testconnect.png)

### B. Using Bitvise SSH Client within GUI

{{% notice info %}}
Bitvise SSH Client use private key to authenticate the connection so we need first generate private key version from pem file.
{{% /notice %}}

1. Go to [PuTTYgen Website](https://www.puttygen.com/) to download the software.
![Test Connect](images/2.prerequisite/034-testconnect.png)

2. Open Puttygen App to start generate private key.
+ Click **Load**
![Test Connect](images/2.prerequisite/035-testconnect.png)

3. Choose **All Files**
+ Select pem file of our EC2 Instance
![Test Connect](images/2.prerequisite/036-testconnect.png)

4. At **Key passphrase** and **Confirm passphrase**, Enter password for private key.
+ Click **Save private key**
![Test Connect](images/2.prerequisite/037-testconnect.png)

5. Go to [Download Bitvise SSH Client](https://bitvise.com/ssh-client-download) to download the software.
+ Click **Download Bitvise SSH Client**
![Test Connect](images/2.prerequisite/038-testconnect.png)

6. Open **Bitvise SSH Client**
+ At Host, Enter EC2 Instance public IP **18.132.42.239**
+ At Port, Enter SSH default port we allowed in Security Group **22**
+ At Username, Enter **ubuntu**
+ Click **Client key manager** to import generated private key.
![Test Connect](images/2.prerequisite/039-testconnect.png)

7. Click **Import and select our generated private key**
![Test Connect](images/2.prerequisite/040-testconnect.png)

8. After finish the import, return to the main screen an click Login.
+ Successfully connect to our EC2 instance.
![Test Connect](images/2.prerequisite/041-testconnect.png)

Our EC2 work as expected. Let's move to next section.
