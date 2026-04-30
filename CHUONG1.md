# CHƯƠNG 1: GIỚI THIỆU ĐỀ TÀI

## 1.1 Lý do chọn đề tài

Trong những năm gần đây, ngành dịch vụ làm đẹp — đặc biệt là các salon tóc, barber shop và spa — đang phát triển mạnh mẽ tại Việt Nam. Nhu cầu chăm sóc ngoại hình ngày càng tăng cao, kéo theo sự xuất hiện của hàng nghìn cơ sở dịch vụ lớn nhỏ trên khắp cả nước. Tuy nhiên, phần lớn các salon hiện nay vẫn tiếp nhận lịch hẹn theo phương thức truyền thống: khách hàng gọi điện, nhắn tin hoặc đến trực tiếp để đặt chỗ. Cách làm này tồn tại nhiều bất cập rõ ràng.

Về phía khách hàng, họ khó biết salon nào còn chỗ trống, phải mất thời gian liên hệ thủ công, không có thông tin rõ ràng về dịch vụ, giá cả và nhân viên phục vụ trước khi đến. Về phía chủ salon, việc quản lý lịch hẹn thủ công dễ xảy ra tình trạng đặt trùng giờ, không có công cụ theo dõi doanh thu và đánh giá chất lượng dịch vụ một cách hệ thống, dẫn đến hiệu quả vận hành thấp.

Trước thực trạng đó, nhóm nhận thấy nhu cầu cấp thiết cần có một nền tảng đặt lịch trực tuyến dành riêng cho lĩnh vực salon và barber spa — nơi khách hàng có thể tìm kiếm, so sánh và đặt lịch dễ dàng, trong khi chủ salon có đầy đủ công cụ để vận hành và quản lý hiệu quả.

Đề tài **"Website Đặt Lịch Cắt Tóc & Làm Đẹp (Barber & Spa) bằng ngôn ngữ mã nguồn mở PHP"** được chọn với các lý do cụ thể sau:

**Thứ nhất, tính thực tiễn cao.** Bài toán đặt lịch trực tuyến là nhu cầu có thật, đang được nhiều doanh nghiệp trong ngành tìm kiếm giải pháp. Hệ thống xây dựng được có thể áp dụng trực tiếp vào thực tế với chi phí thấp.

**Thứ hai, phạm vi phù hợp với mục tiêu học tập.** Hệ thống bao gồm đầy đủ các nghiệp vụ phổ biến trong phát triển web như xác thực người dùng, phân quyền theo vai trò, quản lý dữ liệu quan hệ, tích hợp thanh toán và gửi email — đây là những kiến thức cốt lõi của môn Lập trình Web.

**Thứ ba, cơ hội áp dụng kiến thức toàn diện.** Đề tài yêu cầu vận dụng đồng thời kiến thức về lập trình PHP, thiết kế cơ sở dữ liệu quan hệ, bảo mật ứng dụng web và xây dựng giao diện người dùng — giúp nhóm củng cố và kết nối các kiến thức đã học.

**Thứ tư, tính mở rộng tốt.** Hệ thống được thiết kế theo kiến trúc rõ ràng, có thể phát triển thêm các tính năng như thông báo thời gian thực, ứng dụng di động hay tích hợp bản đồ trong tương lai.

---

## 1.2 Công cụ và công nghệ sử dụng

### 1.2.1 Công nghệ Backend và Cơ sở dữ liệu

Hệ thống được xây dựng hoàn toàn bằng **PHP phiên bản 8.0 trở lên** — một trong những ngôn ngữ lập trình phía máy chủ phổ biến nhất thế giới, chiếm hơn 77% các website hiện nay. PHP 8 mang lại nhiều cải tiến đáng kể so với các phiên bản trước như hiệu năng cao hơn nhờ JIT Compiler, hỗ trợ Union Types, Named Arguments và Match Expression giúp mã nguồn rõ ràng và an toàn hơn. Toàn bộ dự án áp dụng chế độ kiểm tra kiểu dữ liệu nghiêm ngặt (`declare(strict_types=1)`), giúp phát hiện lỗi sớm ngay trong quá trình phát triển.

Điểm đặc biệt là dự án không sử dụng framework mà tự xây dựng kiến trúc **MVC (Model - View - Controller) thuần**. Trong đó, tầng Model chịu trách nhiệm truy vấn và thao tác dữ liệu; tầng View chứa các template HTML nhận dữ liệu để hiển thị; tầng Controller xử lý logic nghiệp vụ và điều phối giữa Model và View. Một front controller trung tâm nhận toàn bộ request, phân tích đường dẫn bằng biểu thức chính quy và điều hướng đến đúng Controller tương ứng. Cách tiếp cận này giúp nhóm hiểu sâu cơ chế hoạt động nội tại của một ứng dụng web thay vì phụ thuộc vào "magic" của framework.

Kết nối cơ sở dữ liệu sử dụng **PDO (PHP Data Objects)** với mẫu thiết kế Singleton, đảm bảo chỉ tạo một kết nối duy nhất trong suốt vòng đời của mỗi request. Toàn bộ truy vấn đều dùng prepared statements để ngăn chặn tấn công SQL Injection.

Hệ quản trị cơ sở dữ liệu sử dụng **MySQL 8.0+ hoặc MariaDB 10.x+** với 11 bảng chính, được thiết kế với encoding utf8mb4 hỗ trợ đầy đủ tiếng Việt, InnoDB Engine hỗ trợ transaction và ràng buộc khóa ngoại, index tối ưu trên các cột thường xuyên truy vấn và FULLTEXT Index phục vụ tìm kiếm toàn văn. Đặc biệt, cơ chế transaction kết hợp khóa hàng (`SELECT ... FOR UPDATE`) được áp dụng trong luồng tạo lịch hẹn để ngăn chặn race condition — hai khách đặt cùng một khung giờ của cùng một nhân viên trong cùng thời điểm.

### 1.2.2 Công nghệ Frontend, Giao diện và Tích hợp bên thứ ba

Giao diện người dùng được xây dựng bằng bộ ba công nghệ chuẩn của web hiện đại. **HTML5** cung cấp các thẻ ngữ nghĩa và input type hiện đại giúp trải nghiệm người dùng tốt hơn trên mọi thiết bị. **CSS3** với Flexbox, Grid Layout, transition và animation tạo giao diện hiện đại và mượt mà. **JavaScript ES6+** xử lý các tương tác phía client như gọi API gợi ý tìm kiếm theo thời gian thực, đếm ngược thời gian giữ slot và tính tổng tiền động khi người dùng chọn dịch vụ.

**Bootstrap 5** được tích hợp qua CDN, là framework CSS phổ biến nhất hiện nay do Twitter phát triển. Bootstrap cung cấp hệ thống lưới 12 cột responsive và hơn 30 component UI sẵn có, giúp giao diện hiển thị tốt và nhất quán trên mọi kích thước màn hình mà không cần viết CSS từ đầu.

**Chart.js** là thư viện JavaScript mã nguồn mở chuyên vẽ biểu đồ, được dùng để hiển thị các thống kê trực quan trên dashboard: biểu đồ đường thể hiện số lượng lịch hẹn theo 7 ngày gần nhất và biểu đồ cột thể hiện doanh thu theo 6 tháng gần nhất, áp dụng cho cả trang quản trị hệ thống lẫn trang quản lý của chủ salon.

Về tích hợp bên thứ ba, hệ thống sử dụng hai thư viện và dịch vụ chính. **PHPMailer** (phiên bản 7.0 trở lên, cài đặt qua Composer) là thư viện gửi email mạnh mẽ và phổ biến nhất trong hệ sinh thái PHP, hỗ trợ giao thức SMTP với mã hóa TLS/SSL. Trong dự án, PHPMailer được dùng để gửi email đặt lại mật khẩu kèm đường dẫn có thời hạn 15 phút và email xác thực tài khoản sau khi đăng ký. **VNPay** là cổng thanh toán trực tuyến hàng đầu tại Việt Nam, hỗ trợ thẻ ATM nội địa, thẻ quốc tế Visa/Mastercard và ví điện tử. Dự án tích hợp môi trường Sandbox của VNPay với chữ ký số HMAC-SHA512 và cơ chế kiểm tra giao dịch trùng lặp để tránh xử lý thanh toán hai lần.

### 1.2.3 Môi trường phát triển và Bảo mật ứng dụng

Về môi trường phát triển, dự án sử dụng **XAMPP** — gói phần mềm mã nguồn mở tích hợp sẵn Apache, MySQL và PHP, giúp dựng môi trường phát triển cục bộ trên Windows nhanh chóng mà không cần cấu hình phức tạp. **Composer** là trình quản lý dependency chuẩn của PHP, cho phép khai báo và tự động tải các thư viện cần dùng, đảm bảo môi trường nhất quán giữa các thành viên. **phpMyAdmin** hỗ trợ quản lý cơ sở dữ liệu qua giao diện web trực quan. **Git** được dùng để quản lý phiên bản mã nguồn và phối hợp làm việc nhóm.

Về bảo mật, hệ thống áp dụng đồng bộ nhiều lớp bảo vệ theo chuẩn thực tiễn tốt nhất. Mật khẩu được mã hóa bằng thuật toán **bcrypt** — thuật toán băm một chiều không thể giải mã ngược, được khuyến nghị bởi OWASP. **CSRF Token** được tạo ngẫu nhiên và kiểm tra trên toàn bộ form POST, ngăn chặn tấn công giả mạo yêu cầu. Session ID được tái tạo sau mỗi lần đăng nhập thành công, cookie phiên được đặt httponly và SameSite. Sau 5 lần nhập sai mật khẩu liên tiếp, tài khoản bị khóa tạm thời 30 phút để ngăn chặn tấn công brute force. Hệ thống phân quyền theo ba vai trò riêng biệt — quản trị viên, chủ salon và khách hàng — với kiểm tra quyền truy cập ở đầu mỗi action. Mọi thao tác trên lịch hẹn và đánh giá đều xác minh tài nguyên thuộc về đúng người dùng hiện tại, ngăn chặn tấn công IDOR.
