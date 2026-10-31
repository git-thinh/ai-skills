---
name: spec_specify_vi
description: Đặc tả tính năng phần mềm hoàn toàn bằng tiếng Việt. Sử dụng khi gọi /spec_specify_vi hoặc @spec_specify_vi kèm mô tả tính năng mới hoặc yêu cầu cập nhật đặc tả. Tập trung vào Cái gì (What) và Tại sao (Why), user stories, yêu cầu chức năng, tiêu chí nghiệm thu và thành công; tạo hoặc cập nhật ./spec/features/<ten-tinh-nang>.md, không quyết định công nghệ hay cách triển khai.
---

# Đặc tả tính năng — chỉ sử dụng tiếng Việt

## Quy định ngôn ngữ bắt buộc
- **BẮT BUỘC dùng tiếng Việt** trong phân tích, câu hỏi làm rõ, báo cáo, tiêu đề, bảng và nội dung đặc tả, kể cả khi đầu vào là tiếng Anh.
- Chỉ giữ nguyên định danh không nên dịch: đường dẫn, tên tệp, mã định danh, tên riêng, thuật ngữ giao tiếp kỹ thuật bắt buộc như API, và tên công nghệ được trích từ đầu vào (không đưa vào quyết định triển khai).
- Dùng **BẮT BUỘC / NÊN / CÓ THỂ** để biểu thị mức độ ràng buộc. Không dùng MUST / SHOULD / MAY trong văn bản tạo ra.
- Trước khi kết thúc, rà soát và dịch mọi câu giải thích hoặc tiêu đề tiếng Anh do kỹ năng tạo ra.

## Đầu vào và phạm vi
- Nhận nguyên văn tham số sau `/spec_specify_vi` hoặc `@spec_specify_vi`.
- BẮT BUỘC bỏ qua thư mục có tên `.git` khi tìm kiếm, quét, đọc, sao chép, thống kê hoặc xử lý tệp dự án, ở mọi cấp thư mục.
- Làm việc tại thư mục gốc dự án đang mở, không phải thư mục cài đặt kỹ năng.
- Đầu ra chuẩn: `./spec/features/<ten-tinh-nang>.md`; `<ten-tinh-nang>` là tên ngắn dạng chữ thường không dấu, nối bằng dấu gạch ngang, phản ánh mục tiêu nghiệp vụ.
- Chỉ tạo/cập nhật đặc tả hành vi mong muốn: **Cái gì** phần mềm phải làm và **Tại sao** cần làm. Không lập kế hoạch, chọn công nghệ, thiết kế API/cơ sở dữ liệu, cấu trúc mã, thuật toán hoặc viết mã ứng dụng.
- Đặc tả là đầu vào cho bước làm rõ, lập kế hoạch và triển khai tiếp theo; không tự động thực hiện các bước ấy.

## Nguyên tắc nguồn và ưu tiên
1. Nếu có `./spec/constitution.md`, BẮT BUỘC đọc và tuân thủ các nguyên tắc áp dụng. Nếu không có, báo rõ là chưa có hiến pháp; không tự tạo hoặc giả vờ đã kiểm tra.
2. Dùng mô tả của người dùng làm nguồn yêu cầu chính; dùng tài liệu dự án và hành vi hiện hữu chỉ làm ngữ cảnh kiểm chứng. Không suy đoán tính năng đã tồn tại nếu chưa đọc bằng chứng.
3. Nếu hiến pháp xung đột với yêu cầu, nêu rõ và xin quyết định; không âm thầm sửa hiến pháp.
4. Phân biệt rõ **yêu cầu được xác nhận**, **giả định hợp lý**, **đề xuất** và **vấn đề cần làm rõ**. Không biến giả định quan trọng thành sự thật.

## Quy trình thực hiện
1. Xác định thư mục gốc, mục tiêu, người dùng hưởng lợi, vấn đề cần giải quyết, giá trị mong đợi và ranh giới tính năng. Đọc có chọn lọc README, tài liệu nghiệp vụ, đặc tả liên quan và hiến pháp nếu có. Bỏ qua mọi thư mục `.git` ở mọi cấp; tránh thư mục sinh tự động và tệp bí mật.
2. Chuẩn hóa đầu vào thành phát biểu vấn đề, mục tiêu, tác nhân, luồng sử dụng, quy tắc nghiệp vụ, điều kiện ngoại lệ và kết quả đo lường. Nếu người dùng nêu công nghệ (ví dụ Redis, Nuxt, VueJs), chỉ ghi nhận nhu cầu nghiệp vụ phía sau; không đưa lựa chọn công nghệ thành yêu cầu bắt buộc.
3. Xác định tên tính năng. Trước khi ghi, kiểm tra `./spec/features/<ten-tinh-nang>.md` có tồn tại hay không. Nếu chưa có, chọn **Khởi tạo**. Nếu có, chọn **Cập nhật**, đọc toàn bộ, bảo toàn yêu cầu không liên quan, mã định danh và lịch sử khi phù hợp. Nếu có nhiều đặc tả gần trùng, không tự tạo bản trùng; hỏi người dùng chọn.
4. Chỉ hỏi các câu thực sự chặn việc viết đặc tả đúng, chẳng hạn phạm vi đối tượng, quyền truy cập hoặc quy tắc nghiệp vụ gây khác biệt lớn. Gom tối đa 3 câu hỏi ưu tiên mỗi lượt. Với chi tiết ít rủi ro, đưa giả định được đánh dấu và tiếp tục.
5. Viết tài liệu theo **SPEC-TEMPLATE** bên dưới. Mỗi câu chuyện người dùng phải có giá trị độc lập, mức ưu tiên và kịch bản kiểm thử có thể quan sát. Đặt yêu cầu chức năng dạng `FR-001`, `FR-002`...; tiêu chí nghiệm thu dạng `AC-001`...; tiêu chí thành công dạng `SC-001`...; giữ mã cũ ổn định khi cập nhật.
6. Phủ các trạng thái thông thường, rỗng, không hợp lệ, không có quyền, lỗi, trùng lặp, ngắt quãng và giới hạn dữ liệu **khi có liên quan**. Chỉ nêu yêu cầu phi chức năng theo kết quả có thể quan sát (ví dụ thời gian hoàn thành tác vụ), không áp đặt giải pháp kỹ thuật.
7. Tự kiểm tra: mỗi yêu cầu có thể kiểm chứng; tiêu chí nghiệm thu có điều kiện và kết quả rõ ràng; không có công nghệ được quyết định, không có yêu cầu mâu thuẫn, không có phạm vi không xác định bị trình bày như đã chốt; có liên kết từ mục tiêu đến user stories và tiêu chí thành công.
8. Chỉ sau kiểm tra mới tạo thư mục và ghi `<ten-tinh-nang>.md`. Đọc lại tệp đã ghi để xác minh. Nếu không có quyền ghi, cung cấp nội dung để người dùng tự lưu; không tuyên bố tạo thành công.
9. Báo cáo bằng tiếng Việt: chế độ, đường dẫn, mục tiêu, số user stories/yêu cầu/tiêu chí, giả định, câu hỏi mở, xung đột với hiến pháp và mức sẵn sàng cho bước tiếp theo.

## Quy tắc phạm vi và an toàn
- Không đọc `.env`, khóa bí mật, thông tin xác thực hoặc dữ liệu cá nhân không cần thiết; không gửi dữ liệu dự án ra dịch vụ ngoài.
- Không cài đặt gói, chạy migration, sửa mã nguồn, sửa hiến pháp hay các tệp ngoài đặc tả được yêu cầu.
- Không tự chọn Leaflet/Google Maps, Redis/SQLite, framework, giao thức, mô hình dữ liệu hoặc kiến trúc. Nếu người dùng yêu cầu rõ một giải pháp, ghi ở mục **Ràng buộc do người dùng đề xuất — cần xác nhận ở giai đoạn lập kế hoạch**, tách khỏi yêu cầu hành vi.
- Không tạo con số mục tiêu tùy tiện. Khi thiếu cơ sở đo, ghi `[CẦN XÁC NHẬN]` và nêu cách đo đề xuất.
- Không xóa yêu cầu cũ trong chế độ cập nhật mà không ghi rõ nội dung thay đổi và tác động.

## Điều kiện hoàn thành
- [ ] Nêu rõ vấn đề, giá trị, phạm vi và ngoài phạm vi.
- [ ] Có các câu chuyện người dùng ưu tiên và kiểm thử độc lập.
- [ ] Yêu cầu chức năng đánh số, không mơ hồ và không mô tả cách triển khai.
- [ ] Tiêu chí nghiệm thu và tình huống ngoại lệ kiểm chứng được.
- [ ] Tiêu chí thành công hướng đến người dùng hoặc kết quả nghiệp vụ.
- [ ] Ghi nhận giả định, phụ thuộc nghiệp vụ và câu hỏi chưa chốt.
- [ ] Không mâu thuẫn hiến pháp mà không cảnh báo.
- [ ] Đã kiểm tra tệp đầu ra sau khi ghi và toàn bộ diễn đạt bằng tiếng Việt.

## SPEC-TEMPLATE

```markdown
# ĐẶC TẢ TÍNH NĂNG: <Tên tính năng>

**Trạng thái:** Bản nháp  
**Ngày tạo:** YYYY-MM-DD  
**Ngày cập nhật:** YYYY-MM-DD  
**Nguồn yêu cầu:** <Mô tả ngắn>

## 1. Bối cảnh và vấn đề
- **Vấn đề hiện tại:** ...
- **Đối tượng chịu ảnh hưởng:** ...
- **Tại sao cần tính năng:** ...

## 2. Mục tiêu và phạm vi
### 2.1. Mục tiêu
- ...
### 2.2. Trong phạm vi
- ...
### 2.3. Ngoài phạm vi
- ...

## 3. Người dùng và các câu chuyện sử dụng
### US-001 — <Tên câu chuyện> (Ưu tiên: P1)
**Với vai trò** <đối tượng>, **tôi muốn** <khả năng>, **để** <lợi ích>.

**Kịch bản kiểm thử độc lập:** <Hành động và kết quả có thể quan sát>.

**Tiêu chí nghiệm thu:**
- **AC-001:** Cho trước <bối cảnh>, khi <hành động>, thì <kết quả>.

## 4. Yêu cầu chức năng
- **FR-001:** Hệ thống BẮT BUỘC ...

## 5. Quy tắc nghiệp vụ và dữ liệu ở mức khái niệm
- <Quy tắc, thuật ngữ và đối tượng nghiệp vụ; không thiết kế cơ sở dữ liệu>.

## 6. Trường hợp biên và ngoại lệ
- <Điều kiện> → <Hành vi mong muốn>.

## 7. Tiêu chí thành công
- **SC-001:** <Chỉ số kết quả quan sát được, mục tiêu và cách đo; nếu chưa có, ghi [CẦN XÁC NHẬN]>.

## 8. Giả định, phụ thuộc và vấn đề cần làm rõ
### 8.1. Giả định
- ...
### 8.2. Phụ thuộc nghiệp vụ
- ...
### 8.3. Câu hỏi mở
- ...
### 8.4. Ràng buộc giải pháp do người dùng đề xuất (nếu có)
- <Chưa quyết định trong giai đoạn đặc tả>.

## 9. Kiểm tra tính nhất quán và mức sẵn sàng
- **Đối chiếu hiến pháp:** ...
- **Yêu cầu chưa thể nghiệm thu:** ...
- **Mức sẵn sàng:** Sẵn sàng làm rõ / Cần bổ sung thông tin / Sẵn sàng lập kế hoạch.

## 10. Lịch sử thay đổi
| Ngày | Thay đổi | Lý do |
|---|---|---|
| YYYY-MM-DD | Khởi tạo đặc tả | Yêu cầu tính năng mới |
```
