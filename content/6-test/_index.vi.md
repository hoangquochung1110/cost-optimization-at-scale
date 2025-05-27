---
title : "Kiểm thử giải pháp"
date : "2025-05-14" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

Chúng ta sẽ tạo một ổ cứng EBS loại gp2 để kiểm thử giải pháp


1. Lặp lại bước đăng nhập sử dụng tài khoản thành viên
    ![Member account](/images/5.conformancepack/019-memberaccount.png)

2. Truy cập dịch vụ EC2

3. Ở thanh điều hướng trái, chọn **Volume** 
    ![EC2 Console](/images/6.test/002-test.png)

4. Tạo một ổ cứng với các thuộc tính sau, chú ý chọn loại ổ cứng gp2
    ![Create EBS Volume](/images/6.test/003-test.png)

5. Sau khi tạo thành công, kiểm tra trạng thái ổ cứng rồi di chuyển đến dịch vụ AWS Config
    
    💡 Ghi chú id ổ cứng EBS để sau đó đối chiếu với kết quả đánh giá của AWS Config Conformance Pack
    ![Create EBS Volume](/images/6.test/004-test.png)

6. Chọn Conformance pack với tên `Cost-Optimization` hoặc tương tự
    ![AWS Config Conformance Pack](/images/6.test/005-test.png)

7. Chọn **View** để xem chi tiết danh mục quy tắc

    Do ổ cứng EBS được tạo vừa sử dụng loại ổ cứng gp2 đồng thời không được gán vào máy chủ EC2 nào nên có hai quy tắc được đánh giá không tuân thủ
    ![AWS Config Conformance Pack rule](/images/6.test/006-test.png)

8. Chọn quy tắc `CostOpt-Ebs-Gp3` để xem bảng điều khiển quy tắc

    Bảng điều khiển liệt kê các ổ cứng EBS vi phạm quy tắc sử dụng loại gp3, có thể thấy id trùng lắp với ổ cứng chúng ta vừa tạo ở bước trên
    ![AWS Config Conformance Pack rule](/images/6.test/007-test.png)

9. Để thực hiện hành động khắc phục, chọn nút **Remediate**

10. Đợi chốc lát và kiểm tra cột **Status** như bên dưới:
    ![AWS Config Conformance Pack rule](/images/6.test/008-test.png)

    Sau đó ổ cứng EBS trên sẽ được loại bỏ khỏi bảng điều khiển do đã đáp ứng quy tắc.

11. Kiểm tra thuộc tính của ổ cứng EBS nói trên:
    ![EBS Volume](/images/6.test/009-test.png)

