---
name: spec_clarify_vi
description: Làm rõ đặc tả tính năng hoàn toàn bằng tiếng Việt sau @spec_specify_vi và trước lập kế hoạch. Sử dụng khi gọi /spec_clarify_vi hoặc @spec_clarify_vi, có thể kèm tên tính năng hay vùng cần tập trung; phát hiện tối đa 5 vấn đề mơ hồ quan trọng, hỏi người dùng, cập nhật mục ## Clarifications và các yêu cầu liên quan trong ./spec/features/<ten-tinh-nang>.md mà không thiết kế kỹ thuật.
---

# Làm rõ yêu cầu đặc tả — chỉ sử dụng tiếng Việt

## Quy định ngôn ngữ bắt buộc
- BẮT BUỘC sử dụng tiếng Việt trong toàn bộ phân tích, câu hỏi, lựa chọn, báo cáo và nội dung tài liệu, kể cả khi đầu vào bằng tiếng Anh.
- Chỉ giữ nguyên tên tệp, đường dẫn, mã FR/AC/SC/US, tên riêng và định danh kỹ thuật không thể dịch. Dùng BẮT BUỘC / NÊN / CÓ THỂ thay cho MUST / SHOULD / MAY.
- Tiêu đề `## Clarifications` được giữ nguyên để tương thích nghiệp vụ yêu cầu; các tiêu đề con và nội dung giải thích bằng tiếng Việt.

## Đầu vào, tài liệu và phạm vi
- Nhận nguyên văn tham số sau `/spec_clarify_vi` hoặc `@spec_clarify_vi`: tên tính năng, đường dẫn đặc tả, câu hỏi cụ thể hoặc khu vực ưu tiên làm rõ (không bắt buộc).
- Thực hiện ở thư mục gốc dự án đang mở. BẮT BUỘC bỏ qua mọi thư mục `.git` ở mọi cấp khi tìm kiếm, quét, đọc, sao chép, thống kê và xử lý tệp.
- Đọc `./spec/constitution.md` nếu tồn tại, rồi đọc toàn bộ đặc tả đích `./spec/features/<ten-tinh-nang>.md` do `spec_specify_vi` tạo. Không giả định đặc tả nằm ở `specify.md` nếu không có tệp đó.
- Nếu người dùng chỉ định một đường dẫn đặc tả khác trong dự án, sử dụng đường dẫn được chỉ định sau khi kiểm tra. Nếu không chỉ định, xác định tệp duy nhất phù hợp trong `./spec/features/`; nếu có nhiều ứng viên, hỏi chọn tệp; nếu không có, báo cần chạy `/spec_specify_vi` trước. Không tự tạo đặc tả thay cho Specify.
- Mục tiêu duy nhất: xác định và giải quyết **Cái gì (What)** phần mềm cần làm, **Tại sao (Why)** cần làm, quy tắc và kết quả quan sát được. Không chọn công nghệ, kiến trúc, thuật toán, API, cơ sở dữ liệu, thư viện hay cách triển khai.

## Nguyên tắc nguồn và ưu tiên
1. Hiến pháp hiện có là ràng buộc; không tự sửa hiến pháp. Nếu xung đột, nêu rõ và xin xác nhận hướng xử lý phù hợp.
2. Đặc tả hiện có là nguồn trạng thái yêu cầu; quyết định mới được người dùng xác nhận là nguồn cập nhật. Không thay đổi ý nghĩa các yêu cầu không liên quan.
3. Phân biệt **đã xác nhận**, **đề xuất**, **giả định** và **chưa giải quyết**. Không biến lựa chọn khuyến nghị hoặc sự im lặng thành quyết định.
4. Chỉ hỏi những vấn đề có ảnh hưởng đáng kể đến phạm vi, hành vi, quyền, quy tắc nghiệp vụ hoặc khả năng nghiệm thu. Không hỏi lại thông tin đã được đặc tả xác định rõ.

## Quy trình thực hiện
1. **Xác định đặc tả:** Kiểm tra đường dẫn và đọc toàn bộ tệp, kể cả lịch sử, câu hỏi mở và các lần làm rõ trước. Đọc hiến pháp nếu có. Nếu không đọc được, dừng và báo lý do; không sửa tệp dựa trên suy đoán.
2. **Kiểm tra độ rõ:** Đánh giá mục tiêu/phạm vi; tác nhân và quyền; luồng chính; dữ liệu ở mức nghiệp vụ; quy tắc và điều kiện; ngoại lệ/trường hợp biên; tiêu chí nghiệm thu; tiêu chí thành công; phụ thuộc; thuật ngữ; tính nhất quán giữa US, FR, AC, SC; xung đột hiến pháp. Ghi bằng chứng theo mục/mã yêu cầu.
3. **Ưu tiên:** Chấm mỗi điểm mơ hồ theo tác động (cao/vừa/thấp) và độ bất định. Ưu tiên vấn đề có thể làm thay đổi hành vi người dùng, ranh giới tính năng, an toàn/quyền truy cập hoặc làm cho nghiệm thu không xác định. Loại trùng lặp và các vấn đề đã giải quyết. Chọn tối đa **5 câu hỏi cho mỗi lần gọi Skill**, không phải 5 câu mỗi lượt hội thoại.
4. **Đặt câu hỏi tương tác:** Hỏi từng câu hoặc nhóm nhỏ khi hợp lý, không vượt tổng 5 câu. Mỗi câu phải nêu ngữ cảnh/mã liên quan, câu hỏi duy nhất, 2–4 lựa chọn loại trừ nhau khi có thể, hậu quả nghiệp vụ ngắn gọn và lựa chọn **Khác (tự nhập)**. Có thể đề xuất phương án khuyến nghị với lý do, nhưng không tự chọn. Nếu câu hỏi không phù hợp dạng trắc nghiệm, hỏi mở ngắn gọn. Không dùng lựa chọn mặc định như một sự đồng ý.
5. **Xử lý trả lời:** Kiểm tra câu trả lời có xác định được hành vi hay không. Nếu câu trả lời mâu thuẫn, mơ hồ hoặc ngoài các lựa chọn, hỏi xác nhận ngắn trong phạm vi ngân sách câu hỏi; không tự diễn giải thành quyết định. Nếu người dùng bỏ qua, từ chối hoặc không trả lời, giữ trạng thái chưa giải quyết và tiếp tục với những quyết định đã rõ. Không cần đủ 5 câu nếu ít vấn đề.
6. **Cập nhật an toàn:** Sau khi có câu trả lời được xác nhận, đọc lại tệp trước khi ghi để tránh ghi đè thay đổi mới. Tạo hoặc cập nhật duy nhất một mục cấp hai `## Clarifications`, ghi ngày, câu hỏi, quyết định và mã yêu cầu liên quan. Nếu mục đã có, nối thêm phiên làm rõ; không nhân đôi quyết định cũ. Đồng thời sửa chính xác các mục US/FR/AC/SC, quy tắc, ngoại lệ, phạm vi, giả định, câu hỏi mở và mức sẵn sàng bị ảnh hưởng. Giữ nguyên mã định danh hiện có; chỉ cấp mã mới nếu cần, không tái sử dụng mã đã tồn tại. Không xóa lịch sử hoặc yêu cầu khác.
7. **Đồng bộ tính nhất quán:** Quyết định phải được thể hiện bằng yêu cầu kiểm chứng được, không chỉ xuất hiện trong nhật ký làm rõ. Loại câu hỏi mở đã giải quyết, giữ câu hỏi chưa giải quyết; ghi lịch sử thay đổi và ngày cập nhật theo định dạng tài liệu. Nếu chưa có câu trả lời được xác nhận, không ghi quyết định giả định; chỉ cập nhật tệp khi người dùng đồng ý ghi nhận trạng thái câu hỏi mở.
8. **Xác minh:** Đọc lại tệp đã ghi. Kiểm tra một mục `## Clarifications`, không có quyết định trùng/mâu thuẫn, các mã US/FR/AC/SC vẫn ổn định, tiêu chí nghiệm thu quan sát được, không xuất hiện lựa chọn công nghệ mới, nội dung tiếng Việt và hiến pháp được tuân thủ.
9. **Báo cáo:** Nêu đường dẫn, số điểm mơ hồ phát hiện, số câu đã hỏi (tối đa 5), số quyết định được xác nhận và cập nhật, các vấn đề còn mở, mục đã sửa và trạng thái **Sẵn sàng lập kế hoạch / Cần làm rõ tiếp**. Chỉ báo đã cập nhật thành công khi thực sự ghi và kiểm chứng tệp.

## Quy tắc cập nhật `## Clarifications`
- Thêm mục này trước `## 10. Lịch sử thay đổi` nếu đặc tả dùng mẫu của `spec_specify_vi`; giữ nguyên các mục đã có, không đánh số lại toàn bộ tài liệu.
- Mỗi phiên có đề mục `### Phiên làm rõ YYYY-MM-DD` (nếu có nhiều phiên cùng ngày, thêm số thứ tự).
- Mỗi quyết định có mã `CL-001`, `CL-002`... ổn định, tăng dần, không trùng; ghi **Liên quan**, **Câu hỏi**, **Quyết định**, **Tác động đến đặc tả**.
- Với câu hỏi chưa được giải quyết, giữ trong `8.3. Câu hỏi mở` thay vì ghi là quyết định. Không đưa lựa chọn chưa được xác nhận vào phần yêu cầu chính thức.

## Mẫu cập nhật
```markdown
## Clarifications

### Phiên làm rõ YYYY-MM-DD

- **CL-001 — [Chủ đề]:**
  - **Liên quan:** FR-001, AC-001.
  - **Câu hỏi:** Khi [tình huống nghiệp vụ], hệ thống cần làm gì?
  - **Quyết định:** [Câu trả lời đã được người dùng xác nhận].
  - **Tác động đến đặc tả:** Cập nhật FR-001 và AC-001 để quy định hành vi có thể kiểm chứng.
```

## Quy tắc an toàn
- Không đọc `.env`, khóa bí mật, dữ liệu xác thực hay thông tin cá nhân không cần thiết; không gửi dữ liệu dự án ra dịch vụ ngoài.
- Không cài gói, chạy lệnh phá hủy, sửa mã nguồn, hiến pháp hoặc tệp không liên quan.
- Không tự ý giải quyết xung đột bằng cách thay đổi phạm vi hay hạ thấp yêu cầu bảo mật.
- Nếu không có quyền ghi, cung cấp bản vá/nội dung tiếng Việt để người dùng tự áp dụng; không báo thành công giả.

## Điều kiện hoàn thành
- [ ] Đã xác định đúng đặc tả và đọc hiến pháp nếu có.
- [ ] Đã kiểm tra những vùng mơ hồ quan trọng, có căn cứ từ tài liệu.
- [ ] Không hỏi quá 5 câu cho một lần gọi Skill.
- [ ] Không biến khuyến nghị hoặc giả định thành quyết định chưa xác nhận.
- [ ] `## Clarifications` phản ánh đúng quyết định và các mục yêu cầu liên quan được đồng bộ.
- [ ] Vấn đề chưa giải quyết vẫn được ghi nhận và báo cáo trung thực.
- [ ] Không thiết kế kỹ thuật; không sửa tệp ngoài phạm vi; đã xác minh tệp sau khi ghi.
