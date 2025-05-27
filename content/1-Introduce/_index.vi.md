---
title : "Giới thiệu"
date : "2025-05-14" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Tổng quan

**AWS Config** là dịch vụ liên tục đánh giá, kiểm tra và phân tích cấu hình cùng mối quan hệ giữa các tài nguyên trên AWS, on-premises và các đám mây khác. Bài viết này hướng dẫn cách tăng cường giá trị của AWS Config thông qua việc triển khai giải pháp toàn tổ chức, tự động đánh giá tài nguyên theo các thực hành tốt nhất cho tối ưu chi phí sử dụng tính năng Conformance Packs.

**Conformance Pack** là tập hợp các quy tắc AWS Config và hành động khắc phục, cung cấp khung tuân thủ tổng quát để mã hóa và triển khai các kiểm tra quản trị về bảo mật, vận hành hoặc tối ưu chi phí trong một tài khoản và vùng, hoặc mở rộng ra toàn bộ AWS Organization. Các quy tắc này tự động giám sát và đánh giá tài nguyên để xác định tình trạng tuân thủ so với logic được định nghĩa trong mỗi quy tắc. AWS Config cung cấp AWS Config Managed Rules (danh sách quy tắc được định nghĩa sẵn có thể tùy chỉnh) hoặc AWS Config Custom Rules (cho phép định nghĩa logic tùy chỉnh sử dụng các hàm **AWS Lambda** hoặc AWS CloudFormation Guard - một ngôn ngữ chính sách dưới dạng mã).
Khi tài nguyên không tuân thủ logic được định nghĩa trong quy tắc, nó sẽ được đánh dấu **Noncompliant**. Bạn có thể chọn thực hiện các bước khắc phục theo cách thủ công hoặc tự động thông qua **AWS Systems Manager** Automation - dịch vụ cung cấp trung tâm vận hành cho các ứng dụng và tài nguyên AWS, với các runbook được định nghĩa sẵn để tự động khắc phục tài nguyên không tuân thủ hoặc kích hoạt quy trình làm việc điều khiển bằng sự kiện như cảnh báo đội ngũ để hành động.

#### Tổng quan giải pháp

Giải pháp này cho phép các tổ chức đã sử dụng AWS Config tối đa hóa lợi ích sử dụng bằng cách tích hợp quản trị tối ưu chi phí tự động vào hạ tầng hiện có. Giải pháp linh hoạt này cung cấp ba quy tắc tùy chỉnh mẫu thể hiện các thực hành tốt nhất về tối ưu chi phí, liên tục giám sát cấu hình tài nguyên và báo cáo tình trạng tuân thủ về bộ tổng hợp AWS Config tập trung trong tài khoản 'quản trị viên được ủy quyền' để giám sát và báo cáo được đơn giản hóa.

![Architecture Overview](images/5.conformancepack/007-architecture-overview.png)

Việc triển khai bao gồm các quy tắc quản trị sau:

- **Quy tắc 1**: Xác định các EBS gp2 volumes Khắc phục: Tự động chuyển đổi sang gp3 volumes
- **Quy tắc 2**: Phát hiện các EBS volumes chưa gắn vào EC2 instances
- **Quy tắc 3**: Tìm các S3 buckets thiếu chính sách cấu hình vòng đời

Khi tài nguyên không đáp ứng tiêu chí quy tắc, cả tài nguyên riêng lẻ và quy tắc cấu hình cùng conformance pack liên quan đều nhận trạng thái Noncompliant. Quy tắc 1 tích hợp khả năng khắc phục tự động có thể thực thi theo yêu cầu hoặc tự động, khởi chạy runbook tự động hóa SSM để di chuyển EBS volumes từ gp2 sang gp3. Việc nâng cấp này cho phép cung cấp IOPS và throughput độc lập mà không cần mở rộng lưu trữ, mang lại mức giảm chi phí lên đến 20% mỗi GB so với gp2 volumes.

{{% notice info %}}
Quan trọng: AWS Config hoạt động như dịch vụ tính phí - xem lại tài liệu giá cả để hiểu tác động chi phí tổ chức trước khi triển khai rộng rãi nếu chưa triển khai hiện tại.
{{% /notice %}}

Giải pháp hỗ trợ triển khai trên AWS Organizations bất kể trạng thái AWS Control Tower. AWS Control Tower cung cấp thiết lập có tổ chức và quản trị cho môi trường AWS đa tài khoản sử dụng các thực hành tốt nhất đã được thiết lập. Hình 1 minh họa việc triển khai Cost Optimization Conformance Pack trên kiến trúc OU mẫu điển hình của triển khai AWS Control Tower với các tài khoản thành viên.
Security OU lưu trữ tài khoản kiểm toán, được chỉ định làm quản trị viên được ủy quyền cho cả AWS Config và AWS CloudFormation. Việc chỉ định này cung cấp quyền cần thiết để triển khai Cost Optimization Conformance Pack cùng các tài nguyên liên quan thông qua phân phối CloudFormation Stack trên các tài khoản trong tổ chức.
CloudFormation Stack bao gồm các quy tắc tùy chỉnh Cost Optimization Conformance Pack cùng với hàm AWS Lambda và tài liệu AWS Systems Manager được tham chiếu bởi các quy tắc này. Hai vai trò AWS Identity and Access Management (IAM) tùy chỉnh được cung cấp thông qua CloudFormation StackSets để cho phép thực thi hàm Lambda và tài liệu Systems Manager. Tất cả thành phần triển khai toàn tổ chức từ tài khoản kiểm toán tập trung, đơn giản hóa việc quản lý giải pháp.

AWS Config đánh giá sự tuân thủ tài nguyên với các quy tắc conformance pack theo định kỳ hoặc được kích hoạt bởi thay đổi cấu hình môi trường. Bộ tổng hợp AWS Config trong tài khoản kiểm toán tổng hợp và tập trung dữ liệu tuân thủ được thu thập trên các tài khoản thành viên, tạo điều kiện thuận lợi cho phân tích và báo cáo theo vùng.
