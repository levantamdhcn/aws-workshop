---
title : "Kiểm tra kết nối"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.4.5 </b> "
---

{{% notice info %}}
Trong bước này, chúng ta tiến hành kiểm tra hoạt động instances của mình với VPC, Subnet và Security Group mà ta đã tạo ở các bước trước.
{{% /notice %}}

Để tìm hiểu thêm vè các cách kết nối tới EC2 instances, ta có thể xem  bài lab sau:
To learn how to connect EC2 instances, you can refer to the lab:

- [Test EC2 Connection](https://www.youtube.com/watch?v=wWu67GyrUNY&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=42)
- [EC2 Instance Connect Endpoint Guide](https://www.youtube.com/watch?v=7NjNTnXon5s&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=44)

Ta sử dụng file .pem đã tạo ở bước [Create EC2 Instance](/2-Prerequiste/2.4-createec2/2.4.4-createec2linux/) để xác thực kết nối đển EC2 instance.

### A. Sử dụng Terminal
1. Mở terminal Terminal (hoặc PowerShell, Git Bash,...)
    + Nhập **cd /path-to-pem-file** và nhấn Enter
2. Tiếp tục nhập **ssh -i /path-to-pem-file ubuntu@public-ip** và nhấn Enter
    + Ở lần kết nối đầu tiền, hệ điều hành xác định host mới và sẽ hỏi xác nhận truy nhập, ta nhập **yes** và nhấn Enter
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/032-testconnect.png)
3. Kiểm tra kết quả. Như trong hình là chúng ta đã thành công kết nối tới EC2.
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/033-testconnect.png)

### B. Sử dụng phần mềm Bitvise SSH Client với giao diện người dùng.

{{% notice info %}}
Bitvise SSH Client sử dụng private key để xác thực kết nối vì vậy ta cần tạo một private key từ file pem mà AWS trả cho chúng ta từ bước tạo EC2 Instance.
{{% /notice %}}

1. Vào trang [PuTTYgen Website](https://www.puttygen.com/) để tải phần mềm.
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/034-testconnect.png)

2. Mở phần mềm Puttygen để bắt đầu tạo private key.
+ Click **Load**
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/035-testconnect.png)

3. Chọn **All Files**
+ Chọn file pem của EC2 Instance
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/036-testconnect.png)

4. Tại **Key passphrase** và **Confirm passphrase**, nhập mật khẩu cho private key.
+ Click **Save private key**
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/037-testconnect.png)

5. Vào trang [Download Bitvise SSH Client](https://bitvise.com/ssh-client-download) để tải phần mềm.
+ Click **Download Bitvise SSH Client**
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/038-testconnect.png)

6. Mở phần mềm **Bitvise SSH Client**
+ Tại mục Host, nhập EC2 Instance public IP: **18.132.42.239**
+ Tại mục Port, nhập port mặc định của SSH: **22**
+ Tại mục Username, nhập **ubuntu**
+ Click vào **Client key manager** để import private key.
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/039-testconnect.png)

7. Click vào **Import and select our generated private key**
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/040-testconnect.png)

8. Sau khi hoàn thành trở về màn hình chính và chọn Login.
+ Kết nối thành công tới EC2 instance.
![Test Connect](https://tamlv.buzz/aws-workshop/images/2.prerequisite/041-testconnect.png)

Như vậy EC2 Instance của chúng ta hoạt động tốt. Ta có thể đi tới bước tiếp theo.