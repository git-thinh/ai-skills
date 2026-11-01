---
name: spec_agent_vi
description: Khởi tạo, rà soát hoặc sửa đổi quy tắc tác nhân và quy ước phát triển dự án bằng tiếng Việt trong ./spec/AGENT.md. Sử dụng khi gọi /spec_agent_vi hoặc @spec_agent_vi kèm các yêu cầu thiết lập hoặc cập nhật chỉ dẫn dự án, hiến pháp ràng buộc, mô tả dự án, công nghệ, kiến trúc, quy chuẩn mã nguồn, bảo mật, kiểm thử, chất lượng hiệu năng hoặc các ràng buộc tổ chức hoặc quản trị thay đổi;
---

# SPEC AGENT VI — Quy tắc dự án

## 1. Quy định ngôn ngữ bắt buộc
- **BẮT BUỘC sử dụng tiếng Việt** trong toàn bộ quá trình phân tích, câu hỏi làm rõ, phản hồi, báo cáo, tiêu đề, bảng, lịch sử thay đổi và nội dung hiến pháp tạo mới hoặc sửa đổi.
- Không viết lời giải thích, tiêu đề hay đoạn văn bằng tiếng Anh, kể cả khi yêu cầu đầu vào viết bằng tiếng Anh. Diễn giải yêu cầu đó sang tiếng Việt trước khi đưa vào hiến pháp.
- Chỉ giữ nguyên các định danh kỹ thuật không nên dịch: tên công nghệ và thư viện (Nuxt, Tailwind CSS, TypeScript), tên tệp, đường dẫn, câu lệnh, cú pháp, mã nguồn, tên API, khóa cấu hình và các thuật ngữ bắt buộc để tương thích kỹ thuật.
- Khi sửa đổi tài liệu cũ có nội dung tiếng Anh, chuyển phần văn bản được chỉnh sửa và các phần tiếng Anh còn lại sang tiếng Việt nhưng giữ nguyên ý nghĩa, mức độ ràng buộc và các quy tắc đang có. Nếu việc dịch có thể làm thay đổi ý nghĩa pháp quy, yêu cầu xác nhận.
- Diễn đạt mức độ ràng buộc bằng **BẮT BUỘC / NÊN / CÓ THỂ**, không dùng MUST / SHOULD / MAY trong nội dung tài liệu.
- Trước khi kết thúc, rà soát để bảo đảm không còn tiêu đề  hoặc câu giải thích tiếng Anh do kỹ năng tạo ra.

## 2. Vai trò và ranh giới
- Luôn luôn kiểm tra sự tồn tại của file `./spec/AGENT.md` để  chọn chế độ **Khởi tạo** hoặc **Sửa đổi** .
- Quản lý **chỉ dẫn phát triển cho tác nhân** tại `./spec/AGENT.md`: hiến pháp ràng buộc, kiến trúc, quy ước, bảo mật, kiểm thử, chất lượng, quyền sửa đổi. Không tạo đặc tả FR/AC hoặc tự quyết định yêu cầu nghiệp vụ.
- `./spec/AGENT.md` là nguồn quy tắc chuẩn của dự án. Nếu dự án có `AGENTS.md`, `./spec/memory/constitution.md` hoặc chỉ dẫn khác, đọc và sử dụng các nội dung này như nguồn thông tin yêu cầu đầu vào của dự án; KHÔNG tự coi chúng tương đương hoặc tự thay thế.
- Quy tắc ưu tiên: chỉ dẫn hệ thống/nền tảng và người dùng có thẩm quyền ➔ chính sách dự án đã được xác nhận ➔ đề xuất mới ➔ suy luận. Nếu hai chính sách dự án mâu thuẫn mà không có quy tắc ưu tiên được xác nhận, **dừng phần xung đột và hỏi**; không âm thầm chọn.
- `AGENTS.md` ở gốc dự án (nếu có) có thể được công cụ coding agent đọc tự động; `./spec/AGENT.md` không mặc nhiên được tự động đọc. Chỉ cập nhật hoặc tạo file cầu nối `AGENTS.md` khi người dùng cho phép; nếu không, hướng dẫn tham chiếu bằng chỉ dẫn hiện có.

## 3. Phạm vi và an toàn
- Làm việc tại gốc dự án được xác định bằng ngữ cảnh hoặc xác nhận của người dùng. Không thao tác tại thư mục cài đặt Skill.
- BẮT BUỘC bỏ qua thư mục có tên `.git` khi tìm kiếm, quét, đọc, sao chép, thống kê hoặc xử lý tệp dự án, ở mọi cấp thư mục.
- BẮT BUỘC bỏ qua thư mục sinh tự động (`node_modules`, `dist`, `build`, `.nuxt`, `.output`...), tệp bí mật (`.env*`, khóa, chứng chỉ, token) và dữ liệu cá nhân không cần thiết. Không đọc, in hoặc đưa dữ liệu bí mật vào tài liệu.
### 3.1. Vùng cấm tuyệt đối: Git và thư mục ẩn
- **BẮT BUỘC:** Trong toàn bộ vòng đời Skill, KHÔNG đọc, liệt kê, tìm kiếm, thống kê, phân tích hoặc suy luận từ bất kỳ thư mục `.git` nào, kể cả `.git` ở thư mục cha, thư mục con, worktree, submodule hoặc đường dẫn liên kết. Không đọc file `.git` trỏ tới gitdir.
- **BẮT BUỘC:** KHÔNG chạy bất kỳ lệnh `git` nào, bao gồm `git status`, `git log`, `git show`, `git diff`, `git ls-files`, `git branch`, `git rev-parse` hoặc lệnh tương đương qua API/thư viện/công cụ khác. Không truy vấn commit, nhánh, index, object database, reflog hay lịch sử phiên bản, kể cả khi mục đích chỉ là xác định file hiện tại.
- **BẮT BUỘC:** Mặc định bỏ qua toàn bộ thư mục ẩn (tên bắt đầu bằng dấu `.`) khi khảo sát; ngoại lệ chỉ cho phép các đường dẫn hiện hành được nêu rõ trong Skill (`./spec/AGENT.md` không phải thư mục ẩn) hoặc được người dùng chỉ định rõ và không thuộc `.git`. Không tự mở rộng tìm kiếm sang thư mục cha hay ngoài gốc dự án.
- **BẮT BUỘC:** Chỉ dùng nội dung file đang tồn tại trong cây làm việc và được phép truy cập. Nếu file không tồn tại, coi là **không tìm thấy trong cây làm việc hiện tại**; KHÔNG tìm bản cũ bằng Git, không suy luận file đã bị xóa hoặc từng tồn tại.
- **BẮT BUỘC:** Trước mỗi lệnh Shell/Read/Search, kiểm tra lệnh và phạm vi quét; từ chối lệnh có thể đọc vùng cấm. Không dùng `find .`/`grep -R .`/`ls -a` hoặc quét toàn bộ không có bộ lọc loại trừ. Nếu công cụ không hỗ trợ loại trừ chắc chắn, chỉ đọc các đường dẫn cụ thể đã được phép.
- **NÊN:** Khảo sát bằng danh sách file hiện hành có bộ lọc loại trừ, ví dụ `find . -path './.git' -prune -o -name '.*' -prune -o -type f -print` (chỉ khi phạm vi là gốc dự án và không đi theo symlink). Với `rg`, sử dụng bộ lọc ẩn và loại trừ `.git`; không dùng tùy chọn `--hidden` hoặc `--no-ignore`.
- **Kiểm chứng:** Nhật ký công cụ không chứa lệnh Git, truy vấn metadata Git, hoặc thao tác đọc vùng cấm. Nếu đã vô tình truy cập, dừng khảo sát vùng đó, không sử dụng kết quả và báo cáo vi phạm.

- Không sửa mã, chính sách hoặc Skill khác.
- Không tự di chuyển/xóa tài liệu cũ.
- Không chạy script dự án không tin cậy.
- Chỉ đọc có chọn lọc README, manifest, lockfile, cấu hình framework, kiểm thử, lint, CI và cấu trúc thư mục. Không cài gói, chạy script dự án không tin cậy, sửa mã ứng dụng hoặc thay đổi tài liệu ngoài phạm vi.
- Dùng công cụ đọc/ghi thực sự có sẵn trong môi trường; không giả định tên công cụ `read`/`write` là cố định. Nếu không có quyền ghi, chỉ xuất nội dung/bản vá và báo rõ chưa ghi.

## 4. Quy trình mỗi lần gọi
1. **Khảo sát:** Xác định gốc dự án; kiểm tra sự tồn tại và đọc toàn bộ `./spec/AGENT.md` trước khi ghi. Đọc các chính sách có liên quan và bằng chứng công nghệ **chỉ từ các file hiện hành được phép**, tuân thủ mục 2.1; không dùng Git để khảo sát. Ghi rõ file nào đã đọc, file nào không thể đọc.
2. **Chọn chế độ:** Không tìm thấy `./spec/AGENT.md` trong cây làm việc hiện tại → **Khởi tạo**; đã có, kể cả rỗng/hỏng → **Sửa đổi hoặc phục hồi có xác nhận**. Không ghi đè file rỗng/hỏng bằng mẫu nếu chưa bảo toàn bản gốc và được phép.
3. **Phân loại:** Phân biệt dữ kiện đã kiểm chứng, yêu cầu người dùng, đề xuất, giả định và xung đột. Không trình bày đề xuất như chính sách đã thông qua.
4. **Làm rõ có chọn lọc:** Hỏi khi thiếu quyết định ảnh hưởng đến bảo mật, kiến trúc, quy tắc bắt buộc, quyền hạn hoặc khi chính sách mâu thuẫn. Không tự giảm tiêu chuẩn bảo mật/kiểm thử.
5. **Lập thay đổi:** Xác định điều khoản thêm/sửa/ngừng hiệu lực, tác động tới `spec_feature_vi` và `spec_clarify_vi`, file tham chiếu và phiên bản. Không sửa các Skill khác nếu chưa được yêu cầu.
6. **Ghi an toàn:** Đọc lại file ngay trước khi ghi; bảo toàn phần không liên quan, ngày thông qua, số điều khoản và lịch sử. Nếu file thay đổi từ lúc khảo sát, đối chiếu lại, không ghi đè. Ưu tiên ghi tạm rồi thay thế nguyên tử nếu công cụ hỗ trợ; sao lưu khi thay đổi lớn.
7. **Kiểm chứng:** Đọc lại file đã ghi, kiểm tra cấu trúc, phiên bản, ngày, quy tắc bắt buộc có cách kiểm chứng, liên kết, nội dung tiếng Việt và không còn mâu thuẫn đã biết. Không tuyên bố thành công nếu ghi/kiểm chứng thất bại.
8. **Báo cáo:** Chế độ, file, phiên bản trước/sau, các điều khoản thay đổi, bằng chứng, giả định, xung đột chưa giải quyết và tình trạng ghi.

## 5. Phiên bản và quản trị
- Dùng `MAJOR.MINOR.PATCH`, bắt đầu `1.0.0` khi tạo mới. `PATCH`: sửa câu chữ không đổi nghĩa; `MINOR`: bổ sung quy tắc tương thích; `MAJOR`: xóa, thay thế hoặc thay đổi không tương thích. Nếu nhiều loại thay đổi, lấy mức cao nhất; mỗi lần ghi thực chất tăng một phiên bản.
- Ngày thông qua không đổi; ngày cập nhật và lịch sử thay đổi phản ánh ngày thực tế. Nếu thiếu thông tin lịch sử, ghi **chưa xác minh**, không bịa.
- Mọi quy tắc **BẮT BUỘC** phải có phạm vi, hành vi yêu cầu và cách kiểm chứng. Chính sách chưa được chấp thuận phải đánh dấu **Đề xuất**, không coi là có hiệu lực.
- Khi thay đổi ảnh hưởng yêu cầu nghiệp vụ, chỉ báo tác động và đề nghị chạy `spec_feature_vi`; khi cần kiểm định, đề nghị chạy `spec_clarify_vi`.

## 6. Mẫu `./spec/AGENT.md`

```text
# AGENT.md - Quy tắc tác nhân và phát triển dự án
- **Phiên bản:** 1.0.0
- **Ngày thông qua:** YYYY-MM-DD
- **Ngày cập nhật:** YYYY-MM-DD
- **Trạng thái:** Bản nháp / Có hiệu lực
- **Nguồn chính sách liên quan:** ...
## 1. Mục tiêu và phạm vi
- ...
## 2. Kiến trúc và ranh giới mô-đun
- ...
## 3. Công nghệ và phụ thuộc đã kiểm chứng
- ...
## 4. Cấu trúc dự án và quyền sở hữu
- ...
## 5. Quy chuẩn mã nguồn
- ...
## 6. Bảo mật và quyền riêng tư
- ...
## 7. Kiểm thử và cổng chất lượng
- ...
## 8. Hiệu năng và khả năng tiếp cận
- ...
## 9. Quy tắc dành cho tác nhân AI
- BẮT BUỘC đọc chính sách liên quan trước khi thay đổi kiến trúc hoặc mã.
- BẮT BUỘC không tự ý sửa ngoài phạm vi và phải báo cáo sai lệch.
## 10. Quản trị và sửa đổi
- ...
## 11. Vấn đề chưa được phê duyệt
- ...
## 12. Lịch sử thay đổi
| Ngày | Phiên bản | Điều khoản | Thay đổi | Lý do |
|---|---|---|---|---|
```

## 6. Điều kiện hoàn thành
- Chỉ báo **Đã cập nhật** khi file thực sự được ghi và đọc kiểm chứng; nếu chưa có quyền, báo **Đã chuẩn bị, chưa ghi**.
- Không tự tạo `AGENTS.md`, không tự sửa hiến pháp khác, không biến giả định thành quy tắc và không xóa lịch sử.
