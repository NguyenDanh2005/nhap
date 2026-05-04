# CHƯƠNG 5: QUẢN LÝ CHẤT LƯỢNG

## 5.1. Lập kế hoạch chất lượng

### 5.1.1. Các metric chất lượng trong dự án

Trong dự án xây dựng Hệ thống Quản lý Bệnh án Điện tử, các metric chất lượng được áp dụng bao gồm:

- **Tính khả dụng của giao diện:** Giao diện hệ thống phải thân thiện, dễ sử dụng cho cả bác sĩ và y tá, kể cả những người chưa quen với phần mềm. Giao diện cần hiển thị đầy đủ thông tin bệnh nhân, sinh hiệu, đơn thuốc một cách trực quan.

- **Tính toàn vẹn của dữ liệu:** Đảm bảo dữ liệu bệnh án, đơn thuốc, sinh hiệu không bị mất mát hay sai lệch trong quá trình lưu trữ và truyền tải. Đây là yêu cầu đặc biệt quan trọng vì liên quan trực tiếp đến sức khỏe bệnh nhân.

- **Tính ổn định của ứng dụng:** Hệ thống phải hoạt động ổn định, không bị lỗi hay crash trong quá trình bác sĩ lập bệnh án hoặc y tá đo sinh hiệu. Khả năng tránh các tác động không mong muốn khi cập nhật phần mềm.

- **Tính phù hợp:** Phần mềm phải cung cấp đầy đủ các chức năng nghiệp vụ y tế: quản lý bệnh nhân, đo và lưu sinh hiệu, lập bệnh án 5 tab (khám lâm sàng, chẩn đoán, kê đơn, dặn dò, lịch sử), quản lý lịch hẹn, báo cáo thống kê.

- **Tính bảo mật:** Hệ thống phải phân quyền rõ ràng giữa bác sĩ và y tá. Thông tin bệnh nhân phải được bảo vệ, chỉ người có thẩm quyền mới được truy cập.

- **Tính đáp ứng thời gian:** Đảm bảo hệ thống phản hồi nhanh khi tải danh sách bệnh nhân, lưu bệnh án, gọi API. Thời gian phản hồi API không vượt quá 3 giây trong điều kiện bình thường.

---

### 5.1.2. Các loại kiểm thử sử dụng

- **Kiểm thử chức năng (Functional Testing):** Kiểm thử định kỳ từng module: đăng nhập, quản lý bệnh nhân, đo sinh hiệu, lập bệnh án, kê đơn thuốc, lịch sử khám bệnh.

- **Kiểm thử tích hợp (Integration Testing):** Kiểm tra sự kết nối giữa ứng dụng Java Swing và Spring Boot API Server, đảm bảo dữ liệu bệnh án được lưu và truy xuất chính xác qua REST API.

- **Kiểm tra tính toàn vẹn dữ liệu:** Kiểm tra dữ liệu bệnh án, đơn thuốc sau khi lưu vào SQL Server có khớp với dữ liệu đầu vào hay không.

- **Kiểm thử giao diện người dùng (UI Testing):** Đảm bảo giao diện hiển thị đúng trên các độ phân giải màn hình khác nhau, các badge trạng thái hiển thị đúng màu sắc.

- **Kiểm thử hiệu năng (Performance Testing):** Kiểm tra tốc độ tải danh sách bệnh nhân, tốc độ lưu bệnh án khi có nhiều bản ghi trong database.

- **Thiết lập lịch trình kiểm thử định kỳ** dựa trên các mốc hoàn thành module, đảm bảo mỗi chức năng được kiểm thử trước khi tích hợp vào hệ thống chính.

---

## 5.2. Kế hoạch giám sát chất lượng

**Bảng 5.1: Bảng kế hoạch giám sát chất lượng**

| Thời gian đánh giá | Các công việc đã hoàn thành | Nội dung đánh giá | Đánh giá |
|---|---|---|---|
| Tuần 1 (Lập kế hoạch) | Hoàn thành bộ tài liệu kế hoạch dự án | Tính khả thi; Tính chính xác; Thời gian thực hiện | Tài liệu đầy đủ, phân công rõ ràng? |
| Tuần 2 (Thu thập yêu cầu) | Hoàn thành thu thập yêu cầu từ bệnh viện | Gặp gỡ khách hàng lấy yêu cầu; Viết tài liệu yêu cầu người dùng, yêu cầu hệ thống | Xác định đúng, đầy đủ yêu cầu nghiệp vụ y tế? Mô tả yêu cầu chính xác? |
| Tuần 3–4 (Thiết kế) | Hoàn thành thiết kế hệ thống | Thiết kế kiến trúc 2 tầng (Swing + Spring Boot); Thiết kế giao diện; Thiết kế CSDL SQL Server | CSDL phù hợp với nghiệp vụ bệnh viện? Giao diện đúng yêu cầu? |
| Tuần 5–8 (Xây dựng) | Hoàn thành xây dựng các module | Xây dựng CSDL; Xây dựng các module chức năng; Tích hợp API | Đầy đủ chức năng? Code đúng thiết kế? API hoạt động ổn định? |
| Tuần 9–10 (Kiểm thử) | Hoàn thành kiểm thử phần mềm | Kiểm thử chức năng; Kiểm thử tích hợp; Báo cáo kiểm thử | Kiểm thử hết chức năng? Chất lượng đạt yêu cầu? Tích hợp hệ thống ổn định? |
| Tuần 11–12 (Bàn giao) | Kết thúc dự án và chuyển giao | Triển khai hệ thống; Viết hướng dẫn sử dụng; Bàn giao cho bệnh viện | Hệ thống hoạt động ổn định? Hướng dẫn dễ hiểu? Khách hàng hài lòng? |

---

## 5.3. Kế hoạch đảm bảo chất lượng sản phẩm và kế hoạch bàn giao

**Bảng 5.2: Bảng kế hoạch đảm bảo chất lượng**

| STT | Sản phẩm bàn giao | Thước đo chất lượng | Các hoạt động | Tần suất thực hiện |
|---|---|---|---|---|
| 1 | Tài liệu lập kế hoạch | Bàn giao 100% các bản kế hoạch đúng thời gian; Xác định đúng 100% phạm vi dự án; Mỗi thành viên được phân công rõ ràng | Trao đổi với bệnh viện; Đội dự án tổ chức họp bàn | 1 buổi/tuần |
| 2 | Module Quản lý Bệnh nhân | Thực hiện đầy đủ 100% chức năng: thêm, sửa, xóa, tìm kiếm bệnh nhân; Hỗ trợ đầy đủ nghiệp vụ tiếp nhận bệnh nhân của y tá | Xem xét tài liệu yêu cầu; Kiểm thử chức năng CRUD | Thường xuyên kiểm thử |
| 3 | Module Đo Sinh Hiệu | Lưu trữ chính xác các chỉ số: mạch, nhiệt độ, huyết áp, SpO2 vào CSDL; Cập nhật trạng thái lịch hẹn sang VITAL_DONE | Kiểm thử nhập liệu; So sánh dữ liệu lưu với dữ liệu nhập | Kiểm tra thường xuyên |
| 4 | Module Bệnh án Điện tử (5 tab) | Lưu đầy đủ thông tin 5 tab: khám lâm sàng, chẩn đoán, kê đơn, dặn dò, lịch sử; Tích hợp thành công với Spring Boot API | Kiểm thử từng tab; Kiểm thử tích hợp API POST/GET | Thường xuyên kiểm thử |
| 5 | Module Kê Đơn Thuốc | Tìm kiếm thuốc chính xác; Tính tổng tiền đúng; Lưu đơn thuốc vào CSDL sau khi lưu bệnh án | Kiểm thử chức năng kê đơn; Kiểm tra tính toán | Thường xuyên kiểm tra |
| 6 | Spring Boot API Server | API hoạt động ổn định trên port 8081; Thời gian phản hồi < 3 giây; Xử lý đúng các trường hợp lỗi (400, 404, 500) | Kiểm thử API bằng Postman; Kiểm thử tích hợp với Swing client | Thường xuyên kiểm thử |
| 7 | Hệ thống Đăng nhập & Phân quyền | Phân quyền đúng: Bác sĩ → DoctorDashboard, Y tá → PatientManagementFrame; Không cho phép truy cập trái phép | Kiểm thử đăng nhập với các role khác nhau | Thường xuyên kiểm tra |
| 8 | Hệ CSDL SQL Server | Đảm bảo lưu trữ toàn vẹn dữ liệu; Không mất dữ liệu khi rollback transaction; Hỗ trợ truy vấn nhanh với dữ liệu lớn | Test nhiều lần với bộ dữ liệu lớn; Kiểm tra transaction | Theo kỳ |
| 9 | Tài liệu hướng dẫn sử dụng | Mọi người dùng (bác sĩ, y tá) đều có thể dễ dàng sử dụng hệ thống sau khi đọc tài liệu | Xem lại tài liệu; Thử nghiệm với người dùng thực tế | Trước khi bàn giao |

---

# CHƯƠNG 6: QUẢN LÝ NHÂN LỰC

## 6.1. Xác định vị trí các cá nhân và nhóm phát triển dự án

**Bảng 6.1: Bảng xác định cá nhân nhóm và phát triển**

| Giai đoạn | Tên công việc | Công việc chi tiết | Nhân sự |
|---|---|---|---|
| **1** | **Lên kế hoạch dự án** | 1.1 Khảo sát tính khả thi của dự án | Nguyễn Công Sơn |
| | | 1.2 Khảo sát yêu cầu nghiệp vụ bệnh viện | Nguyễn Văn Quang |
| | | 1.3 Xây dựng tài liệu quản lý dự án | Nguyễn Công Sơn, Nguyễn Văn Quang |
| | | 1.4 Xây dựng bản kế hoạch đảm bảo chất lượng | Nguyễn Văn Quang |
| | | 1.5 Xây dựng bản kế hoạch quản lý cấu hình | Nguyễn Văn Phương |
| | | 1.6 Xây dựng bản kế hoạch quản lý rủi ro | Nguyễn Văn Danh |
| **2** | **Xác định yêu cầu** | 2.1 Xác định yêu cầu chung của hệ thống EMR | Nguyễn Công Sơn, Nguyễn Văn Quang |
| | | 2.2 Xác định yêu cầu của bác sĩ và y tá | Nguyễn Công Sơn, Nguyễn Văn Quang |
| | | 2.3 Xác định yêu cầu của hệ thống | Nguyễn Văn Danh |
| | | 2.3.1 Xác định yêu cầu cho từng chức năng | Nguyễn Văn Quang, Nguyễn Văn Danh |
| | | 2.3.2 Mô tả giao diện hệ thống | Nguyễn Công Sơn, Nguyễn Văn Quang |
| | | 2.4 Xác định các yêu cầu phi chức năng | Nguyễn Công Sơn, Nguyễn Văn Quang |
| **3** | **Phân tích hệ thống** | 3.1 Phân tích và đặc tả chức năng đăng nhập & phân quyền | Nguyễn Văn Danh |
| | | 3.2 Phân tích và đặc tả chức năng quản lý bệnh nhân | Nguyễn Văn Quang |
| | | 3.3 Phân tích và đặc tả chức năng đo sinh hiệu | Nguyễn Văn Quang |
| | | 3.4 Phân tích và đặc tả chức năng lập bệnh án điện tử | Nguyễn Văn Danh |
| | | 3.5 Phân tích và đặc tả chức năng kê đơn thuốc | Nguyễn Văn Danh |
| | | 3.6 Phân tích và đặc tả chức năng quản lý lịch hẹn | Nguyễn Văn Quang |
| | | 3.7 Phân tích và đặc tả chức năng báo cáo thống kê | Nguyễn Văn Danh |
| **4** | **Thiết kế hệ thống** | 4.1 Thiết kế kiến trúc 2 tầng (Swing + Spring Boot) | Nguyễn Văn Danh |
| | | 4.2 Thiết kế giao diện người dùng (UI/UX) | Nguyễn Công Sơn, Nguyễn Văn Danh |
| | | 4.2.1 Thiết kế giao diện chung | Nguyễn Công Sơn, Nguyễn Văn Danh |
| | | 4.2.2 Thiết kế giao diện từng chức năng | Nguyễn Văn Danh |
| | | 4.3 Thiết kế cơ sở dữ liệu SQL Server | Nguyễn Văn Danh |
| **5** | **Xây dựng hệ thống** | 5.1 Xây dựng cơ sở dữ liệu | Nguyễn Văn Danh |
| | | 5.2 Xây dựng các module | Nguyễn Văn Danh |
| | | 5.2.1 Xây dựng module đăng nhập & phân quyền | Nguyễn Văn Danh |
| | | 5.2.2 Xây dựng module quản lý bệnh nhân | Nguyễn Văn Danh |
| | | 5.2.3 Xây dựng module đo sinh hiệu | Nguyễn Văn Danh |
| | | 5.2.4 Xây dựng module bệnh án điện tử (5 tab) | Nguyễn Văn Danh |
| | | 5.2.5 Xây dựng module kê đơn thuốc | Nguyễn Văn Danh |
| | | 5.2.6 Xây dựng Spring Boot API Server | Nguyễn Văn Danh |
| | | 5.2.7 Xây dựng module báo cáo thống kê | Nguyễn Văn Danh |
| | | 5.3 Tích hợp các chức năng đã xây dựng | Nguyễn Văn Danh |
| **6** | **Kiểm thử phần mềm** | 6.1 Lập kế hoạch kiểm thử | Nguyễn Văn Phương |
| | | 6.2 Kiểm thử các chức năng của hệ thống | Nguyễn Văn Phương |
| | | 6.2.1 Kiểm thử module đăng nhập | Nguyễn Văn Phương |
| | | 6.2.2 Kiểm thử module quản lý bệnh nhân | Nguyễn Văn Phương |
| | | 6.2.3 Kiểm thử module đo sinh hiệu | Nguyễn Văn Phương |
| | | 6.2.4 Kiểm thử module bệnh án điện tử | Nguyễn Văn Phương |
| | | 6.2.5 Kiểm thử module kê đơn thuốc | Nguyễn Văn Phương |
| | | 6.2.6 Kiểm thử Spring Boot API | Nguyễn Văn Phương |
| | | 6.2.7 Kiểm thử module báo cáo thống kê | Nguyễn Văn Phương |
| | | 6.3 Kiểm thử tích hợp hệ thống | Nguyễn Văn Danh |
| | | 6.4 Lập báo cáo kiểm thử | Nguyễn Văn Phương, Nguyễn Công Sơn |
| **7** | **Kết thúc & bàn giao** | 7.1 Viết tài liệu hướng dẫn sử dụng | Nguyễn Công Sơn |
| | | 7.2 Mô phỏng hoạt động của hệ thống | Nguyễn Văn Danh |
| | | 7.3 Triển khai và bàn giao sản phẩm | Nguyễn Công Sơn, Nguyễn Văn Danh |

---

## 6.2. Quản lý tài nguyên con người

### 6.2.1. Các ràng buộc về con người

**Bảng 6.2: Bảng các thành viên của đội dự án**

| STT | Họ và tên | Vai trò |
|---|---|---|
| 1 | Nguyễn Công Sơn | Nhóm trưởng |
| 2 | Nguyễn Văn Quang | Thành viên |
| 3 | Nguyễn Văn Danh | Thành viên |
| 4 | Nguyễn Văn Phương | Thành viên |

**Quy tắc chung khi teamwork:**

- Phân chia công việc đều nhau và hợp lý, ưu tiên theo năng lực sở trường.
- Thảo luận công việc sôi nổi, tích cực trong khi làm việc nhóm.
- Mọi sự phân công đều được đưa ra họp bàn công khai và công bằng.

**Yêu cầu đối với các thành viên trong nhóm:**

- Nghiêm chỉnh chấp hành thực hiện công việc theo bản kế hoạch của dự án.
- Tích cực tham gia thảo luận, phát biểu ý kiến để dự án đạt kết quả tốt nhất.
- Bồi dưỡng khả năng chuyên môn (Java, Spring Boot, SQL Server) để hoàn thành vai trò trong dự án.
- Tham gia đầy đủ các buổi họp và làm việc. Không nghỉ quá 2 buổi/tuần.
- Nghỉ làm phải thông báo trưởng nhóm để sắp xếp công việc chạy đúng tiến độ.

**Truyền thông:**

- Trao đổi qua email, điện thoại, Zalo/Facebook.
- Họp nhóm khi cần và theo kế hoạch truyền thông.
- Thường xuyên liên hệ khi có vướng mắc trong quá trình làm việc.

**Hội họp:**

- Có mặt đầy đủ, đúng giờ các buổi họp nhóm dự án.
- Có công việc đột xuất cần báo cáo trưởng nhóm trước ít nhất 1 giờ trước khi họp.
- Tích cực bàn bạc và giải quyết vấn đề của dự án.
- Chấp hành, thực hiện đúng quyết định đã thống nhất trong cuộc họp.

---

### 6.2.2. Danh sách các vị trí dành cho dự án

**Bảng 6.3: Bảng danh sách các vị trí cần cho dự án**

| STT | Vị trí | Trách nhiệm | Kỹ năng yêu cầu | Số lượng |
|---|---|---|---|---|
| 1 | Giám đốc dự án (Lead) | Quản lý đội dự án, điều phối công việc, báo cáo tiến độ | Lãnh đạo, có kinh nghiệm quản lý dự án phần mềm | 1 |
| 2 | Kỹ sư phân tích thiết kế (BA) | Nhận thông tin từ bệnh viện, phân tích nghiệp vụ y tế, thiết kế luồng xử lý | Giao tiếp tốt, hiểu nghiệp vụ bệnh viện, thiết kế biểu đồ Use Case, UML | 1 |
| 3 | Lập trình viên (Coder) | Viết mã nguồn Java Swing, Spring Boot, tích hợp API | Thành thạo Java, Spring Boot, SQL Server, REST API | 1 |
| 4 | Người quản trị CSDL | Xây dựng, bảo trì và nâng cấp CSDL SQL Server | SQL Server 2019, thiết kế schema, tối ưu truy vấn | 1 |
| 5 | Kỹ sư quản lý cấu hình | Quản lý cấu hình dự án, kiểm soát phiên bản trên GitHub | Thành thạo Git/GitHub, quản lý branch, merge request | 1 |
| 6 | Kỹ sư kiểm tra chất lượng (Tester) | Kiểm tra các chức năng, viết testcase, lập báo cáo kiểm thử | Thông thạo kiểm thử phần mềm, có kinh nghiệm test ứng dụng Java và REST API | 1 |

---

### 6.2.3. Vị trí các thành viên trong dự án

**Bảng 6.4: Bảng các thành viên trong dự án**

| STT | Họ tên nhân viên | Vị trí |
|---|---|---|
| 1 | Nguyễn Công Sơn | Giám đốc dự án |
| 2 | Nguyễn Văn Quang | Kỹ sư phân tích thiết kế (BA) |
| 3 | Nguyễn Văn Danh | Người quản trị CSDL; Lập trình viên (Coder) |
| 4 | Nguyễn Văn Phương | Kỹ sư quản lý cấu hình; Kỹ sư kiểm tra chất lượng (Tester) |
