---
name: spec_agent_vi
description: Khởi tạo, kiểm tra và sửa đổi ./spec/AGENT.md bằng tiếng Việt khi gọi /spec_agent_vi hoặc yêu cầu quản lý chỉ dẫn tác nhân AI, quy tắc làm việc, quy ước kỹ thuật và giới hạn thao tác. Tuyệt đối không đưa tính năng, chức năng, đối tượng hoặc nghiệp vụ sản phẩm vào AGENT.md.
---

# SPEC AGENT VI — Chỉ dẫn dành cho tác nhân AI

## 1. Bản chất và giới hạn tuyệt đối

`./spec/AGENT.md` là **tài liệu chỉ dẫn cách tác nhân AI làm việc với dự án**, KHÔNG PHẢI đặc tả dự án, sản phẩm hay nghiệp vụ.

**BẮT BUỘC:** Chỉ ghi các quy tắc điều khiển hành vi AI: phạm vi thao tác, cách đọc tài liệu, thứ tự ưu tiên chính sách, tiêu chuẩn kỹ thuật áp dụng khi sửa mã, an toàn công cụ, kiểm thử, kiểm chứng, báo cáo và quản trị thay đổi.

**CẤM** đưa vào `AGENT.md`, kể cả dưới dạng tóm tắt, ví dụ hoặc mục tham khảo chi tiết:
- Tính năng, chức năng, màn hình, API nghiệp vụ, yêu cầu chức năng và tiêu chí nghiệm thu sản phẩm.
- Đối tượng nghiệp vụ, thực thể miền, vai trò người dùng sản phẩm, quyền của từng vai trò hoặc mô hình dữ liệu nghiệp vụ.
- Luồng nghiệp vụ, use case, user story, quy trình thao tác của người dùng, điều kiện kinh doanh, trạng thái nghiệp vụ.
- Mô tả sản phẩm làm gì, phục vụ ai, hỗ trợ nền tảng nào như một danh sách yêu cầu sản phẩm.
- Thông số cụ thể của tính năng (ví dụ thời hạn phiên đăng nhập), trừ khi được chuyển thành quy tắc làm việc của AI mà không lặp lại đặc tả.
- Các vấn đề nghiệp vụ chưa phê duyệt, danh sách tính năng dự kiến hoặc bản sao từ requirements.

**Quy tắc phân biệt:** Mỗi câu phải trả lời câu hỏi “AI phải làm gì, không được làm gì hoặc phải kiểm chứng điều gì khi làm việc?” Nếu câu chủ yếu trả lời “Sản phẩm có gì, ai dùng, làm gì, nghiệp vụ vận hành ra sao?” thì **LOẠI BỎ**. Không hợp thức hóa nội dung sai phạm vi bằng cách thêm tiền tố “AI phải bảo đảm”.

## 2. Ngôn ngữ bắt buộc

- Toàn bộ lời giải thích, câu hỏi làm rõ, lựa chọn trong công cụ tương tác, tiêu đề, báo cáo và nội dung `AGENT.md` phải bằng **tiếng Việt có dấu**.
- Giữ nguyên tên file, đường dẫn, khóa cấu hình, tên công nghệ, mã và định danh kỹ thuật cần thiết.
- Trước MỖI lời gọi công cụ tương tác, kiểm tra tất cả chuỗi do AI tự tạo: `question`, `header`, `title`, `label`, `description`, `options`, `placeholder`...; sửa sang tiếng Việt trước khi gửi.
- Nhãn cố định do nền tảng tự sinh không thuộc quyền kiểm soát của Skill.
- Dùng **BẮT BUỘC / NÊN / CÓ THỂ** cho mức độ ràng buộc.

## 3. Đường dẫn, nguồn và quyền ghi

- Đích duy nhất mặc định: `./spec/AGENT.md` tính từ gốc dự án.
- Kiểm tra file đích trước khi quyết định **Khởi tạo** (chưa tồn tại) hoặc **Sửa đổi** (đã tồn tại, kể cả rỗng hoặc hỏng).
- `AGENTS.md` ở gốc dự án là file khác; không tạo, đồng bộ hoặc sửa nếu chưa được người dùng cho phép rõ ràng. Không mặc định tác nhân khác tự đọc `./spec/AGENT.md`.
- Có thể đọc có chọn lọc `./spec/memory/constitution.md`, `./spec/memory/requirements.md`, `AGENTS.md`, README và các file cấu hình được phép để trích xuất **quy tắc phát triển**, tuyệt đối không sao chép đặc tả nghiệp vụ.
- Không sửa mã, các Skill khác, tài liệu yêu cầu hoặc hiến pháp trong quá trình chạy Skill này.
- Không coi đề xuất hay giả định là quy tắc đã được phê duyệt. Nếu hai chính sách có hiệu lực xung đột và chưa có thứ tự ưu tiên được xác nhận, hỏi bằng tiếng Việt trước khi ghi phần xung đột.

## 4. Vùng cấm Git và giới hạn khảo sát

- **CẤM TUYỆT ĐỐI** chạy mọi lệnh `git`, truy vấn lịch sử, metadata, index, commit hoặc thao tác tương đương qua API/thư viện.
- **CẤM TUYỆT ĐỐI** đọc, quét, liệt kê, tìm kiếm, thống kê hoặc đi theo liên kết vào thư mục `.git` ở mọi cấp; không đọc file `.git` trỏ đến gitdir.
- Mặc định bỏ qua mọi thư mục ẩn, trừ đường dẫn cụ thể do người dùng cho phép rõ ràng và không thuộc `.git`.
- Bỏ qua `node_modules`, `dist`, `build`, `.nuxt`, `.output` và thư mục sinh tự động; không đọc nội dung `.env*`, khóa, chứng chỉ, token hoặc dữ liệu bí mật. Có thể nhắc tên khóa cấu hình công khai khi thật sự cần thiết, không đọc giá trị bí mật.
- Không chạy `find .`, `grep -R .`, `ls -a`, `rg --hidden`, `rg --no-ignore` hay quét rộng thiếu bộ lọc chắc chắn. Nếu không bảo đảm loại trừ, chỉ đọc từng file được phép bằng đường dẫn tường minh.
- Không truy cập ngoài gốc dự án, không chạy script dự án không tin cậy, không cài gói.
- Kiểm tra phạm vi của từng thao tác Shell/Read/Search trước khi thực hiện. Nếu vô tình truy cập vùng cấm, không sử dụng kết quả và báo cáo vi phạm.

## 5. Quy trình bắt buộc mỗi lần chạy

1. **Khảo sát an toàn:** Xác định gốc dự án, kiểm tra và đọc file đích nếu tồn tại. Chỉ đọc tài liệu nguồn cần thiết và được phép.
2. **Chọn chế độ:** Khởi tạo hoặc Sửa đổi. Với file rỗng/hỏng, bảo toàn bản gốc và xin phép phục hồi nếu có nguy cơ mất dữ liệu.
3. **Phân loại từng thông tin nguồn:**
   - **A — Chỉ dẫn AI:** Được phép ghi.
   - **B — Quy ước kỹ thuật:** Chỉ được ghi nếu thể hiện thành hành vi hoặc tiêu chuẩn AI phải tuân thủ khi phát triển; không diễn giải thành chức năng sản phẩm.
   - **C — Nội dung sản phẩm/nghiệp vụ:** CẤM ghi, kể cả khi được nhắc trong tài liệu hiến pháp hoặc yêu cầu.
   - **D — Bí mật, giả định, mâu thuẫn chưa giải quyết:** Không ghi thành quy tắc có hiệu lực.
4. **Lọc nội dung:** Với mỗi câu dự kiến ghi, áp dụng phép thử ở mục 1. Nếu thuộc C hoặc D, loại khỏi bản thảo; không chuyển sang phần “vấn đề chưa phê duyệt” của AGENT.md. Chỉ báo riêng trong phản hồi nếu cần.
5. **Làm rõ:** Chỉ hỏi những quyết định thực sự cần để xác định quy tắc tác nhân; không hỏi hoặc suy diễn yêu cầu nghiệp vụ. Tất cả câu hỏi và phương án bằng tiếng Việt.
6. **Soạn thảo:** Sử dụng mẫu tại mục 7; không tự tạo các mục “mục tiêu sản phẩm”, “tính năng”, “vai trò”, “nghiệp vụ”, “yêu cầu chức năng”.
7. **Ghi an toàn:** Đọc lại file trước khi ghi; giữ các quy tắc hợp lệ không liên quan. Khi sửa file đã bị nhiễm nội dung nghiệp vụ, loại các đoạn sai phạm vi và bảo toàn quy tắc hợp lệ. Nếu file thay đổi đồng thời, dừng và đối chiếu; sao lưu khi thay đổi lớn nếu được phép.
8. **Kiểm chứng sau ghi:** Đọc lại toàn bộ file, kiểm tra tiếng Việt, phạm vi, tính nhất quán, đường dẫn, phiên bản và đặc biệt kiểm tra không còn nội dung C. Nếu thất bại, sửa và kiểm chứng lại; không báo hoàn thành giả.
9. **Báo cáo:** Chế độ, file thực tế, phiên bản trước/sau, quy tắc thay đổi, nhóm nội dung nghiệp vụ đã loại bỏ, xung đột và tình trạng ghi.

## 6. Phiên bản và nguyên tắc cập nhật

- Phiên bản `MAJOR.MINOR.PATCH`; tạo mới từ `1.0.0`.
- `PATCH`: chỉnh câu chữ không đổi nghĩa; `MINOR`: bổ sung quy tắc tương thích; `MAJOR`: thay đổi không tương thích hoặc tái cấu trúc ranh giới tài liệu.
- Không tự tạo ngày thông qua hoặc lịch sử giả. Giữ lịch sử hợp lệ; ghi rõ thông tin chưa xác minh.
- Chỉ ghi quy tắc được xác nhận hoặc có căn cứ rõ ràng. Đề xuất chưa được duyệt chỉ nêu trong báo cáo, không lẫn vào nội dung có hiệu lực.
- Nếu phát hiện yêu cầu nghiệp vụ thiếu hoặc mâu thuẫn, báo người dùng xử lý trong tài liệu đặc tả hoặc Skill tương ứng; không đưa vào `AGENT.md`.

## 7. Mẫu chuẩn `./spec/AGENT.md`

```markdown
# AGENT.md — Chỉ dẫn dành cho tác nhân AI

- **Phiên bản:** 1.0.0
- **Ngày cập nhật:** YYYY-MM-DD
- **Trạng thái:** Bản nháp / Có hiệu lực

## 1. Vai trò và phạm vi hoạt động của tác nhân
- AI chỉ thực hiện nhiệm vụ được giao trong phạm vi được phép.

## 2. Nguồn tài liệu và thứ tự ưu tiên
- AI đọc tài liệu chính sách liên quan trước khi sửa mã.
- AI không sao chép đặc tả nghiệp vụ vào file này.

## 3. Giới hạn công cụ và truy cập
- AI không sử dụng Git hoặc truy cập `.git`.

## 4. Quy ước kiến trúc và mã nguồn
- AI tuân thủ các quy ước kỹ thuật đã được xác nhận khi sửa mã.

## 5. Bảo mật trong quá trình phát triển
- AI không đọc, ghi lại hoặc tiết lộ bí mật không cần thiết.

## 6. Kiểm thử và kiểm chứng
- AI chạy kiểm tra phù hợp khi được phép và báo cáo kết quả thực tế.

## 7. Quản lý thay đổi và báo cáo
- AI không sửa ngoài phạm vi; báo cáo file thay đổi và phần chưa kiểm chứng.

## 8. Lịch sử thay đổi
| Ngày | Phiên bản | Thay đổi quy tắc tác nhân |
|---|---|---|
```

Mẫu là khung, không phải lý do để bịa chính sách chưa xác nhận. Có thể bổ sung mục khi đó thực sự là chỉ dẫn hành vi AI; không bổ sung mục nghiệp vụ.

## 8. Kiểm tra chấp nhận bắt buộc

Trước khi kết luận, tự kiểm tra toàn bộ file:
- Không có danh sách tính năng, chức năng, đối tượng, vai trò sản phẩm hoặc quy trình nghiệp vụ.
- Không có nội dung được sao chép từ `requirements.md` chỉ vì nó xuất hiện trong nguồn.
- Mỗi quy tắc nội dung chính đều hướng dẫn hành vi AI hoặc tiêu chuẩn kỹ thuật AI phải tuân thủ.
- Các quy tắc kỹ thuật được nêu ngắn gọn, không biến thành bản mô tả sản phẩm.
- Không có dữ liệu bí mật, truy cập `.git`, thao tác ngoài phạm vi hoặc nội dung tiếng Anh do AI tự soạn ngoài định danh kỹ thuật.
- File thực tế được đọc kiểm chứng sau ghi.

Chỉ báo **Đã cập nhật** khi ghi và đọc kiểm chứng thành công. Nếu chưa thể ghi, báo **Đã chuẩn bị, chưa ghi**.
