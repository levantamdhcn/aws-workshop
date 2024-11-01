---
title : "Tạo Public Subnet"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.4.2 </b> "
---

#### Tạo Public Subnet

1. Chọn vào trang **Subnets**.
  + Chọn **Create subnet**.

![VPC](/images/2.prerequisite/003-createsubnet.png)

2. Tại trang **Create subnet**.
  + Tại mục **VPC ID** section, chọn **ASG**.
  + Tại mục **Subnet name**, nhập **Public Subnet**.
  + Tại phần **Availability Zone**, chọn AZ đầu tiên.
  + Tại mục **IPv4 CIRD block** nhập **10.10.1.0/24**.

![VPC](/images/2.prerequisite/004-createsubnet.png)

3. Kéo xuống dưới cùng trang và click **Create subnet**.

4. Click vào **Public Subnet** vừa tạo.
  + Click **Actions**.
  + Click **Edit subnet settings**.

![VPC](/images/2.prerequisite/005-createsubnet.png)

5. Click **Enable auto-assign public IPv4 address**.
  + Click **Save**.

![VPC](/images/2.prerequisite/006-createsubnet.png)

6. Click **Internet Gateways**.
  + Click **Create internet gateway**.
  
![VPC](/images/2.prerequisite/007-createigw.png)

7. Tại trang **Create internet gateway**.
  + Ở mục **Name tag** nhập **IGW**.
  + Click **Create internet gateway**.
  
![VPC](/images/2.prerequisite/008-createigw.png)

8. Sau khi tạo thành công, click vào **Actions**.
  + Click **Attach to VPC**.
 
![VPC](/images/2.prerequisite/009-createigw.png)

9. Ở trang **Attach to VPC**.
  + Ở phần **Available VPCs**, chọn **ASG**.
  + Click **Attach internet gateway**.
  + Kiểm tra trạng thái đến khi hiện như hình sau.

![VPC](/images/2.prerequisite/010-createigw.png)

10. Tiếp theo ta cần tạo 1 Route Table cho Subnet vừa tạo.
  + Click **Route Tables**.
  + Click **Create route table**.

![VPC](/images/2.prerequisite/011-creatertb.png)

11. Tại trang **Create route table**.
  + Ở mục **Name**, nhập **Public Route Table**.
  + Ở phần **VPC** chọn **VPC**.
  + Click **Create route table**.

![VPC](/images/2.prerequisite/012-creatertb.png)

12. Sau khi đã tạo thành công Route Table, ta cần cài đặt routes.
  + Click **Edit routes**.
  
![VPC](/images/2.prerequisite/013-creatertb.png)

13. Tại trang **Edit routes**.
  + Click **Add route**.
  + Ở mục **Destination** ta nhập 0.0.0.0/0
  + Ở mục **Target**, chọn **Internet Gateway** sau đó chọn **IGW**.
  + Click **Save changes**.

![VPC](/images/2.prerequisite/014-creatertb.png)
![VPC](/images/2.prerequisite/015-creatertb.png)

14. Chọn tab **Subnet associations**.
  + Click **Edit subnet associations** để gắn Route Table ta vừa tạo trong **Public Subnet**.

![VPC](/images/2.prerequisite/016-creatertb.png)

15. Tại tab **Edit subnet associations**.
  + Click vào **Public Subnet**.
  + Click **Save associations**.

![VPC](/images/2.prerequisite/017-creatertb.png)

16. Kiểm tra lại các thông tin và trạng thái của các thành phần ta vừa tạo.

![VPC](/images/2.prerequisite/018-creatertb.png)