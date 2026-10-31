---
name: spec_constitution_vi
description: Thiết lập hoặc sửa đổi hiến pháp dự án (project constitution) bắt buộc cho một kho lưu trữ phần mềm. Sử dụng khi được gọi qua /spec_constitution_vi hoặc @spec_constitution_vi cùng với mô tả dự án, tech stack, kiến trúc, quy chuẩn lập trình, bảo mật, kiểm thử, hiệu năng hoặc các ràng buộc tổ chức. Tự động chọn Khởi tạo (Initialize) hoặc Sửa đổi (Amend) dựa trên việc tệp ./spec/01.constitution.md đã tồn tại hay chưa. Tất cả nội dung hiến pháp và trao đổi phải sử dụng hoàn toàn bằng tiếng Việt.
---

# Hiến pháp Dự án (Project Constitution)

## Đầu vào và Thẩm quyền
- Nhận toàn bộ chuỗi tham số người dùng cung cấp đằng sau lệnh `/spec_constitution_vi` hoặc `@spec_constitution_vi`.
- Hoạt động tại thư mục gốc của dự án hiện tại (không phải thư mục cài đặt skill).
- Đầu ra chuẩn duy nhất là tệp `./spec/01.constitution.md`.
- Dùng công cụ tool read để đọc nội dung và tool write để ghi nội dung vào `./spec/01.constitution.md`.
- Tất cả nội dung viết trong tệp hiến pháp và các phản hồi liên quan BẮT BUỘC phải sử dụng tiếng Việt.
- Xem hướng dẫn của người dùng là chính sách được yêu cầu, hiến pháp hiện tại là cơ sở bắt buộc trong chế độ Sửa đổi (Amend), và các dữ kiện thực tế trong kho lưu trữ là bằng chứng. Không bao giờ giả định một thư viện phụ thuộc hoặc cấu hình tồn tại nếu chưa kiểm tra thực tế.

## Quy trình làm việc
1. Xác định thư mục gốc dự án bằng không gian làm việc hiện tại; kiểm tra các tệp `package.json`, lockfiles, cấu hình framework, cấu trúc mã nguồn, README, cấu hình test/lint/CI và các hướng dẫn dự án hiện có nếu có. Tránh quét các thư mục sinh tự động hoặc chứa thông tin bảo mật/bí mật. Không cài đặt thư viện phụ thuộc hay thay đổi mã nguồn ứng dụng.
2. Kiểm tra sự tồn tại của tệp `./spec/01.constitution.md` trước khi ghi bất kỳ nội dung nào. Nếu chưa có, chọn **Khởi tạo (Initialize)**; nếu đã có, chọn **Sửa đổi (Amend)**. Tệp có kích thước 0-byte hoặc bị lỗi định dạng vẫn được tính là Sửa đổi: giữ nguyên tệp và yêu cầu làm rõ nếu không thể giải thích an toàn.
3. Phân tích mô tả của người dùng thành các yêu cầu rõ ràng, khuyến nghị suy luận, các điểm chưa rõ và các xung đột. Xác minh công nghệ hiện có của dự án từ các tệp thực tế. Yêu cầu rõ ràng từ người dùng có ưu tiên cao hơn các thiết lập mặc định chung, nhưng cần chỉ ra các điểm xung đột với cấu hình hiện tại.
4. Trong chế độ **Khởi tạo**, soạn thảo một hiến pháp hoàn chỉnh, cụ thể dựa trên `CONSTITUTION-TEMPLATE`. Tạo thư mục `spec/` nếu cần thiết. Tránh đưa ra các quy tắc quá áp đặt mà không có ý định của người dùng hoặc bằng chứng từ kho lưu trữ hỗ trợ; dán nhãn rõ ràng cho các đề xuất mặc định.
5. Trong chế độ **Sửa đổi**, đọc toàn bộ hiến pháp hiện có, giữ nguyên các nguyên tắc và thứ tự đánh số không liên quan, chỉ cập nhật các điều khoản có liên quan, giải thích các xung đột và ảnh hưởng khi chuyển đổi, tuyệt đối không âm thầm hạ thấp các đảm bảo về bảo mật hoặc kiểm thử. Nếu yêu cầu mơ hồ hoặc phá vỡ một nguyên tắc cốt lõi, hãy hỏi ý kiến phê duyệt trước khi thay thế nguyên tắc đó.
6. Quản lý phiên bản theo Semantic Versioning: Khởi tạo tại 1.0.0; Sửa đổi dạng PATCH cho các giải thích làm rõ, MINOR cho các quy tắc bổ sung, MAJOR cho các thay đổi gỡ bỏ hoặc không tương thích. Ghi lại ngày cập nhật và lịch sử sửa đổi ngắn gọn; giữ nguyên ngày phê chuẩn ban đầu.
7. Kiểm tra để đảm bảo mọi quy tắc BẮT BUỘC (MUST) đều có thể kiểm thử được hoặc có tiêu chí đánh giá đo lường được; loại bỏ các yêu cầu mâu thuẫn và giả định công nghệ không căn cứ. Xác minh đường dẫn đầu ra, các tiêu đề và nội dung thực tế của tệp sau khi ghi.
8. Báo cáo chế độ đã chọn, đường dẫn tệp, phiên bản, các nguyên tắc đã thay đổi, các giả định và mọi xung đột chưa được giải quyết. Không tuyên bố thành công trừ khi tệp đã được ghi và xác minh thành công.

## Các lĩnh vực bắt buộc
Bao gồm mục đích/phạm vi dự án; nguyên tắc kiến trúc và ranh giới; tech stack và thư viện phụ thuộc; tổ chức thư mục; quy ước đặt tên và chuẩn mã nguồn; bảo mật/quyền riêng tư/quản lý bí mật; chiến lược kiểm thử và chính sách TDD; hiệu năng/khả năng truy cập (accessibility) nếu áp dụng; tiêu chuẩn chất lượng (quality gates); quy tắc hoạt động của AI Agent; quản trị và quy trình sửa đổi hiến pháp. Sử dụng ngôn ngữ rõ ràng BẮT BUỘC (MUST) / NÊN (SHOULD) / CÓ THỂ (MAY). Tùy chỉnh các phần phù hợp với người dùng và dự án thực tế.

## Yêu cầu ngôn ngữ
- Toàn bộ nội dung của hiến pháp (`./spec/01.constitution.md`) và tất cả các phản hồi, báo cáo, trao đổi liên quan đến skill này CHỈ ĐƯỢC SỬ DỤNG TIẾNG VIỆT.

## An toàn
Không bao giờ ghi đè văn bản hiện có bằng một mẫu chung trong chế độ Sửa đổi. Không truy cập vào các bí mật hoặc làm rò rỉ nội dung kho lưu trữ. Không thêm thư viện phụ thuộc, không refactor mã nguồn hoặc chỉnh sửa các tệp không liên quan. Chỉ đặt câu hỏi khi thật sự cần thiết để giải quyết mơ hồ có ảnh hưởng lớn.

## MẪU HIẾN PHÁP (CONSTITUTION-TEMPLATE)

```text

# Hiến pháp Dự án

**Phiên bản:** 1.0.0  
**Ngày phê chuẩn:** YYYY-MM-DD  
**Cập nhật lần cuối:** YYYY-MM-DD  
**Trạng thái:** Đang áp dụng

## 1. Sứ mệnh và Phạm vi
- Xác định mục tiêu sản phẩm, các nền tảng hỗ trợ và các công việc ngoài phạm vi dự án.

## 2. Nguyên tắc Kiến trúc
- Xác định kiến trúc, sự tách biệt các mối quan tâm (separation of concerns), quyền sở hữu trạng thái và ranh giới mô-đun.

## 3. Công nghệ Sử dụng (Technology Stack)
- Danh sách công cụ runtime/framework/styling/build đã được xác minh và chính sách nâng cấp.

## 4. Cấu trúc Kho lưu trữ
- Mô tả các thư mục và ranh giới sở hữu mà không tự nghĩ ra các tệp không tồn tại.

## 5. Chuẩn Mã nguồn
- Quy định cụ thể về đặt tên, kiểu dữ liệu, định dạng, xử lý lỗi và quy tắc bảo trì code.

## 6. Bảo mật và Quyền riêng tư
- Quy định về kiểm tra dữ liệu đầu vào (input validation), xác thực (nếu có), quản lý thư viện phụ thuộc và mã bí mật.

## 7. Kiểm thử và Chất lượng
- Xác định phạm vi unit/integration/e2e, kỳ vọng TDD và các bước kiểm tra bắt buộc.

## 8. Hiệu năng và Khả năng truy cập
- Thiết lập các mục tiêu phù hợp với bối cảnh và phương pháp đo lường.

## 9. Quy tắc dành cho AI Agent
- Yêu cầu đọc hiến pháp này trước khi lập kế hoạch hoặc triển khai; tuân thủ các quy ước hiện có, tránh các thay đổi không được yêu cầu và báo cáo các điểm độ lệch.

## 10. Quản trị và Sửa đổi
- Hiến pháp có hiệu lực cao hơn các sở thích triển khai thông thường, chịu sự điều chỉnh của các hướng dẫn có độ ưu tiên cao hơn. Sửa đổi phải kèm lý do được ghi nhận, đánh giá tác động, tăng phiên bản và nhật ký thay đổi.

## Lịch sử Sửa đổi
| Ngày | Phiên bản | Thay đổi | Lý do |
|---|---|---|---|
| YYYY-MM-DD | 1.0.0 | Phê chuẩn ban đầu | Khởi tạo dự án |