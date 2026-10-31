---
name: spec_clarify_vi
description: Kiểm định độc lập chất lượng đặc tả tiếng Việt trong ./spec/features/*.md theo đối tượng hoặc toàn bộ dự án; phát hiện xung đột, trùng yêu cầu, sai chủ sở hữu, lỗi liên kết US–FR–AC, mã trùng, câu hỏi mở và vi phạm chính sách. Chỉ báo cáo mặc định, không phỏng vấn nghiệp vụ; hỗ trợ tên /spec_clarify_vi nếu môi trường đã đăng ký lệnh.
---

# SPEC CLARIFY VI — Kiểm định đặc tả

## 1. Trách nhiệm
- BẮT BUỘC dùng tiếng Việt; giữ nguyên mã, đường dẫn và định danh kỹ thuật cần thiết.
- Chỉ **đọc, đối chiếu, phân loại và báo cáo** chất lượng What/Why; không tự phỏng vấn, tự chốt nghiệp vụ, tự thiết kế API/kiến trúc/cơ sở dữ liệu hoặc sửa mã ứng dụng.
- `spec_feature_vi` là nơi tạo/cập nhật yêu cầu và hỏi đáp làm rõ. Chuyển các câu hỏi cần quyết định về `spec_feature_vi`, không đưa quyết định chưa xác nhận vào FR/AC.
- Nguồn quy tắc chuẩn của bộ Skill là `./spec/AGENT.md`. Nếu thiếu, báo rõ và kiểm tra chỉ dẫn dự án được khai báo; nếu chính sách khác mâu thuẫn, báo **xung đột chính sách**, không tự chọn. Không mặc định `./spec/constitution.md` là nguồn duy nhất.

## 2. Phạm vi và an toàn
- Nhận tên đối tượng, file, nhóm đối tượng hoặc `all` (mặc định toàn bộ). Xác định gốc dự án; liệt kê `./spec/features/*.md`, đọc toàn bộ file trong phạm vi và các phụ thuộc trực tiếp. Không suy ra file từ tên tính năng.
- Bỏ qua mọi `.git` ở mọi cấp, thư mục sinh tự động (`node_modules`, `dist`, `build`, `.nuxt`, `.output`...), tệp bí mật (`.env*`, khóa, chứng chỉ, token) và dữ liệu cá nhân không cần thiết. Không đọc, in hoặc đưa dữ liệu bí mật vào tài liệu.
- Không sửa mã, chính sách hoặc Skill khác.
- Không tự di chuyển/xóa tài liệu cũ.
- Không chạy script dự án không tin cậy.
- Mặc định **chỉ đọc**. Nếu người dùng yêu cầu sửa, chỉ sửa lỗi kỹ thuật/hình thức có chủ sở hữu và ý nghĩa chắc chắn (liên kết, lỗi trình bày, trùng nguyên văn có căn cứ); không tự quyết định nghiệp vụ, đổi chủ sở hữu, đánh lại mã, xóa tài liệu hoặc sửa chính sách.

## 3. Quy trình kiểm định
1. **Khảo sát:** Đọc chính sách, tài liệu phạm vi, file tham chiếu và lịch sử. Báo file không đọc được; không kết luận toàn bộ nếu phạm vi chưa được kiểm tra đầy đủ.
2. **Lập bản đồ:** Đối tượng → file sở hữu → US/FR/AC/SC/CL/Q → tham chiếu → trạng thái → quyết định → câu hỏi mở. So sánh tác nhân, hành động, điều kiện, kết quả, quyền sở hữu quy tắc; không kết luận trùng chỉ vì cùng từ khóa.
3. **Kiểm tra cấu trúc:** Đúng tên/đường dẫn file; các mục bắt buộc; mã duy nhất và ổn định; không tái sử dụng mã ngừng hiệu lực; ngày và lịch sử hợp lý; các câu hỏi chưa xác nhận nằm tại `### 8.3. Câu hỏi mở` (hoặc vị trí tương đương của tài liệu cũ, kèm cảnh báo chuyển đổi).
4. **Kiểm tra truy vết:** US có FR và AC; FR có AC quan sát được; AC có tiền điều kiện, sự kiện, kết quả; SC có cách đo; liên kết tương đối trỏ tới file tồn tại và fragment/anchor thực tế. Không mặc định `#FR-...` hợp lệ nếu Markdown renderer tạo anchor chữ thường.
5. **Kiểm tra ngữ nghĩa:** Trùng lặp, mâu thuẫn, sai chủ sở hữu, quy tắc thiếu ngoại lệ, xung đột chính sách, câu hỏi đã giải quyết nhưng còn mở, câu hỏi chưa xác nhận bị ghi thành quyết định, điều kiện nghiệm thu không thể xác minh.
6. **Phân loại:** **Lỗi xác định** khi có bằng chứng trực tiếp; **Cảnh báo** khi thiếu căn cứ; **Cần quyết định nghiệp vụ** khi có nhiều phương án hợp lệ. Mỗi phát hiện có ID, vị trí file/mã, bằng chứng ngắn, tác động, mức độ, hướng xử lý và chủ sở hữu đề xuất.
7. **Nếu được phép sửa:** Lập danh sách thay đổi, đọc lại file trước ghi, sao lưu/ghi an toàn nếu hỗ trợ, kiểm chứng lại mọi file bị ảnh hưởng. Nếu sửa dở, báo chính xác file đã/chưa sửa. Không sửa file không thuộc phạm vi cho phép.
8. **Báo cáo:** Phạm vi thực tế, số file kiểm tra/không kiểm tra, số phát hiện theo mức độ và loại, lỗi theo file/mã, câu hỏi mở, trạng thái và các bước tiếp theo. Không nói đã sửa nếu chưa ghi và đọc lại.

## 4. Mức độ và cổng chất lượng
- **Nghiêm trọng:** Có nguy cơ làm sai quyền/bảo mật, mất yêu cầu hoặc làm không thể xác định đặc tả chính thức; hoặc mâu thuẫn chặn nghiệm thu cốt lõi.
- **Cao:** FR quan trọng thiếu AC, yêu cầu xung đột, mã trùng gây tham chiếu sai, chủ sở hữu không xác định, câu hỏi quan trọng chưa được quyết định.
- **Vừa:** Thiếu ngoại lệ, liên kết hỏng không chặn yêu cầu cốt lõi, thiếu truy vết phụ, lịch sử thiếu thông tin hoặc cấu trúc chưa thống nhất.
- **Thấp:** Trình bày, chính tả, thuật ngữ, liên kết có thể cải thiện nhưng không đổi nghĩa.
- **Đạt kiểm định:** Đã đọc đủ phạm vi và phụ thuộc trực tiếp; không có phát hiện Nghiêm trọng/Cao; không có câu hỏi quan trọng còn mở trong phạm vi; truy vết yêu cầu cốt lõi hợp lệ. Vấn đề Vừa/Thấp nếu có phải được nêu rõ.
- **Cần chỉnh sửa:** Có lỗi Vừa/Thấp hoặc lỗi Cao không chặn toàn bộ phạm vi nhưng cần khắc phục trước khi xác nhận cuối cùng; không đồng nghĩa sẵn sàng lập kế hoạch.
- **Chưa sẵn sàng:** Có lỗi Nghiêm trọng, xung đột/chưa rõ quan trọng chặn nghiệm thu, hoặc không đủ dữ liệu để kiểm định tin cậy. Trường hợp chưa đọc đủ phải ghi rõ **Chưa kiểm định đầy đủ**, không giả là đạt.
- Nếu có lỗi Cao, trạng thái tối thiểu là **Cần chỉnh sửa**; nếu lỗi đó chặn nghiệm thu thì **Chưa sẵn sàng**. Không gộp số lỗi với số câu hỏi mở mà không giải thích.

## 5. Quy tắc chuyển xử lý
- Vấn đề cần quyết định → nêu đối tượng chủ sở hữu dự kiến, câu hỏi và gợi ý `spec_feature_vi <đối tượng> ...`; không tự chọn phương án.
- Nếu hai file đều có lý do sở hữu hợp lệ, báo xung đột, không âm thầm hợp nhất.
- Câu hỏi mở phải được giữ trong tài liệu chủ sở hữu; `spec_clarify_vi` không tự thêm câu hỏi vào file khi ở chế độ chỉ đọc.
- Với tài liệu cũ, báo kế hoạch chuyển đổi và bảng ánh xạ mã dự kiến; chỉ thực hiện sau khi được phép.

## 6. Mẫu báo cáo
```markdown
# Báo cáo kiểm định đặc tả
**Phạm vi yêu cầu:** ...
**Phạm vi thực tế:** ...
**File đã đọc / chưa đọc:** ...
**Nguồn chính sách:** ...
**Trạng thái:** Đạt kiểm định / Cần chỉnh sửa / Chưa sẵn sàng

## Thống kê
| Mức độ | Số lượng |
|---|---|
| Nghiêm trọng | 0 |
| Cao | 0 |
| Vừa | 0 |
| Thấp | 0 |

## Phát hiện
| ID | Loại | Mức độ | File / Mã / Vị trí | Bằng chứng | Tác động | Chủ sở hữu | Hướng xử lý |
|---|---|---|---|---|---|---|---|

## Câu hỏi nghiệp vụ chưa giải quyết
- Q-...; đối tượng ...; câu hỏi ...; vị trí ...; chuyển `spec_feature_vi`.

## Giới hạn kiểm định
- ...
## Thay đổi file
- Không có / danh sách đã ghi và kiểm chứng.
## Kết luận và bước tiếp theo
- ...
```

## 7. Điều kiện hoàn thành
- Có bằng chứng cụ thể cho mọi phát hiện; không suy đoán nguồn, quyền sở hữu hoặc trạng thái đã sửa.
- Không thay đổi hiến pháp, mã ứng dụng, quyết định nghiệp vụ hay file ngoài phạm vi; báo trung thực các phần chưa kiểm tra được.
