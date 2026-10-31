---
name: spec_feature_vi
description: Tạo và cập nhật đặc tả yêu cầu nghiệp vụ tiếng Việt theo đối tượng trong ./spec/features/*.md, kiểm tra trùng lặp và tổ chức vòng lặp hỏi đáp làm rõ có thể dừng/lưu tiến độ. Dùng khi người dùng muốn đặc tả What/Why, user stories, FR, AC, quy tắc và ngoại lệ; Sử dụng khi gọi @spec_feature_vi hoặc /spec_feature_vi.
---

# SPEC FEATURE VI — Đặc tả theo đối tượng nghiệp vụ

## 1. Nguyên tắc bất biến
- BẮT BUỘC dùng tiếng Việt cho hội thoại, câu hỏi, tài liệu, báo cáo; giữ nguyên định danh kỹ thuật. Chỉ đặc tả **Cái gì** và **Tại sao**; không tự chọn API, cơ sở dữ liệu, thuật toán, kiến trúc, thư viện hoặc viết mã.
- Gốc chính sách chung: `./spec/AGENT.md`. Đọc nếu có; nếu không có, báo thiếu và kiểm tra chỉ dẫn dự án khác được khai báo. Nếu có nhiều chính sách mâu thuẫn, hỏi trước khi chốt; không tự chọn nguồn ưu tiên.
- Một **yêu cầu nguyên tử** có đúng một file chủ sở hữu. Các file khác chỉ tham chiếu mã/đường dẫn, không chép nguyên yêu cầu. Một đối tượng nghiệp vụ có một tài liệu chính thức trong `./spec/features/`.
- Bỏ qua mọi `.git` ở mọi cấp, thư mục sinh tự động (`node_modules`, `dist`, `build`, `.nuxt`, `.output`...), tệp bí mật (`.env*`, khóa, chứng chỉ, token) và dữ liệu cá nhân không cần thiết. Không đọc, in hoặc đưa dữ liệu bí mật vào tài liệu.
- Không sửa mã, chính sách hoặc Skill khác.
- Không tự di chuyển/xóa tài liệu cũ.
- Không chạy script dự án không tin cậy.

## 2. Quy ước đối tượng, mã và tham chiếu
- Thư mục chuẩn: `./spec/features/`; tên file: `<doi-tuong-so-it-kebab-case>.md`, chữ thường không dấu, dạng kebab-case, số ít, ổn định theo thời gian. ví dụ `user.md`, `file.md`, `folder.md`, `permission.md`, `trash.md`. Đây là ví dụ, không phải danh sách file bắt buộc.
- Không đặt tên theo vai trò (`admin`, `viewer`), màn hình hoặc tính năng nếu đó không phải đối tượng nghiệp vụ có ranh giới độc lập.
- Chọn chủ sở hữu theo **nơi quy tắc được định nghĩa và quản trị**; trạng thái bị tác động chỉ là tín hiệu phụ. Quy tắc cấp/chia sẻ quyền → `permission.md`; vòng đời file → `file.md`. Nếu có hai chủ sở hữu hợp lý hoặc file cũ đã sở hữu quy tắc, báo xung đột và hỏi trước khi chuyển.
- Mã toàn cục ổn định: `US-OBJECT-001`, `FR-OBJECT-001`, `AC-OBJECT-001`, `SC-OBJECT-001`, `CL-OBJECT-001`, `Q-OBJECT-001`. `OBJECT` là tên đối tượng viết hoa, thay dấu `-` bằng `-` nhất quán. Mỗi mã duy nhất trong toàn bộ `spec/features`; không tái sử dụng mã đã ngừng hiệu lực.
- Giữ mã cũ (`FR-001`, v.v.) nếu đang được tham chiếu; muốn chuyển đổi phải có bảng ánh xạ và phê duyệt. Tham chiếu `./permission.md#fr-permission-001` phải khớp anchor Markdown thực tế; ưu tiên liên kết tương đối kèm mã hiển thị, kiểm tra tồn tại sau ghi.
- Mỗi US liên kết tối thiểu một FR và AC; mỗi FR cần AC có thể kiểm chứng trực tiếp hoặc qua liên kết truy vết rõ ràng. AC phải nêu điều kiện, hành động, kết quả quan sát được. SC là chỉ số thành công, không thay thế AC.

## 3. Quy trình bắt buộc mỗi lần gọi
### A. Khảo sát
1. Xác định gốc dự án và yêu cầu đầu vào; đọc `./spec/AGENT.md` nếu có, liệt kê toàn bộ `./spec/features/*.md`, đọc đầy đủ file liên quan và các tham chiếu trực tiếp. Không giả định file theo tên tính năng.
2. Lập bản đồ nội bộ đối tượng → file chủ sở hữu → US/FR/AC/SC/CL/Q → tham chiếu → quyết định đã xác nhận → câu hỏi mở. Đối chiếu ngữ nghĩa, không chỉ từ khóa.
3. Phân loại yêu cầu mới, sửa đổi, trùng, xung đột và chưa rõ. Nếu có tài liệu cũ tương đương, không tạo file cạnh tranh; đề xuất chuyển đổi và xin phép trước khi đổi tên/xóa.

### B. Phân rã
1. Xác định mục tiêu, giá trị, tác nhân, phạm vi, trạng thái nghiệp vụ, quyền, quy tắc, luồng chính, ngoại lệ, trường hợp biên và tiêu chí nghiệm thu.
2. Gán mỗi yêu cầu nguyên tử cho đúng một file; yêu cầu liên đối tượng chỉ được định nghĩa ở file sở hữu. Không nhân bản yêu cầu.
3. Giữ nguyên quyết định đã xác nhận trừ khi người dùng yêu cầu thay đổi; nếu yêu cầu mới xung đột, hỏi trước khi ghi bản chính thức.

### C. Vòng lặp làm rõ
1. Rà soát các chiều: phạm vi, chủ sở hữu, tác nhân, quyền, điều kiện, trạng thái, dữ liệu nghiệp vụ, quy tắc, lỗi, ngoại lệ, nghiệm thu, xung đột và phụ thuộc trực tiếp.
2. Phân loại: **Đã xác nhận**, **Suy ra từ nguồn đã xác nhận** (ghi nguồn), **Chưa rõ quan trọng**, **Chi tiết kỹ thuật để sau**. Một điểm là **quan trọng** nếu đáp án khác nhau làm thay đổi hành vi quan sát được, quyền, phạm vi, nghĩa vụ, kết quả nghiệm thu hoặc chủ sở hữu.
3. Nếu có điểm chưa rõ quan trọng, hỏi tối đa 3 câu/lượt. Mỗi câu có mã Q ổn định, đối tượng, nội dung, 2–4 phương án loại trừ nhau nếu phù hợp, hậu quả và lựa chọn **Khác**. Không tự chọn phương án đề xuất.
4. Dừng lượt hiện tại và chờ người dùng. Khi nhận trả lời, trước tiên kiểm tra **toàn bộ thông điệp** sau khi trim và chuyển chữ thường: `done`, `stop`, `exit`, `cancel`. Không kích hoạt nếu từ khóa chỉ nằm trong câu văn hoặc đoạn trích dài.
5. Nếu là câu trả lời nghiệp vụ, xác nhận ý nghĩa, kiểm tra xung đột, ghi quyết định vào trạng thái phiên, quét lại phụ thuộc; tiếp tục hỏi nếu còn điểm quan trọng. Không giới hạn tổng số lượt, không tự lặp trong một phản hồi.
6. Không còn điểm quan trọng → chuyển bước D. Nếu chưa thể nghiệm thu vì câu hỏi chưa giải quyết → **Chưa sẵn sàng**, tuyệt đối không tự chốt.

### D. Lệnh dừng và quyền lưu
| Lệnh | Kết thúc hỏi | Lưu quyết định chưa ghi | Lưu câu hỏi mở | Hành vi |
|---|---|---|---|---|
| `done` | Có | Có, nếu có quyền ghi và không xung đột | Có, nếu có quyền ghi | Lưu tiến độ, không coi câu chưa trả lời là đã xác nhận |
| `stop` | Có | Chỉ nếu đã được phép lưu trong phiên | Chỉ nếu đã được phép lưu trong phiên | Dừng, báo tiến độ chưa lưu |
| `exit` | Có | Như `stop` | Như `stop` | Kết thúc phiên, không tự xác nhận |
| `cancel` | Có | Không | Không | Hủy thay đổi chưa ghi; không tự hoàn tác thay đổi đã ghi |
- Nếu chưa được phép ghi, chỉ trả báo cáo/bản nháp đề xuất; không tự tạo file. `done` là yêu cầu lưu tiến độ, nhưng vẫn tuân thủ quyền truy cập và chính sách dự án.
- Khi được phép lưu, gom mọi câu chưa hỏi/chưa trả lời/trả lời chưa đủ, loại trùng, gán mã Q ổn định, ghi ở `### 8.3. Câu hỏi mở` trong từng file sở hữu. Không đưa lựa chọn chưa xác nhận vào FR/AC hoặc quyết định đã xác nhận.
- Nếu có câu hỏi chặn nghiệm thu, trạng thái file là **Bản nháp / Chưa sẵn sàng**. Nếu người dùng quay lại ở phiên sau, đọc `8.3`, quyết định CL và lịch sử từ file để khôi phục; không dựa duy nhất vào bộ nhớ hội thoại.

### E. Ghi và kiểm chứng nhiều file
1. Lập danh sách file sẽ tạo/sửa và thay đổi dự kiến; kiểm tra mã, chủ sở hữu, tham chiếu trước ghi. Chỉ ghi các file thuộc phạm vi đã được phép.
2. Đọc lại tất cả file đích trước ghi. Nếu nội dung thay đổi từ khi khảo sát, dừng phần bị ảnh hưởng và đối chiếu lại; không ghi đè.
3. Ưu tiên bản sao lưu và ghi tạm rồi thay thế nguyên tử nếu công cụ hỗ trợ. Khi cập nhật nhiều file, theo dõi kết quả từng file; nếu thất bại giữa chừng, không báo hoàn tất và cung cấp danh sách file đã/ chưa cập nhật cùng phương án phục hồi. Không giả định có giao dịch đa file.
4. Bảo toàn ngày tạo, mã, phần không liên quan, quyết định cũ, lịch sử và liên kết. Mỗi thay đổi thực chất ghi lịch sử của **chính file đó**, nêu mã, trước/sau, lý do; không thêm lịch sử cho file không đổi.
5. Đọc lại toàn bộ file đã ghi; kiểm tra mã duy nhất, liên kết/anchor tồn tại, US–FR–AC, câu hỏi mở, trạng thái, tiếng Việt và xung đột. Nếu kiểm tra thất bại, sửa an toàn hoặc báo thất bại và phạm vi ảnh hưởng.
6. Báo cáo file tạo/sửa/không ghi, mã thêm/sửa, quyết định, câu hỏi mở, lỗi còn lại và trạng thái **Sẵn sàng lập kế hoạch** hoặc **Chưa sẵn sàng**.

## 4. Mẫu tài liệu đối tượng
```markdown
# Đặc tả đối tượng: <Tên đối tượng>
**Đối tượng:** <tên chuẩn>
**Trạng thái:** Bản nháp / Đã xác nhận
**Ngày tạo:** YYYY-MM-DD
**Ngày cập nhật:** YYYY-MM-DD
**Nguồn yêu cầu:** ...

## 1. Vai trò và ranh giới
- Mục đích, thuộc phạm vi, ngoài phạm vi, tài liệu liên quan.
## 2. Câu chuyện sử dụng
### US-OBJECT-001 — <Tên>
- Với vai trò ..., tôi muốn ..., để ...
- **Liên kết:** FR-OBJECT-001; AC-OBJECT-001
## 3. Yêu cầu chức năng
- **FR-OBJECT-001:** Hệ thống BẮT BUỘC ...
  - **Nghiệm thu:** AC-OBJECT-001
## 4. Quy tắc nghiệp vụ
- ...
## 5. Ngoại lệ và trường hợp biên
- **Điều kiện:** ...; **Kết quả:** ...
## 6. Tiêu chí nghiệm thu và thành công
- **AC-OBJECT-001:** Cho trước ..., khi ..., thì ...
- **SC-OBJECT-001:** Chỉ số ..., cách đo ... (không bịa mục tiêu).
## 7. Quan hệ và phụ thuộc
- **Liên quan:** ./permission.md (FR-PERMISSION-001)
## 8. Làm rõ
### 8.1. Nguyên tắc diễn giải
- Chỉ dùng quyết định đã xác nhận.
### 8.2. Quyết định đã xác nhận
- **CL-OBJECT-001:** Câu hỏi ...; quyết định ...; nguồn xác nhận ...; ảnh hưởng FR/AC ...
### 8.3. Câu hỏi mở
- **Q-OBJECT-001:** Câu hỏi ...; liên quan ...; lý do ...; trạng thái Chưa xác nhận.
## 9. Kiểm tra nhất quán
- Chính sách đã đối chiếu: ...
- Câu hỏi chặn nghiệm thu: ...
- Mức sẵn sàng: Sẵn sàng lập kế hoạch / Chưa sẵn sàng
## 10. Lịch sử thay đổi
| Ngày | Mã | Trước → Sau | Lý do |
|---|---|---|---|
```

## 5. Điều kiện hoàn thành
- Chỉ báo **Sẵn sàng lập kế hoạch** khi mọi câu hỏi quan trọng trong phạm vi và phụ thuộc trực tiếp đã được xác nhận, AC kiểm chứng được, mọi file cần thiết đã ghi và được kiểm tra thành công.
- Không tự chuyển sang lập kế hoạch/triển khai; không tự sửa Skill khác, chính sách, file cũ hoặc xóa mã lịch sử.
