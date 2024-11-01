---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
**CI (Continuous Integration):** CI là phương thức được sử dụng để tự động quá quy trình build và test của ứng dụng. CD kiểm tra liên tục các thay đổi trong repository và khởi động quá trình build, test. Điều này có nghĩa là mã nguồn của chúng ta liên tục được tích hợp. Quy trình CI đảm bảo rằng mã nguồn mới được liên tục build và test mà không cần thêm các bước sau khi commit. Với việc thường xuyên cập nhật và tích hợp mã nguồn mới, chúng ta giảm thiểu tối đa rủi ro về xung đột mã nguồn giữa các thành viên trong cùng một dự án.

**CD (Continuous Delivery):** CD là một hoạt động kết hợp cùng với CD tạo thành 1 quy trình tự động triển khai mã nguồn tới môi trường staging hoặc testing mà không cần sự can thiệp của con người.

**CI/CD** kết hợp các bước của CI & CD để tạo nên một quy trình triển khai phần mềm được tối ưu hóa.
Với việc cài đặt CI/CD, ứng dụng sẽ có được những ưu điểm sau:
1. Cho phép lập trình viên commit các thay đổi nhỏ thường xuyên hơn thay vì phải gom thành 1 đợt release đủ lớn.
2. Việc tự động, liên tục build mã nguồn đảm bảo rằng codebase luôn ổn định và xác định sớm mọi vấn đề tiềm ẩn.
3. Khi có một vấn đề nào đó được phát hiện trong quá trình CI/CD, logs và build flow được cung cấp một cách chi tiết, đẩy đủ, trực quan để giúp việc sửa lỗi dễ dàng và nhanh gọn hơn.

Với những ưu điểm trên, chúng ta hoàn toàn nên cân nhắc về việc triển khai CI/CD cho ứng dụng để tiết kiệm thời gian và công sức phát triển.

![ConnectPrivate](https://tamlv.buzz/aws-workshop/images/cicd_flow.png) 