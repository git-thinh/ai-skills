---
name: spec_agent_vi
description: Khởi tạo, kiểm tra, làm sạch và sửa đổi ./spec/AGENT.md bằng tiếng Việt khi gọi /spec_agent_vi. Chỉ quản lý chỉ dẫn hành vi tác nhân AI, quy tắc làm việc, quy ước phát triển và giới hạn công cụ. Nghiêm cấm đưa tính năng, chức năng, đối tượng, vai trò, luồng và yêu cầu nghiệp vụ sản phẩm vào AGENT.md, kể cả dưới hình thức quy tắc bảo mật, kiến trúc hoặc kiểm thử.
---

# SPEC AGENT VI — Quản lý chỉ dẫn tác nhân AI

## 1. Mục đích và bản chất tài liệu

Skill này có nhiệm vụ khởi tạo, kiểm tra, làm sạch và sửa đổi tài liệu:

`./spec/AGENT.md`

**AGENT.md là tài liệu chỉ dẫn tác nhân AI làm việc trong dự án, KHÔNG PHẢI tài liệu mô tả sản phẩm hoặc đặc tả yêu cầu.**

AGENT.md chỉ được chứa:

- Quy tắc hành vi và trách nhiệm của tác nhân AI.
- Phạm vi thao tác và giới hạn quyền hạn của AI.
- Quy tắc sử dụng công cụ, đọc tài liệu và chỉnh sửa mã nguồn.
- Thứ tự ưu tiên và cách áp dụng các chính sách phát triển.
- Quy ước kỹ thuật và tiêu chuẩn chất lượng đã được xác nhận.
- Nguyên tắc bảo vệ dữ liệu trong quá trình phát triển.
- Quy trình kiểm thử, kiểm chứng và báo cáo kết quả.
- Nguyên tắc quản lý thay đổi và xử lý mâu thuẫn chỉ dẫn.

**Nguyên tắc cốt lõi:**

> AGENT.md quy định AI phải làm việc như thế nào, không quy định phần mềm phải hoạt động như thế nào.

Mọi nội dung không thuộc phạm vi trên đều phải bị loại bỏ.

## 2. Ranh giới nội dung tuyệt đối

### 2.1. Nội dung bị nghiêm cấm

**CẤM TUYỆT ĐỐI** đưa vào AGENT.md, kể cả dưới dạng tóm tắt, diễn giải, ví dụ, ghi chú, câu hỏi mở hoặc lịch sử thay đổi:

1. Danh sách tính năng và chức năng của sản phẩm.
2. Mô tả mục đích, khả năng hoặc hành vi của sản phẩm.
3. Yêu cầu chức năng và tiêu chí nghiệm thu nghiệp vụ.
4. Đối tượng nghiệp vụ, thực thể miền và mô hình dữ liệu nghiệp vụ.
5. Vai trò người sử dụng sản phẩm và quyền hạn của từng vai trò.
6. Quy trình nghiệp vụ, use case, user story và luồng thao tác của người dùng.
7. Quy tắc kinh doanh, điều kiện kinh doanh và trạng thái nghiệp vụ.
8. Chi tiết triển khai của một chức năng cụ thể.
9. Thông số vận hành được quy định cho chức năng sản phẩm.
10. Các tính năng dự kiến, chưa phê duyệt hoặc đang chờ làm rõ.
11. Bản sao, bản tóm tắt hoặc bản chuyển ngữ từ tài liệu yêu cầu sản phẩm.
12. Mô tả giao diện, màn hình, thao tác hoặc trải nghiệm của người dùng cuối.

Quy định này áp dụng cho **toàn bộ AGENT.md**, không có ngoại lệ theo tên mục.

### 2.2. Không hợp thức hóa nội dung nghiệp vụ

**CẤM** chuyển yêu cầu sản phẩm thành chỉ dẫn AI bằng cách thêm các tiền tố:

- "AI phải bảo đảm..."
- "AI phải triển khai..."
- "AI phải hỗ trợ..."
- "AI phải tuân thủ chức năng..."
- "Khi phát triển, AI phải xây dựng..."
- "Vì lý do bảo mật, hệ thống phải..."

Nếu phần còn lại của câu mô tả chức năng hoặc hành vi sản phẩm, câu đó vẫn bị cấm.

**Ví dụ sai:**

- AI phải bảo đảm phiên đăng nhập hết hạn sau 24 giờ.
- AI phải triển khai chức năng khôi phục mật khẩu.
- AI phải bảo đảm người quản trị có toàn quyền đối với dữ liệu.
- AI phải xây dựng giao diện hỗ trợ điện thoại và máy tính bảng.

**Ví dụ đúng:**

- AI phải kiểm tra tài liệu yêu cầu liên quan trước khi sửa mã.
- AI không được tự ý thay đổi yêu cầu đã được phê duyệt.
- AI phải bảo vệ thông tin bí mật khi sử dụng công cụ.
- AI phải thực hiện kiểm thử phù hợp và báo cáo kết quả thực tế.

### 2.3. Quy tắc mặc định loại bỏ

- Mỗi thông tin dự kiến ghi vào AGENT.md phải được chứng minh là hợp lệ.
- Nếu không xác định rõ thông tin đó là chỉ dẫn tác nhân hoặc quy ước kỹ thuật được phép, **BẮT BUỘC loại bỏ**.
- Không suy đoán rằng nội dung hợp lệ chỉ vì nó xuất hiện trong tài liệu hiến pháp.
- Không sử dụng tên mục để hợp thức hóa nội dung sai phạm vi.

## 3. Kiểm tra phạm vi hai tầng

Mỗi điều khoản dự kiến ghi phải vượt qua hai tầng kiểm tra.

### Tầng 1 — Kiểm tra hành vi tác nhân

Đặt câu hỏi:

> Điều khoản này có trực tiếp quy định AI phải làm gì, không được làm gì, phải kiểm tra gì hoặc phải báo cáo gì trong quá trình làm việc không?

Nếu không, loại bỏ.

### Tầng 2 — Kiểm tra độc lập nghiệp vụ

Đặt câu hỏi:

> Nếu thay đổi hoàn toàn lĩnh vực sản phẩm nhưng vẫn giữ quy trình phát triển và các quy ước kỹ thuật, điều khoản này có còn phù hợp không?

Nếu không, phải xem xét loại bỏ vì có khả năng chứa yêu cầu nghiệp vụ.

Ngoại lệ duy nhất là quy ước kỹ thuật thuần túy đã được xác nhận, chẳng hạn ngôn ngữ lập trình, công cụ kiểm thử hoặc cấu trúc mã nguồn.

Ngoại lệ này **không áp dụng** cho tính năng, chức năng hoặc thông số vận hành nghiệp vụ.

### Tầng 3 — Kiểm tra nội dung ẩn

Ngay cả khi vượt qua hai tầng trên, phải kiểm tra:

- Có nhắc đến chức năng cụ thể của sản phẩm không?
- Có mô tả quyền hạn của người sử dụng sản phẩm không?
- Có chứa thông số nghiệp vụ không?
- Có mô tả cách sản phẩm hoạt động không?
- Có sao chép hoặc diễn giải yêu cầu chức năng không?

Nếu có, loại bỏ phần sai phạm vi.

Nếu không thể tách phần hợp lệ khỏi phần nghiệp vụ một cách rõ ràng, loại bỏ toàn bộ điều khoản.

## 4. Ngôn ngữ bắt buộc

Toàn bộ quá trình thực hiện Skill phải sử dụng **tiếng Việt có dấu**.

Bao gồm:

- Lời giải thích.
- Câu hỏi làm rõ.
- Phương án lựa chọn.
- Nội dung tài liệu.
- Tiêu đề và ghi chú.
- Báo cáo kết quả.
- Thông báo lỗi.
- Nội dung tương tác với người dùng.

Được giữ nguyên:

- Tên tập tin và đường dẫn.
- Tên công nghệ và thư viện.
- Tên biến, hàm và định danh mã nguồn.
- Khóa cấu hình.
- Cú pháp lập trình.

Trước mỗi lời gọi công cụ tương tác, **BẮT BUỘC** kiểm tra các chuỗi do AI tự tạo như `question`, `header`, `title`, `label`, `description`, `options`, `placeholder`.

Không đặt câu hỏi bằng tiếng Anh khi có thể diễn đạt bằng tiếng Việt.

Các nhãn cố định do nền tảng tự sinh không thuộc quyền kiểm soát của Skill.

Sử dụng các mức độ ràng buộc:

- **BẮT BUỘC:** Quy tắc phải tuân thủ.
- **CẤM:** Hành vi không được thực hiện.
- **NÊN:** Khuyến nghị có căn cứ.
- **CÓ THỂ:** Lựa chọn không bắt buộc.

## 5. Đường dẫn và phạm vi thao tác

### 5.1. Tập tin đích

Tập tin duy nhất được phép tạo hoặc sửa mặc định:

`./spec/AGENT.md`

Đường dẫn được tính từ thư mục gốc dự án.

Trước khi thực hiện, phải kiểm tra tập tin có tồn tại hay không.

- Chưa tồn tại: Chế độ khởi tạo.
- Đã tồn tại: Chế độ sửa đổi.
- Tồn tại nhưng rỗng hoặc hỏng: Chế độ sửa đổi có kiểm tra phục hồi.

Không được coi tập tin rỗng là chưa tồn tại.

### 5.2. Phân biệt AGENT.md và AGENTS.md

- `./spec/AGENT.md` và `./AGENTS.md` là hai tập tin khác nhau.
- **CẤM** tự động tạo, sửa hoặc đồng bộ `./AGENTS.md` nếu người dùng chưa yêu cầu rõ ràng.
- Không mặc định  hoặc tác nhân khác tự động đọc `./spec/AGENT.md`.
- Nếu cần áp dụng các quy tắc cho tác nhân đang chạy, phải bảo đảm cơ chế nạp tài liệu được cấu hình riêng và phù hợp với nền tảng.

### 5.3. Các tập tin nguồn

Có thể đọc có chọn lọc:

- `./spec/memory/requirements.md`
- `./spec/memory/constitution.md`
- `./AGENTS.md`
- `./package.json`
- README
- Tập tin cấu hình kỹ thuật được phép.
- Các tài liệu quy ước phát triển đã được xác nhận.
- `./spec/memory/requirements.md` **không phải nguồn sinh điều khoản AGENT.md**.
- Chỉ đọc tài liệu yêu cầu khi thật sự cần kiểm tra ranh giới hoặc đối chiếu nội dung đã bị đưa nhầm vào AGENT.md.
- Không trích xuất chức năng hoặc nghiệp vụ từ tài liệu yêu cầu để tạo quy tắc tác nhân.

### 5.4. Giới hạn ghi

**CẤM** sửa các tập tin khác trong quá trình chạy Skill, trừ khi người dùng cho phép rõ ràng.

Không tự ý sửa:

- Mã nguồn.
- Tài liệu hiến pháp.
- Tài liệu yêu cầu.
- Các Skill khác.
- Tập tin cấu hình.
- AGENTS.md ở gốc dự án.

## 6. Cấm Git và giới hạn khảo sát

### 6.1. Cấm tuyệt đối Git

**CẤM TUYỆT ĐỐI:**

- Chạy mọi lệnh `git`.
- Đọc lịch sử commit.
- Đọc Git index.
- Truy vấn Git metadata.
- Đọc, liệt kê, tìm kiếm hoặc thống kê thư mục `.git`.
- Truy cập `.git` thông qua API, thư viện hoặc công cụ gián tiếp.
- Đọc tập tin `.git` trỏ đến thư mục Git khác.
- Đi theo symbolic link dẫn vào `.git`.

Quy tắc này áp dụng cho `.git` ở mọi cấp thư mục.

### 6.2. Giới hạn tìm kiếm

Mặc định bỏ qua:

- Mọi thư mục ẩn, ngoại trừ đường dẫn cụ thể được người dùng cho phép và không thuộc `.git`.
- `node_modules`
- `dist`
- `build`
- `.nuxt`
- `.output`
- Các thư mục sinh tự động.

**CẤM** sử dụng các lệnh quét rộng thiếu bộ lọc an toàn, bao gồm:

- `find .`
- `grep -R .`
- `ls -a`
- `rg --hidden`
- `rg --no-ignore`

Không thực hiện thao tác tìm kiếm nếu không bảo đảm loại trừ được vùng cấm.

Ưu tiên đọc trực tiếp từng tập tin cần thiết bằng đường dẫn tường minh.

### 6.3. Giới hạn bảo mật công cụ

- Không đọc giá trị trong `.env*`.
- Không đọc khóa riêng tư, chứng chỉ hoặc token.
- Không truy cập ngoài gốc dự án.
- Không tự ý cài đặt gói.
- Không chạy mã hoặc script dự án không tin cậy.
- Không thực hiện thao tác phá hủy dữ liệu.
- Không sử dụng nội dung từ vùng cấm nếu vô tình truy cập.

Mỗi thao tác Shell, Read hoặc Search phải được kiểm tra phạm vi trước khi thực hiện.

## 7. Phân loại thông tin nguồn

Trước khi soạn thảo, phân loại từng thông tin thành một trong bốn nhóm.

### Nhóm A — Chỉ dẫn tác nhân AI

Bao gồm:

- Quy tắc đọc tài liệu.
- Quy tắc sử dụng công cụ.
- Giới hạn truy cập.
- Quy tắc sửa mã.
- Quy tắc kiểm thử.
- Quy tắc báo cáo.
- Quy tắc quản lý thay đổi.

**Được phép ghi** nếu có căn cứ hợp lệ.

### Nhóm B — Quy ước phát triển kỹ thuật

Bao gồm:

- Ngôn ngữ lập trình.
- Quy ước mã nguồn.
- Kiến trúc phát triển.
- Cấu trúc thư mục mã nguồn.
- Công cụ kiểm thử.
- Quy ước định dạng.
- Tiêu chuẩn chất lượng mã.

Chỉ được ghi nếu:

1. Đã được xác nhận.
2. Là quy ước kỹ thuật thực sự.
3. Không mô tả tính năng hoặc hành vi sản phẩm.
4. Được diễn đạt thành chỉ dẫn phát triển dành cho AI.

**Không sao chép nguyên văn toàn bộ sơ đồ hoặc tài liệu kiến trúc nếu chỉ cần tham chiếu.**

### Nhóm C — Nội dung sản phẩm và nghiệp vụ

Bao gồm mọi tính năng, chức năng, đối tượng, vai trò, quyền hạn, luồng nghiệp vụ, tiêu chí nghiệm thu và yêu cầu sản phẩm.

**CẤM TUYỆT ĐỐI ghi vào AGENT.md.**

Không chuyển nhóm C thành nhóm A bằng cách thay đổi câu chữ.

### Nhóm D — Nội dung không đủ căn cứ

Bao gồm:

- Giả định chưa xác nhận.
- Chính sách mâu thuẫn.
- Đề xuất chưa phê duyệt.
- Thông tin bí mật.
- Nội dung không rõ nguồn.
- Quy tắc không xác định được phạm vi.

Không ghi thành quy tắc có hiệu lực.

Nếu cần, báo cáo riêng cho người dùng.

## 8. Quy trình bắt buộc cho mỗi lần chạy

### Bước 1 — Khảo sát an toàn

- Xác định gốc dự án.
- Kiểm tra sự tồn tại của `./spec/AGENT.md`.
- Đọc tập tin đích nếu tồn tại.
- Đọc có chọn lọc các nguồn kỹ thuật cần thiết.
- Không quét rộng toàn bộ dự án.
- Không truy cập `.git`.

### Bước 2 — Xác định chế độ

**Khởi tạo:**

Khi AGENT.md chưa tồn tại.

**Sửa đổi:**

Khi AGENT.md đã tồn tại.

Nếu tập tin bị hỏng hoặc rỗng, không tự ý xóa dữ liệu cũ khi chưa xác định được phương án an toàn.

### Bước 3 — Phân loại nội dung

Phân loại từng điều khoản hiện có và từng thông tin dự kiến bổ sung theo nhóm A, B, C, D.

Đối với tài liệu đã tồn tại, phải kiểm tra cả các mục cũ.

Không mặc định nội dung cũ là hợp lệ.

### Bước 4 — Làm sạch nội dung sai phạm vi

**BẮT BUỘC** loại bỏ:

- Tính năng và chức năng sản phẩm.
- Đối tượng và vai trò nghiệp vụ.
- Quyền hạn người dùng sản phẩm.
- Luồng nghiệp vụ.
- Tiêu chí nghiệm thu chức năng.
- Thông số vận hành nghiệp vụ.
- Câu hỏi mở về sản phẩm.
- Nội dung sao chép từ requirements.md.

Không chuyển nội dung bị loại bỏ sang mục khác trong AGENT.md.

Giữ nguyên các quy tắc tác nhân hợp lệ.

Nếu một điều khoản trộn nội dung hợp lệ và nội dung nghiệp vụ, chỉ giữ phần hợp lệ khi có thể tách rõ ràng mà không thay đổi ý nghĩa chính sách.

### Bước 5 — Kiểm tra nguồn gốc

Mỗi điều khoản được giữ hoặc bổ sung phải có căn cứ rõ ràng.

Ưu tiên:

1. Chỉ dẫn có hiệu lực từ người dùng và nền tảng.
2. Quy tắc tác nhân đã được xác nhận.
3. Quy ước kỹ thuật đã được phê duyệt.
4. Các tài liệu tham chiếu phù hợp.

Không suy diễn chính sách mới từ yêu cầu sản phẩm.

Không coi thứ tự ưu tiên này là quyền vượt qua các chỉ dẫn cấp cao hơn của môi trường thực thi.

### Bước 6 — Làm rõ khi cần thiết

Chỉ hỏi khi thiếu thông tin thực sự ảnh hưởng đến quy tắc làm việc của AI.

Không hỏi về tính năng hoặc nghiệp vụ sản phẩm trong Skill này.

Mọi câu hỏi và phương án lựa chọn phải bằng tiếng Việt.

Nếu không cần làm rõ, tiếp tục thực hiện.

### Bước 7 — Soạn thảo

Sử dụng mẫu tại mục 10.

Không tạo các mục mô tả:

- Mục tiêu sản phẩm.
- Tính năng.
- Chức năng.
- Đối tượng nghiệp vụ.
- Vai trò người dùng sản phẩm.
- Quy trình nghiệp vụ.
- Yêu cầu chức năng.
- Tiêu chí nghiệm thu sản phẩm.

### Bước 8 — Kiểm tra trước khi ghi

Kiểm tra từng điều khoản theo mục 3.

Nếu phát hiện nội dung nhóm C hoặc D, loại bỏ trước khi ghi.

Không ghi tài liệu khi còn vi phạm phạm vi.

### Bước 9 — Ghi an toàn

- Đọc lại tập tin đích trước khi ghi.
- Không ghi đè nếu nội dung đã thay đổi đồng thời.
- Bảo toàn các quy tắc hợp lệ không liên quan.
- Chỉ sửa tập tin được phép.
- Sao lưu trước khi thay đổi lớn nếu được phép và có phương án an toàn.
- Không ghi lịch sử thay đổi giả.

### Bước 10 — Kiểm chứng sau ghi

**BẮT BUỘC** đọc lại toàn bộ AGENT.md.

Kiểm tra:

1. Đúng đường dẫn.
2. Đúng phạm vi.
3. Không chứa chức năng sản phẩm.
4. Không chứa đối tượng nghiệp vụ.
5. Không chứa vai trò người dùng sản phẩm.
6. Không chứa luồng nghiệp vụ.
7. Không chứa yêu cầu chức năng.
8. Không chứa câu hỏi mở về nghiệp vụ.
9. Không chứa bí mật.
10. Không vi phạm quy tắc Git.
11. Nội dung bằng tiếng Việt.
12. Không có mâu thuẫn chỉ dẫn chưa giải quyết.
13. Phiên bản và lịch sử thay đổi nhất quán.

Nếu phát hiện lỗi, sửa và kiểm chứng lại.

Không báo hoàn thành khi kiểm chứng thất bại.

### Bước 11 — Báo cáo

Báo cáo ngắn gọn:

- Chế độ thực hiện.
- Tập tin đã xử lý.
- Phiên bản trước và sau.
- Các nhóm quy tắc được bổ sung hoặc sửa đổi.
- Các nhóm nội dung nghiệp vụ đã loại bỏ.
- Các vấn đề chưa thể xác minh.
- Trạng thái ghi và kiểm chứng.

Không đưa nội dung nghiệp vụ đã loại bỏ trở lại AGENT.md dưới dạng nhật ký.

## 9. Quy tắc riêng cho từng loại điều khoản

### 9.1. Bảo mật trong quá trình phát triển

Chỉ được ghi quy tắc bảo mật liên quan đến **hành vi của tác nhân AI**.

Được phép:

- Bảo vệ dữ liệu bí mật khi sử dụng công cụ.
- Không tiết lộ thông tin xác thực.
- Không ghi cứng bí mật vào mã nguồn.
- Không tự ý thay đổi chính sách bảo mật.
- Kiểm tra rủi ro trước khi sửa mã.
- Báo cáo lỗ hổng phát hiện được một cách an toàn.

Không được ghi:

- Chức năng xác thực người dùng.
- Chức năng khôi phục tài khoản.
- Mô hình phân quyền sản phẩm.
- Vai trò và quyền của người dùng cuối.
- Thời hạn phiên hoặc token.
- Quy trình đăng nhập hoặc đăng ký.
- Các chức năng giám sát hoặc ghi nhật ký nghiệp vụ.

### 9.2. Kiến trúc và mã nguồn

Được phép:

- Quy tắc sử dụng công nghệ đã xác nhận.
- Quy tắc tổ chức mã nguồn.
- Quy tắc tái sử dụng thành phần.
- Quy tắc kiểm tra kiểu dữ liệu.
- Quy tắc quản lý phụ thuộc.
- Quy tắc bảo trì và chất lượng mã.

Không được ghi:

- Danh sách màn hình.
- Danh sách API nghiệp vụ.
- Các mô-đun chức năng của sản phẩm.
- Danh sách thực thể nghiệp vụ.
- Sơ đồ xử lý nghiệp vụ.
- Chi tiết triển khai của từng chức năng.

Ưu tiên tham chiếu tài liệu kiến trúc thay vì sao chép toàn bộ nội dung.

### 9.3. Kiểm thử và kiểm chứng

Được phép:

- Quy định công cụ kiểm thử.
- Quy tắc viết và tổ chức bài kiểm thử.
- Quy tắc chạy kiểm thử.
- Quy tắc xử lý kiểm thử thất bại.
- Quy tắc báo cáo kết quả thực tế.

Không được ghi:

- Kịch bản nghiệm thu của chức năng cụ thể.
- Danh sách chức năng cần kiểm thử.
- Kết quả mong đợi của một luồng nghiệp vụ.
- Quy tắc kinh doanh dưới dạng test case.

### 9.4. Quản lý thay đổi

Được phép:

- Quy tắc giới hạn phạm vi sửa đổi.
- Quy tắc kiểm tra tác động.
- Quy tắc giữ nguyên chính sách đã phê duyệt.
- Quy tắc báo cáo tập tin thay đổi.
- Quy tắc xử lý xung đột.

Không được ghi:

- Danh sách tính năng dự kiến.
- Lộ trình phát triển sản phẩm.
- Các quyết định nghiệp vụ chưa phê duyệt.
- Câu hỏi mở về yêu cầu chức năng.

## 10. Mẫu chuẩn AGENT.md

Mẫu sau chỉ là cấu trúc tài liệu.

Không được coi các câu mẫu là chính sách đã được phê duyệt nếu chưa có căn cứ.

```markdown
# AGENT.md — Chỉ dẫn dành cho tác nhân AI

- **Phiên bản:** 1.0.0
- **Ngày cập nhật:** YYYY-MM-DD
- **Trạng thái:** Bản nháp / Có hiệu lực

## 1. Vai trò và phạm vi hoạt động của tác nhân

- AI chỉ thực hiện nhiệm vụ trong phạm vi được giao.
- AI không tự ý mở rộng phạm vi thay đổi.

## 2. Nguồn tài liệu và thứ tự ưu tiên

- AI đọc các tài liệu chính sách liên quan trước khi sửa mã.
- AI không sao chép yêu cầu sản phẩm vào AGENT.md.
- AI báo cáo khi phát hiện chỉ dẫn mâu thuẫn.

## 3. Giới hạn công cụ và truy cập

- AI không sử dụng Git hoặc truy cập `.git`.
- AI chỉ truy cập các đường dẫn được phép.
- AI không tự ý thực hiện thao tác phá hủy.

## 4. Quy ước kiến trúc và mã nguồn

- AI tuân thủ quy ước kỹ thuật đã được xác nhận.
- AI không tự ý thay đổi kiến trúc đã phê duyệt.
- AI kiểm tra tác động trước khi sửa mã.

## 5. Bảo mật trong quá trình phát triển

- AI bảo vệ dữ liệu bí mật khi sử dụng công cụ.
- AI không đọc hoặc tiết lộ thông tin xác thực trái phép.
- AI không ghi cứng bí mật vào mã nguồn.
- AI báo cáo rủi ro bảo mật phát hiện được.

## 6. Kiểm thử và kiểm chứng

- AI thực hiện kiểm thử phù hợp khi được phép.
- AI không báo cáo kết quả kiểm thử chưa thực hiện.
- AI nêu rõ những phần chưa thể kiểm chứng.

## 7. Quản lý thay đổi và báo cáo

- AI không sửa ngoài phạm vi nhiệm vụ.
- AI kiểm tra lại nội dung sau khi ghi.
- AI báo cáo các tập tin đã thay đổi.

## 8. Lịch sử thay đổi

| Ngày | Phiên bản | Thay đổi quy tắc tác nhân |
|---|---|---|
```

**CẤM** bổ sung mục mô tả tính năng hoặc nghiệp vụ vào mẫu này.

## 11. Quản lý phiên bản

Sử dụng phiên bản:

`MAJOR.MINOR.PATCH`

Quy tắc:

- **MAJOR:** Thay đổi không tương thích hoặc tái cấu trúc đáng kể chính sách tác nhân.
- **MINOR:** Bổ sung quy tắc tương thích.
- **PATCH:** Chỉnh sửa câu chữ không làm thay đổi ý nghĩa chính sách.

Khởi tạo từ `1.0.0`.

Khi sửa đổi, xác định mức tăng phiên bản theo tác động thực tế.

Không tự tạo ngày thông qua, lịch sử hoặc quyết định phê duyệt.

Không ghi nội dung nghiệp vụ vào lịch sử thay đổi.

Nếu ngày cập nhật không thể xác minh, phải thể hiện trạng thái chưa xác minh thay vì tự tạo dữ liệu.

## 12. Kiểm tra chấp nhận bắt buộc

Trước khi kết luận, kiểm tra toàn bộ tài liệu theo danh sách:

- [ ] Tập tin đúng là `./spec/AGENT.md`.
- [ ] Không có tính năng sản phẩm.
- [ ] Không có chức năng sản phẩm.
- [ ] Không có đối tượng nghiệp vụ.
- [ ] Không có vai trò người dùng sản phẩm.
- [ ] Không có mô hình phân quyền nghiệp vụ.
- [ ] Không có luồng nghiệp vụ.
- [ ] Không có user story hoặc use case sản phẩm.
- [ ] Không có tiêu chí nghiệm thu chức năng.
- [ ] Không có thông số vận hành nghiệp vụ.
- [ ] Không có danh sách màn hình hoặc API nghiệp vụ.
- [ ] Không sao chép nội dung requirements.md.
- [ ] Không hợp thức hóa nghiệp vụ bằng tiền tố "AI phải".
- [ ] Các quy tắc bảo mật chỉ hướng dẫn hành vi AI.
- [ ] Các quy tắc kiến trúc không mô tả chức năng sản phẩm.
- [ ] Các quy tắc kiểm thử không chứa kịch bản nghiệm thu nghiệp vụ.
- [ ] Các điều khoản kỹ thuật có căn cứ xác nhận.
- [ ] Không có dữ liệu bí mật.
- [ ] Không có truy cập Git hoặc `.git`.
- [ ] Nội dung và giao tiếp bằng tiếng Việt.
- [ ] Không có chính sách giả định được trình bày như đã phê duyệt.
- [ ] Tập tin đã được đọc và kiểm chứng sau khi ghi.

**Chỉ báo "Đã cập nhật" khi đã ghi và kiểm chứng thành công.**

Nếu chưa ghi, báo "Đã chuẩn bị, chưa ghi".

Nếu kiểm chứng thất bại, báo rõ lỗi và không tuyên bố hoàn thành.

## 13. Nguyên tắc cuối cùng

**AGENT.md là tài liệu điều khiển hành vi của tác nhân AI.**

Không phải:

- Tài liệu đặc tả sản phẩm.
- Tài liệu yêu cầu chức năng.
- Tài liệu nghiệp vụ.
- Tài liệu mô hình dữ liệu nghiệp vụ.
- Tài liệu phân quyền người dùng sản phẩm.
- Tài liệu kiểm thử nghiệm thu sản phẩm.
- Nơi lưu trữ các câu hỏi nghiệp vụ chưa giải quyết.

Khi phát hiện nội dung sai phạm vi, **BẮT BUỘC loại bỏ**, không diễn giải lại để giữ trong AGENT.md.

Nếu không đủ căn cứ xác định một điều khoản là chỉ dẫn tác nhân hoặc quy ước phát triển hợp lệ, **không ghi điều khoản đó**.

**Ưu tiên tính đúng phạm vi hơn độ dài hoặc mức độ đầy đủ của tài liệu.**