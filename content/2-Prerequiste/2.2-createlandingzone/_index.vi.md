---
title : "Thiết lập Landing Zone"
date : "2025-05-14" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Thiết lập Landing Zone

1. Truy cập giao diện quản trị dịch vụ [AWS Control Tower](https://console.aws.amazon.com/controltower/home/landing#):
  
    - Chọn **Set up landing zone**.
  
    - Mất khoảng 15 phút để AWS Control Tower hoàn tất quá trình thiết lập
  
    - Sau khi hoàn tất, về cơ bản, Control Tower sẽ tự động tạo hai tài khoản thành viên bắt
buộc: tài khoản Audit (Kiểm toán) và  tài khoản Log Archive (Lưu trữ nhật  ký) cũng như thiết lập cấu trúc Organizational Units (OU) cơ bản: Security OU (chứa tài khoản Audit và Log Archive), Sandbox OU (để thử nghiệm) và Root OU (chứa management account)

![Landing Zone](/images/2.prerequisite/002-landingzone.png)

2. Kiểm tra cấu trúc Organizational Units (OUs)
    - Truy cập phần "Organization" trong Control Tower

    - Xác nhận các OU cơ bản đã được tạo:
  
        • Security OU (chứa các tài khoản Audit và Log Archive)
        • Sandbox OU (dành cho môi trường thử nghiệm)
        • Root OU (chứa Management account)
  
    - Kiểm tra các OU bổ sung nếu bạn đã cấu hình thêm

3. Xác minh các tài khoản cốt lõi

    - Trong phần "Organization", kiểm tra các tài khoản đã được tạo:
    
        • Management account (tài khoản gốc của bạn)

        • Audit account (tài khoản kiểm toán)
        
        • Log Archive account (tài khoản lưu trữ nhật ký)

    - Xác nhận các tài khoản này đã được phân bổ vào đúng OU

![Landing Zone](/images/2.prerequisite/003-landingzone.png)

💡 Trong quá trình thiết lập Landing Zone, AWS Control Tower sẽ tự động cài đặt cấu hình dịch vụ AWS Config cho các tài khoản thành viên (phương thức ghi chép, kênh phân phối). Đối với tài khoản kiểm toán, Control Tower sẽ cài đặt AWS Config Aggregator, một lọại tài nguyên giúp giám sát tập trung các quy tắc tuân thủ của các tài nguyên trên toàn tổ chức

📌 Sơ đồ minh họa AWS Control Tower tự động thiết lập và quản trị môi trường đa tài khoản với nền tảng quản trị, bảo mật chuẩn hóa và cấp phát tài khoản thông qua tài khoản quản lý trung tâm.

![Landing Zone](/images/2.prerequisite/004-landingzone.png)
