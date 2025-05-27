---
title : "Kích hoạt AWS Organizations"
date : "2025-05-14" 
weight : 1 
chapter : false
pre : " <b> 2.1.1 </b> "
---


#### Chuẩn bị IAM user
Sử dụng một IAM user và đảm bảo IAM user này có các quyền sau:

  • `organizations:CreateOrganization`

  • `organizations:DescribeOrganization`

  • `organizations:ListRoots`

Lý tưởng nhất là IAM user nên có chính sách quản trị như `AdministratorAccess`

### Kích hoạt AWS Organizations (Console)

1. Trong AWS Management Console, ở góc trên bên trái cạnh Services, nhấp vào ô tìm kiếm và nhập “AWS Organizations”, sau đó chọn dịch vụ này.

2. Nhấp vào Create Organization. Theo mặc định, tổ chức được tạo với tất cả các tính năng được kích hoạt.
    ![Create Organization](/images/2.prerequisite/001-createorganization.png)

3. Tổ chức được tạo và trang AWS accounts xuất hiện. Tài khoản duy nhất hiện có là management account của bạn, và hiện đang nằm dưới root organizational unit (OU).
