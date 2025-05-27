---
title : "Kích hoạt tài khoản 'Quản trị viên được ủy quyền'"
date : "2025-05-14" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---


Ở bước này, chúng ta chỉ định một tài khoản thành viên (không phải tài khoản quản lý) thực hiện các tác vụ quản trị cụ thể cho các dịch vụ AWS cụ thể trên toàn tổ chức của bạn

{{% notice info %}}
Tài khoản quản lý nên chỉ dùng cho các tác vụ quản lý organization
{{% /notice %}}

Trong phần này chúng ta sẽ tiến hành tạo S3 bucket và thực hiện cấu hình lưu trữ các session logs để xem được chi tiết các câu lệnh được sử dụng trong session.

### Ý nghĩa

- Phân chia nhiệm vụ - Trách nhiệm quản trị có thể được phân phối cho
các nhóm chuyên biệt sử dụng các tài khoản thành viên chuyên dụng
- Giảm quyền truy cập tài khoản quản lý - Ít người cần truy cập vào
tài khoản quản lý, cải thiện bảo mật
- Quản trị chuyên biệt - Các nhóm có chuyên môn về các dịch vụ cụ thể có thể
quản lý các dịch vụ đó trên toàn tổ chức
- Hiệu quả hoạt động - Quản trị viên dịch vụ có thể làm việc trực tiếp từ
tài khoản được chỉ định mà không cần chuyển sang tài khoản quản lý
- Yêu cầu tuân thủ - Giúp đáp ứng các yêu cầu tuân thủ đòi hỏi
phân chia nhiệm vụ


### Nội dung:

  - [Cài đặt tài khoản Quản trị được uỷ quyền cho AWS Config](./4.1-delegated-admin-account-for-aws-config/)
  - [Cài đặt tài khoản Quản trị được uỷ quyền cho AWS CloudFormation](./4.2-delegated-admin-account-for-aws-cloudformation/)
  - [Tạo các vai trò IAM cần thiết](./4.3-createrole/)
