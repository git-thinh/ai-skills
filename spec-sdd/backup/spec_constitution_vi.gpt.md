---
name: spec_constitution_vi
description: Thiết lập hoặc sửa đổi hiến pháp ràng buộc của dự án phần mềm hoàn toàn bằng tiếng Việt. Sử dụng khi gọi /spec_constitution_vi hoặc @spec_constitution_vi kèm mô tả dự án, công nghệ, kiến trúc, quy chuẩn mã nguồn, bảo mật, kiểm thử, hiệu năng hoặc các ràng buộc tổ chức. Tự động chọn chế độ Khởi tạo hoặc Sửa đổi dựa trên sự tồn tại của ./spec/01.constitution.md.
---

# Hiến pháp dự án — chỉ sử dụng tiếng Việt

## Quy định ngôn ngữ bắt buộc
- **BẮT BUỘC sử dụng tiếng Việt** trong toàn bộ quá trình phân tích, câu hỏi làm rõ, phản hồi, báo cáo, tiêu đề, bảng, lịch sử thay đổi và nội dung hiến pháp tạo mới hoặc sửa đổi.
- Không viết lời giải thích, tiêu đề hay đoạn văn bằng tiếng Anh, kể cả khi yêu cầu đầu vào viết bằng tiếng Anh. Diễn giải yêu cầu đó sang tiếng Việt trước khi đưa vào hiến pháp.
- Chỉ giữ nguyên các định danh kỹ thuật không nên dịch: tên công nghệ và thư viện (Nuxt, Tailwind CSS, TypeScript), tên tệp, đường dẫn, câu lệnh, cú pháp, mã nguồn, tên API, khóa cấu hình và các thuật ngữ bắt buộc để tương thích kỹ thuật.
- Khi sửa đổi tài liệu cũ có nội dung tiếng Anh, chuyển phần văn bản được chỉnh sửa và các phần tiếng Anh còn lại sang tiếng Việt nhưng giữ nguyên ý nghĩa, mức độ ràng buộc và các quy tắc đang có. Nếu việc dịch có thể làm thay đổi ý nghĩa pháp quy, yêu cầu xác nhận.
- Diễn đạt mức độ ràng buộc bằng **BẮT BUỘC / NÊN / CÓ THỂ**, không dùng MUST / SHOULD / MAY trong nội dung tài liệu.
- Trước khi kết thúc, rà soát để bảo đảm không còn tiêu đề hoặc câu giải thích tiếng Anh do kỹ năng tạo ra.

## Đầu vào và phạm vi
- Nhận nguyên văn tham số sau `/spec_constitution_vi` hoặc `@spec_constitution_vi`.
- Thực hiện trong thư mục gốc của dự án đang mở, không phải thư mục cài đặt kỹ năng.
- Đường dẫn đầu ra chuẩn duy nhất: `./spec/01.constitution.md`.
- Dùng công cụ tool read để đọc nội dung và tool write để ghi nội dung vào `./spec/01.constitution.md`.
- Xem yêu cầu người dùng là đề xuất chính sách, hiến pháp hiện có là nền tảng bắt buộc khi sửa đổi và tệp dự án là bằng chứng. Không khẳng định công nghệ hoặc cấu hình đã có nếu chưa kiểm tra. 

## Quy trình
1. Xác định thư mục gốc dự án. Kiểm tra có chọn lọc `package.json`, tệp khóa, cấu hình framework, bố cục mã nguồn, README, kiểm thử, lint, CI và chỉ dẫn dự án hiện có. Không đọc bí mật hoặc quét thư mục sinh tự động. Không cài gói hay chỉnh sửa mã ứng dụng.
2. **Trước khi ghi bất kỳ nội dung nào**, kiểm tra sự tồn tại của `./spec/01.constitution.md`. Nếu chưa có, chọn **Khởi tạo**; nếu đã có, chọn **Sửa đổi**. Tệp rỗng hoặc lỗi định dạng vẫn được xem là đã tồn tại: bảo toàn nội dung và hỏi làm rõ nếu không thể diễn giải an toàn.
3. Phân loại đầu vào thành yêu cầu rõ ràng, đề xuất suy luận, thông tin chưa biết và mâu thuẫn. Đối chiếu công nghệ với tệp dự án. Ưu tiên yêu cầu cụ thể của người dùng hơn mặc định chung nhưng phải chỉ ra xung đột với cấu hình hiện tại.
4. **Khởi tạo:** Tạo bản hiến pháp đầy đủ theo mẫu hiến pháp `CONSTITUTION-TEMPLATE` tạo thư mục `spec/` nếu chưa có. Không tự áp đặt quy tắc quá chi tiết khi thiếu căn cứ; ghi rõ những nội dung chỉ là đề xuất.
5. **Sửa đổi:** Đọc toàn bộ hiến pháp hiện tại, giữ các nguyên tắc không liên quan và thứ tự đánh số; chỉ cập nhật các điều khoản cần thiết, nêu xung đột và tác động chuyển đổi. Không âm thầm hạ thấp tiêu chuẩn bảo mật hoặc kiểm thử. Nếu yêu cầu mơ hồ hoặc làm thay đổi nguyên tắc nền tảng, xin xác nhận trước khi thay thế.
6. Quản lý phiên bản theo quy tắc ba số: khởi tạo `1.0.0`; sửa lỗi diễn đạt tăng số cuối; bổ sung quy tắc tương thích tăng số giữa; xóa hoặc thay đổi không tương thích tăng số đầu. Ghi ngày sửa đổi và lịch sử thay đổi ngắn gọn; giữ nguyên ngày thông qua lần đầu.
7. Đảm bảo mỗi quy tắc **BẮT BUỘC** có cách kiểm chứng hoặc tiêu chí đánh giá cụ thể. Loại bỏ mâu thuẫn, giả định công nghệ không có căn cứ. Kiểm tra lại đường dẫn, đề mục và nội dung thực tế sau khi ghi.
8. Báo cáo bằng tiếng Việt: chế độ đã chọn, đường dẫn, phiên bản, các nguyên tắc đã thay đổi, giả định và xung đột chưa giải quyết. Không thông báo thành công nếu chưa ghi và xác minh tệp.

## Các lĩnh vực bắt buộc
Bao gồm mục tiêu và phạm vi; kiến trúc và ranh giới mô-đun; công nghệ và phụ thuộc; tổ chức thư mục; quy tắc đặt tên và mã nguồn; bảo mật, quyền riêng tư và bí mật; chiến lược kiểm thử và TDD; hiệu năng và khả năng tiếp cận khi phù hợp; cổng kiểm soát chất lượng; quy tắc cho tác nhân AI; quản trị và thủ tục sửa đổi. Điều chỉnh theo yêu cầu người dùng và bằng chứng từ dự án.

## An toàn
- Không ghi đè hiến pháp cũ bằng mẫu chung trong chế độ Sửa đổi.
- Không truy cập bí mật hoặc chuyển dữ liệu dự án ra ngoài.
- Không thêm phụ thuộc, tái cấu trúc mã nguồn hoặc thay đổi tệp không liên quan.
- Chỉ hỏi khi cần giải quyết sự mơ hồ có ảnh hưởng lớn.
- Nếu thiếu quyền ghi tệp, cung cấp nội dung tiếng Việt để người dùng tự lưu; không tuyên bố đã tạo tệp.

## CONSTITUTION-TEMPLATE
- Mẫu hiến pháp dự án: Sử dụng mẫu này khi khởi tạo; thay phần hướng dẫn bằng quy tắc cụ thể có căn cứ. Toàn bộ nội dung phải bằng tiếng Việt, ngoại trừ định danh kỹ thuật không thể dịch.

```text
# HIẾN PHÁP DỰ ÁN

**Phiên bản:** 1.0.0  
**Ngày thông qua:** YYYY-MM-DD  
**Ngày sửa đổi gần nhất:** YYYY-MM-DD  
**Trạng thái:** Có hiệu lực

## 1. Sứ mệnh và phạm vi
- Xác định mục tiêu sản phẩm, nền tảng hỗ trợ và những công việc ngoài phạm vi.

## 2. Nguyên tắc kiến trúc
- Xác định kiến trúc, phân tách trách nhiệm, quyền sở hữu trạng thái và ranh giới mô-đun.

## 3. Nền tảng công nghệ
- Liệt kê môi trường chạy, framework, công cụ giao diện, công cụ xây dựng đã được kiểm chứng và chính sách nâng cấp.

## 4. Cấu trúc kho mã nguồn
- Mô tả các thư mục và ranh giới trách nhiệm; không bịa ra tệp hoặc thư mục chưa có.

## 5. Quy chuẩn mã nguồn
- Quy định cách đặt tên, kiểu dữ liệu, định dạng, xử lý lỗi và khả năng bảo trì.

## 6. Bảo mật và quyền riêng tư
- Quy định kiểm tra dữ liệu đầu vào, xác thực khi phù hợp, quản lý phụ thuộc và thông tin bí mật.

## 7. Kiểm thử và chất lượng
- Xác định phạm vi kiểm thử đơn vị, tích hợp, đầu cuối; chính sách TDD và các bước kiểm tra bắt buộc.

## 8. Hiệu năng và khả năng tiếp cận
- Đặt mục tiêu phù hợp ngữ cảnh và phương pháp đo lường.

## 9. Quy tắc dành cho tác nhân AI
- BẮT BUỘC đọc hiến pháp trước khi lập kế hoạch hoặc triển khai; tuân thủ quy ước hiện có, không thay đổi ngoài yêu cầu và báo cáo sai lệch.
- BẮT BUỘC dùng tiếng Việt trong tài liệu hiến pháp, báo cáo và giải thích; giữ nguyên định danh kỹ thuật cần thiết.

## 10. Quản trị
- Hiến pháp được ưu tiên hơn lựa chọn triển khai thông thường, nhưng không vượt chỉ dẫn có độ ưu tiên cao hơn.
- Mọi sửa đổi BẮT BUỘC có lý do, đánh giá tác động, tăng phiên bản và ghi lịch sử.

## Lịch sử sửa đổi
| Ngày | Phiên bản | Thay đổi | Lý do |
|---|---|---|---|
| YYYY-MM-DD | 1.0.0 | Thông qua lần đầu | Khởi tạo dự án |

```