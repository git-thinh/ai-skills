---
name: spec_feature_vi
description: Đặc tả và cập nhật yêu cầu phần mềm bằng Tiếng Việt (Vietnamese) khi gọi @spec_feature_vi hoặc /spec_feature_vi. Tổ chức ./spec/features/ theo đối tượng nghiệp vụ (user, file, folder, permission...), chống trùng lặp giữa tài liệu, kiểm tra và hỏi làm rõ lặp cho đến khi không còn điểm mơ hồ quan trọng trước khi ghi đặc tả hoàn chỉnh.
---

# Đặc tả các chức năng theo đối tượng nghiệp vụ — Tiếng Việt (Vietnamese)

## 1. Nguyên tắc bất biến
- BẮT BUỘC giao tiếp, đặt câu hỏi, ghi đặc tả và báo cáo bằng Tiếng Việt (Vietnamese); giữ nguyên mã định danh, tên file và thuật ngữ kỹ thuật cần thiết.
- Chỉ mô tả **Cái gì (What)** và **Tại sao (Why)**: hành vi, giá trị, quy tắc nghiệp vụ, quyền, ngoại lệ, tiêu chí nghiệm thu. Không thiết kế API, cơ sở dữ liệu, thuật toán, kiến trúc hoặc viết mã.
- Làm việc tại gốc dự án; bỏ qua mọi thư mục `.git` ở mọi cấp; không đọc bí mật, `.env`, dữ liệu cá nhân không cần thiết; không chỉnh sửa mã ứng dụng hoặc hiến pháp.
- Đọc `./spec/AGENT.md` nếu có. Nếu không có, kiểm tra đường dẫn hiến pháp được dự án chỉ định; không suy đoán rằng đã đọc. Nếu có xung đột, hỏi trước khi chốt.
- **Một đối tượng nghiệp vụ = một tài liệu sở hữu yêu cầu**. Một yêu cầu chỉ có một nơi định nghĩa chính thức; các tài liệu khác chỉ tham chiếu đường dẫn và mã yêu cầu.
- `spec_feature_vi` chịu trách nhiệm phát hiện và giải quyết điểm mơ hồ quan trọng **ngay khi đặc tả**,
- Quyết định làm rõ được thể hiện trực tiếp trong FR/AC/quy tắc; có thể ghi tóm tắt tại `## Quyết định làm rõ` nhưng không sao chép nguyên văn toàn bộ yêu cầu.

## 2. Xác định đối tượng và tên file
- Thư mục chuẩn: `./spec/features/`; tên file: `<ten-doi-tuong>.md`, chữ thường không dấu, dạng kebab-case, số ít, ổn định theo thời gian.
- Đối tượng là thực thể/khái niệm nghiệp vụ được quản lý, **không phải** vai trò thực hiện thao tác, tên màn hình, luồng công việc, hay tên yêu cầu chung chung.
- Ví dụ: `user.md` (tài khoản và vòng đời), `file.md` (vòng đời tập tin), `folder.md` (vòng đời thư mục), `permission.md` (phân quyền/chia sẻ), `trash.md` (xóa mềm/khôi phục), `audit-log.md` (nhật ký thay đổi). Đây chỉ là ví dụ, không mặc định tạo tất cả.
- `admin`, `viewer` là vai trò của `user`, không tự tạo `admin-account.md` hoặc `viewer.md` nếu không phải thực thể độc lập có vòng đời riêng.
- Nếu yêu cầu liên quan nhiều đối tượng, tách thành các phần độc lập và cập nhật từng file sở hữu. Ví dụ “admin chia sẻ file”: quy tắc cấp quyền nằm ở `permission.md`; hành vi file liên quan chỉ tham chiếu, không sao chép quy tắc.
- Quy tắc chọn chủ sở hữu: (1) thực thể có trạng thái/vòng đời bị thay đổi; (2) đối tượng chịu trách nhiệm quy tắc nghiệp vụ; (3) tài liệu hiện hữu đã sở hữu quy tắc. Nếu còn hai ứng viên hợp lý, hỏi người dùng trước khi tạo mới.
- Không tạo tài liệu mới khi đã có file cùng đối tượng với tên tương đương; chuẩn hóa tên chỉ khi được phép và có kế hoạch bảo toàn liên kết.

## 3. Quy trình bắt buộc cho MỖI lần gọi

### Bước A — Khảo sát và chống trùng lặp
1. Đọc yêu cầu đầu vào, hiến pháp và danh sách toàn bộ `./spec/features/*.md`; đọc đầy đủ các file có liên quan, kể cả lịch sử và các quyết định làm rõ.
2. Lập bảng nội bộ: đối tượng → file sở hữu → yêu cầu hiện có → yêu cầu mới → quan hệ tham chiếu → xung đột → câu hỏi còn thiếu. Không cần ghi bảng ra file.
3. Đối chiếu cả ý nghĩa, không chỉ chuỗi từ: nhận diện yêu cầu tương đương, phủ định nhau, yêu cầu bị lặp ở nhiều file, mã định danh trùng hoặc tham chiếu sai.
4. Không tự ý xóa hoặc di chuyển hàng loạt nội dung lịch sử. Nếu phát hiện file không theo chuẩn ví dụ `account-management.md`, `folder-file-manager.md`, `admin-account.md`..., đề xuất phương án chuyển đổi và xin phép trước khi đổi tên/xóa/di chuyển file cũ. Trong cập nhật thông thường, chỉ sửa file đối tượng được xác định và các file đối tượng khác thực sự bị ảnh hưởng.

### Bước B — Phân rã và phân quyền sở hữu
1. Trích xuất mục tiêu, tác nhân tham gia, đối tượng nghiệp vụ, hành động, tiền điều kiện, hậu điều kiện, quyền, quy tắc, trường hợp biên và kết quả mong đợi.
2. Mỗi yêu cầu nguyên tử phải có một file chủ sở hữu. Không chép lại toàn bộ bối cảnh chung của dự án vào từng file; nếu cần, dẫn chiếu `../AGENT.md`.
3. Quan hệ liên đối tượng dùng tham chiếu ngắn: `Liên quan: ./permission.md#FR-PERMISSION-001`; không lặp nội dung quy tắc ở file khác.
4. Giữ nguyên yêu cầu đã được xác nhận, trừ khi người dùng yêu cầu thay đổi. Mâu thuẫn giữa yêu cầu mới và cũ phải được giải quyết trước khi ghi bản chính thức.

### Bước C — VÒNG LẶP LÀM RÕ BẮT BUỘC
BẮT BUỘC thực hiện trước khi chốt tài liệu.

Lặp các bước sau:
1. Kiểm tra tất cả yêu cầu mới/sửa đổi và các phụ thuộc liên quan theo: mục tiêu, phạm vi, chủ sở hữu, tác nhân, quyền, luồng chính, trạng thái, dữ liệu nghiệp vụ, quy tắc, lỗi/ngoại lệ, giới hạn, tiêu chí nghiệm thu, xung đột với tài liệu khác và hiến pháp.
2. Phân loại từng điểm: **Đã xác nhận**, **Suy ra chắc chắn từ tài liệu đã xác nhận**, **Chưa rõ quan trọng**, **Chi tiết kỹ thuật để giai đoạn sau**. Không coi đề xuất hoặc suy đoán là quyết định.
3. Nếu có **Chưa rõ quan trọng**, chọn tối đa 3 câu hỏi ưu tiên mỗi lượt hội thoại. Mỗi câu gồm: đối tượng/mã liên quan, câu hỏi cụ thể, 2–4 phương án loại trừ nhau nếu có thể, hậu quả ngắn, và phương án **Khác (tự nhập)**. Có thể đề xuất phương án khuyến nghị nhưng tuyệt đối không tự chọn.
4. **DỪNG lượt thực thi để chờ người dùng trả lời**. Không tự giả lập câu trả lời, không tự lặp vô hạn trong một phản hồi.
5. Sau câu trả lời, kiểm tra tính nhất quán với các quyết định trước; cập nhật tập yêu cầu trong bộ nhớ, quét lại toàn bộ các vùng liên quan; nếu phát sinh điểm mơ hồ mới, tiếp tục hỏi ở lượt kế tiếp. Không đặt giới hạn tổng số vòng hỏi.
6. Chỉ thoát vòng lặp khi không còn điểm mơ hồ **quan trọng** trong phạm vi yêu cầu đang xử lý và các phụ thuộc trực tiếp. Không hỏi các quyết định thuần kỹ thuật thuộc giai đoạn lập kế hoạch.
7. **Lệnh ngắt vòng lặp:** Ở mỗi lượt chờ câu trả lời, trước khi phân tích nội dung, chuẩn hóa câu trả lời bằng cách bỏ khoảng trắng đầu/cuối và không phân biệt chữ hoa/thường. Nếu toàn bộ câu trả lời đúng một trong `done`, `stop`, `exit`, `cancel`, thoát ngay vòng lặp. Không kích hoạt khi từ khóa chỉ xuất hiện trong câu văn, ví dụ `không stop` hoặc trong nội dung yêu cầu.
8. `done`: kết thúc phiên hỏi và yêu cầu lưu tiến độ; KHÔNG đồng nghĩa xác nhận các câu hỏi chưa trả lời. `stop` và `exit`: dừng hỏi, lưu các quyết định đã xác nhận và trạng thái còn mở. `cancel`: dừng phiên và không áp dụng thay đổi chưa được xác nhận; giữ nguyên các quyết định đã được ghi từ trước. Không tự động xóa hoặc hoàn tác các thay đổi đã ghi trước đó. Nếu có thay đổi đã xác nhận nhưng chưa ghi, với `cancel` không ghi chúng; với các lệnh còn lại lưu an toàn và báo rõ.
9. **Kết thúc sớm:** Gom toàn bộ điểm chưa rõ đã phát hiện (bao gồm các câu chưa hỏi, câu chưa trả lời và câu trả lời chưa đủ rõ), loại trùng, phân theo đối tượng sở hữu, gán mã câu hỏi ổn định và ghi vào `### Câu hỏi mở` trong từng tài liệu đối tượng. Nếu tài liệu hiện có dùng bố cục khác, tạo mục `Câu hỏi mở` trong phần 8 mà không làm mất nội dung cũ. Không đưa lựa chọn chưa được xác nhận vào FR/AC hoặc `Quyết định làm rõ`. Chỉ ghi bản nháp/câu hỏi mở nếu người dùng đã yêu cầu lưu (`done`) hoặc đã cho phép lưu bản nháp; với `stop`/`exit`, chỉ ghi vào file khi đã được cho phép trong phiên, nếu không liệt kê trong báo cáo để tránh tự ý sửa. Với `cancel`, không ghi thay đổi mới, chỉ báo các câu hỏi còn mở.
10. Nếu không thể trả lời câu hỏi chặn nghiệm thu, không chốt yêu cầu đó; báo **Chưa sẵn sàng**. Nếu vòng lặp kết thúc vì không còn mơ hồ quan trọng, tiếp tục bước D và báo **Sẵn sàng lập kế hoạch** sau khi kiểm chứng.

### Bước D — Tạo mới hoặc cập nhật an toàn
1. Với mỗi đối tượng: nếu file chuẩn chưa có và không có tài liệu tương đương, **Tạo mới**; nếu đã có, **Cập nhật đúng file đó**.
2. Trước khi ghi, đọc lại bản hiện tại để tránh ghi đè thay đổi mới. Bảo toàn ngày tạo, yêu cầu không liên quan, quyết định đã xác nhận, mã định danh, liên kết và lịch sử.
3. Sử dụng mã ổn định, duy nhất trên toàn bộ thư mục: `US-USER-001`, `FR-USER-001`, `AC-USER-001`, `SC-USER-001`; với `permission` dùng `FR-PERMISSION-001`, v.v. Không tái sử dụng mã đã xóa. Khi tiếp nhận file cũ dùng `FR-001`, giữ mã cũ hoặc lập ánh xạ chuyển đổi được xác nhận; không âm thầm đánh số lại.
4. Viết theo mẫu mục 5. Tài liệu chỉ chứa yêu cầu trực tiếp thuộc đối tượng; mỗi user story gắn FR/AC kiểm chứng được. Quy tắc ở đối tượng khác chỉ được dẫn chiếu.
5. Mỗi thay đổi thực chất phải thêm một dòng vào **Lịch sử thay đổi của chính đối tượng**, nêu ngày, mã yêu cầu bị ảnh hưởng, nội dung trước/sau tóm tắt và lý do. Không dùng lịch sử chung của toàn dự án; không thêm dòng nếu không có thay đổi thực chất.
6. Không xóa nội dung cũ không liên quan; khi thay đổi yêu cầu, ghi rõ thay thế/ngừng hiệu lực và tác động đến các tham chiếu.

### Bước E — Kiểm tra sau ghi
- Đọc lại tất cả file đã sửa; kiểm tra đúng đối tượng, không lặp yêu cầu ở file khác, không có liên kết/mã trùng, lịch sử chính xác, ngôn ngữ Tiếng Việt (Vietnamese), không áp đặt thiết kế kỹ thuật.
- Đảm bảo mỗi FR quan trọng có AC có thể quan sát; các câu hỏi quan trọng đã có quyết định xác nhận; không có xung đột chưa xử lý trong phạm vi cập nhật.
- Nếu kiểm tra thất bại, sửa và kiểm tra lại; nếu không thể ghi, cung cấp nội dung/bản vá và báo chưa ghi.
- Báo cáo: đối tượng đã xử lý, file tạo/cập nhật, yêu cầu thêm/sửa, quyết định làm rõ, các tham chiếu, các vấn đề chưa giải quyết và trạng thái **Sẵn sàng lập kế hoạch** hoặc **Chưa sẵn sàng**.


## 5. Mẫu file đối tượng

```markdown
# ĐẶC TẢ ĐỐI TƯỢNG: <Tên đối tượng>

**Đối tượng:** <tên chuẩn>
**Trạng thái:** Bản nháp / Đã xác nhận
**Ngày tạo:** YYYY-MM-DD
**Ngày cập nhật:** YYYY-MM-DD
**Nguồn yêu cầu:** <mô tả ngắn>

## 1. Vai trò và ranh giới đối tượng
- **Mục đích:** ...
- **Thuộc phạm vi:** ...
- **Không thuộc phạm vi:** ...
- **Tài liệu liên quan:** <đường dẫn/mã; không chép nội dung>

## 2. Câu chuyện sử dụng
### US-<OBJECT>-001 — <Tên> (Ưu tiên: P1)
**Với vai trò** ..., **tôi muốn** ..., **để** ...
**Kịch bản độc lập:** ...
**Tiêu chí nghiệm thu:**
- **AC-<OBJECT>-001:** Cho trước ..., khi ..., thì ...

## 3. Yêu cầu chức năng
- **FR-<OBJECT>-001:** Hệ thống BẮT BUỘC ...

## 4. Quy tắc nghiệp vụ
- ...

## 5. Ngoại lệ và trường hợp biên
- **Điều kiện:** ... → **Kết quả mong đợi:** ...

## 6. Tiêu chí thành công
- **SC-<OBJECT>-001:** <kết quả quan sát, phương pháp đo; không bịa chỉ tiêu>

## 7. Quan hệ và phụ thuộc
- <tham chiếu ngắn đến file/mã sở hữu>

## 8. Quyết định làm rõ
- **CL-<OBJECT>-001:** <câu hỏi> → **Đã xác nhận:** <quyết định>; **Ảnh hưởng:** <mã FR/AC>

### Câu hỏi mở
- **Q-<OBJECT>-001 — [Chủ đề]:** [Câu hỏi chưa giải quyết]; **Liên quan:** [mã FR/AC hoặc đối tượng]; **Trạng thái:** Chưa xác nhận; **Lý do:** [thiếu thông tin hoặc phiên bị ngắt].
- Không ghi câu trả lời đề xuất thành quyết định. Khi được giải quyết ở lần gọi sau, cập nhật yêu cầu chính và loại khỏi danh sách câu hỏi mở, bảo toàn lịch sử.

## 9. Kiểm tra tính nhất quán
- **Hiến pháp:** ...
- **Yêu cầu chưa xác nhận:** Không có / <nêu rõ nếu bản nháp được cho phép>
- **Mức sẵn sàng:** Sẵn sàng lập kế hoạch / Chưa sẵn sàng

## 10. Lịch sử thay đổi
| Ngày | Mã liên quan | Thay đổi thông tin đối tượng | Lý do |
|---|---|---|---|
| YYYY-MM-DD | FR-<OBJECT>-001 | Khởi tạo yêu cầu ... | Yêu cầu đã xác nhận |
```

## 6. Điều kiện dừng
- Chỉ tuyên bố **Sẵn sàng lập kế hoạch** nếu mọi điểm mơ hồ quan trọng thuộc phạm vi đã được xác nhận, mọi yêu cầu quan trọng có thể nghiệm thu, và mọi file đã được ghi/kiểm tra thành công.
- Khi còn câu hỏi quan trọng: hỏi và chờ, trừ khi người dùng nhập đúng `done`, `stop`, `exit`, `cancel`; khi đó áp dụng quy tắc ngắt và bảo toàn câu hỏi mở ở Bước C; không chuyển sang lập kế hoạch hoặc triển khai.
- Không tự động chuyển đổi tài liệu cũ, xóa file, hoặc chỉnh sửa skill khác nếu người dùng chưa yêu cầu.
