# CHƯƠNG 3. GIAO DIỆN ỨNG DỤNG

## 3.1. Giao diện trang Đăng nhập

Màn hình đăng nhập là điểm khởi đầu của ứng dụng, cho phép người dùng xác thực tài khoản. Giao diện bao gồm các thành phần chính:

- Logo và tên ứng dụng "Hidden Gem" hiển thị ở trung tâm phía trên.
- Dòng mô tả ngắn: "Khám phá những địa điểm thú vị ít ai biết đến".
- Trường nhập EMAIL và MẬT KHẨU với nút hiện/ẩn mật khẩu.
- Liên kết "Quên mật khẩu?" điều hướng sang màn hình khôi phục tài khoản.
- Nút "Đăng nhập" xử lý xác thực tài khoản.
- Liên kết "Chưa có tài khoản? Đăng ký ngay" điều hướng sang màn hình đăng ký.

*Hình 1: Giao diện trang Đăng nhập*

---

## 3.2. Giao diện trang Đăng ký

Màn hình đăng ký cho phép người dùng tạo tài khoản mới. Giao diện bao gồm:

- Logo và tiêu đề "Tạo tài khoản" hiển thị ở phía trên.
- Dòng mô tả: "Tham gia cộng đồng khám phá những địa điểm ẩn giấu".
- Bốn trường nhập liệu theo thứ tự:
  - TÊN NGƯỜI DÙNG
  - EMAIL
  - MẬT KHẨU (yêu cầu tối thiểu 6 ký tự)
  - XÁC NHẬN MẬT KHẨU
- Nút "Đăng ký" xử lý tạo tài khoản.
- Ghi chú đồng ý điều khoản dịch vụ và quyền riêng tư.
- Liên kết "Đã có tài khoản? Đăng nhập" điều hướng về màn hình đăng nhập.

*Hình 2: Giao diện trang Đăng ký*

---

## 3.3. Giao diện trang Quên mật khẩu

Màn hình hỗ trợ người dùng khôi phục quyền truy cập tài khoản. Giao diện bao gồm:

- Biểu tượng chìa khóa và tiêu đề "Quên mật khẩu?" hiển thị ở trung tâm.
- Dòng hướng dẫn: "Nhập email đăng ký, chúng tôi sẽ gửi liên kết đặt lại mật khẩu".
- Trường nhập địa chỉ email.
- Nút "Gửi liên kết" xử lý yêu cầu khôi phục.
- Liên kết "Quay lại đăng nhập" điều hướng về màn hình trước.

*Hình 3: Giao diện trang Quên mật khẩu*

---

## 3.4. Giao diện trang chủ (Home Feed)

Trang chủ là màn hình trung tâm hiển thị bảng tin địa điểm từ cộng đồng. Giao diện bao gồm:

- Tiêu đề "Hidden Gem" và thanh lọc nhanh với ba tùy chọn:
  - "Gần tôi" — lọc địa điểm theo vị trí GPS hiện tại.
  - "Tất cả" — hiển thị toàn bộ bài đăng.
  - "Quán cà phê" — lọc theo danh mục.
- Mỗi bài đăng địa điểm hiển thị dưới dạng thẻ card gồm:
  - Ảnh địa điểm và nhãn danh mục góc trên trái.
  - Thông tin người đăng: tên tài khoản và thời gian.
  - Tiêu đề, mô tả ngắn và các hashtag liên quan.
  - Địa chỉ GPS của địa điểm.
  - Thanh tương tác: Like, Bình luận, Bookmark và Chia sẻ.
- Nút "+" góc phải dưới để tạo bài đăng mới.
- Thanh điều hướng dưới cùng gồm 5 tab: Trang chủ, Bản đồ, Tìm kiếm, Thông báo, Hồ sơ.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 4: Giao diện trang chủ (Light Mode và Dark Mode)*

---

## 3.5. Giao diện trang Bản đồ

Màn hình bản đồ hiển thị trực quan toàn bộ địa điểm trên nền bản đồ tương tác. Giao diện bao gồm:

- Thẻ thông tin góc trên trái hiển thị tiêu đề "Bản đồ địa điểm" và tổng số địa điểm.
- Các Marker hình tròn phân biệt theo danh mục địa điểm được hiển thị trên bản đồ.
- Khi nhấn vào Marker, thông tin tóm tắt của địa điểm được hiển thị.
- Nút định vị góc phải cho phép căn chỉnh bản đồ về vị trí hiện tại của người dùng.
- Nút làm mới dữ liệu bản đồ.
- Hỗ trợ chế độ Light Mode và Dark Mode với nền bản đồ thay đổi tương ứng.

*Hình 5: Giao diện trang Bản đồ (Light Mode và Dark Mode)*

---

## 3.6. Giao diện trang Tìm kiếm

Màn hình tìm kiếm hỗ trợ người dùng khám phá địa điểm theo nhiều tiêu chí. Giao diện bao gồm:

- Thanh tìm kiếm với gợi ý "Tìm kiếm địa điểm, tag, khu vực...".
- Các nút lọc nhanh theo danh mục: Quán cà phê, Ẩm thực, Góc chụp ảnh.
- Mục "Tìm kiếm gần đây":
  - Hiển thị lịch sử các từ khóa đã tìm kiếm.
  - Nút "Xóa tất cả" để xóa lịch sử tìm kiếm.
- Mục "Xu hướng":
  - Hiển thị các hashtag đang được tìm kiếm nhiều nhất.
- Mục "Phổ biến gần bạn":
  - Liệt kê các địa điểm được yêu thích nhiều nhất trong khu vực hiện tại.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 6: Giao diện trang Tìm kiếm (Light Mode và Dark Mode)*

---

## 3.7. Giao diện trang Thông báo

Màn hình thông báo tổng hợp toàn bộ hoạt động tương tác liên quan đến tài khoản. Giao diện bao gồm:

- Hai tab phân loại: "Tất cả" và "Chưa đọc" kèm số lượng thông báo chưa đọc.
- Nút "Đọc tất cả" để đánh dấu toàn bộ thông báo là đã đọc.
- Mỗi thông báo hiển thị:
  - Ảnh đại diện người dùng liên quan.
  - Nội dung hành động (ví dụ: thích bài viết, theo dõi tài khoản).
  - Thời gian xảy ra hoạt động.
  - Chấm tròn đánh dấu thông báo chưa đọc.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 7: Giao diện trang Thông báo (Light Mode và Dark Mode)*

---

## 3.8. Giao diện trang Hồ sơ cá nhân

Màn hình hồ sơ hiển thị thông tin tài khoản và các bài đăng của người dùng. Giao diện bao gồm:

- Tên tài khoản (@username) và biểu tượng cài đặt ở góc phải (khi xem hồ sơ bản thân).
- Ảnh đại diện hình tròn được viền màu nổi bật.
- Ba chỉ số thống kê: số Bài đăng, số Follower và số Following.
- Tên hiển thị, vị trí và phần giới thiệu bản thân.
- Hai nút hành động:
  - "Chỉnh sửa hồ sơ" và nút Bookmark khi xem hồ sơ bản thân.
  - "Đang theo dõi" và nút Nhắn tin khi xem hồ sơ người dùng khác.
- Hai tab nội dung:
  - "Bài đăng": hiển thị lưới ảnh các địa điểm đã đăng.
  - "Đã lưu": hiển thị các địa điểm đã bookmark.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 8: Giao diện trang Hồ sơ cá nhân (Light Mode và Dark Mode)*

---

## 3.9. Giao diện trang Đăng địa điểm mới

Màn hình tạo bài đăng cho phép người dùng đóng góp địa điểm mới vào cộng đồng. Giao diện bao gồm:

- Tiêu đề "Đăng địa điểm mới" và nút "Bản nháp" để lưu tạm thời.
- Khu vực tải ảnh: hỗ trợ tối đa 10 ảnh.
- Trường TIÊU ĐỀ: nhập tên địa điểm, tối đa 200 ký tự.
- Trường DANH MỤC: chọn từ các nhãn có sẵn như Quán cà phê, Ẩm thực, Góc chụp ảnh.
- Trường MÔ TẢ: ô nhập liệu nhiều dòng để chia sẻ trải nghiệm về địa điểm.
- Trường ĐỊA CHỈ: nhập thủ công hoặc chọn vị trí trực tiếp trên bản đồ.

*Hình 9: Giao diện trang Đăng địa điểm mới*

---

## 3.10. Giao diện trang Bình luận

Màn hình bình luận quản lý các phản hồi của cộng đồng về một địa điểm. Giao diện bao gồm:

- Tiêu đề "Bình luận" ở đầu màn hình.
- Mỗi bình luận hiển thị:
  - Ảnh đại diện và tên tài khoản người bình luận.
  - Nội dung bình luận và thời gian đăng.
  - Nút Like và nút "Trả lời".
- Ô nhập liệu "Viết bình luận (@để nhắc đến)..." ở cuối màn hình.
- Nút gửi bình luận để xác nhận đăng tải.
- Hỗ trợ tính năng @mention người dùng khác trong bình luận.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 10: Giao diện trang Bình luận (Light Mode và Dark Mode)*

---

## 3.11. Giao diện trang Bộ sưu tập

Màn hình bộ sưu tập cho phép người dùng quản lý các địa điểm đã lưu theo nhóm. Giao diện bao gồm:

- Nút "Tạo bộ sưu tập mới" ở đầu trang.
- Mỗi bộ sưu tập hiển thị dưới dạng thẻ card gồm:
  - Lưới ảnh thumbnail 4 ô đại diện cho các địa điểm trong bộ sưu tập.
  - Tên bộ sưu tập.
  - Số lượng địa điểm đã lưu.
  - Trạng thái hiển thị: Riêng tư hoặc Công khai.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 11: Giao diện trang Bộ sưu tập (Light Mode và Dark Mode)*

---

## 3.12. Giao diện trang Chỉnh sửa hồ sơ

Màn hình chỉnh sửa hồ sơ cho phép người dùng cập nhật thông tin cá nhân. Giao diện bao gồm:

- Ảnh đại diện hình tròn và liên kết "Đổi ảnh đại diện".
- Trường TÊN NGƯỜI DÙNG: chỉnh sửa tên tài khoản.
- Trường GIỚI THIỆU: nhập tiểu sử cá nhân, tối đa 150 ký tự, có bộ đếm ký tự.
- Trường THÀNH PHỐ: nhập vị trí hiện tại của người dùng.
- Nút "Lưu thay đổi" để xác nhận cập nhật thông tin.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 12: Giao diện trang Chỉnh sửa hồ sơ (Light Mode và Dark Mode)*

---

## 3.13. Giao diện trang Cài đặt

Màn hình cài đặt được tổ chức theo các nhóm chức năng rõ ràng. Giao diện bao gồm:

- Nhóm TÀI KHOẢN:
  - Chỉnh sửa hồ sơ: điều hướng sang màn hình chỉnh sửa hồ sơ.
  - Đổi mật khẩu: mở hộp thoại nhập mật khẩu hiện tại và mật khẩu mới.
  - Email: hiển thị địa chỉ email hiện tại của tài khoản.
- Nhóm THÔNG BÁO:
  - Push Notification: toggle bật/tắt thông báo đẩy.
- Nhóm QUYỀN RIÊNG TƯ:
  - Tài khoản riêng tư: toggle — khi bật, chỉ follower mới xem được bài đăng.
  - Danh sách chặn: điều hướng sang màn hình quản lý danh sách chặn.
- Nhóm GIAO DIỆN:
  - Dark Mode: toggle bật/tắt chế độ tối.
- Nhóm THÔNG TIN:
  - Giới thiệu: mở hộp thoại giới thiệu ứng dụng.
  - Điều khoản dịch vụ: mở hộp thoại điều khoản sử dụng.
  - Chính sách quyền riêng tư: mở hộp thoại chính sách bảo mật.
- Nút "Đăng xuất" và nút "Xóa tài khoản" ở cuối trang.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 13: Giao diện trang Cài đặt (Dark Mode)*

---

## 3.14. Giao diện trang Danh sách chặn

Màn hình quản lý các tài khoản mà người dùng đã thực hiện thao tác chặn. Giao diện bao gồm:

- Tiêu đề "Danh sách chặn" ở đầu màn hình.
- Trạng thái trống khi chưa có tài khoản nào bị chặn:
  - Biểu tượng cấm hiển thị ở trung tâm màn hình.
  - Tiêu đề "Danh sách chặn trống".
  - Mô tả: "Những người bạn chặn sẽ xuất hiện ở đây. Khi bạn chặn ai đó, họ sẽ không thể xem hồ sơ hoặc các địa điểm của bạn."
- Khi có tài khoản bị chặn, mỗi mục hiển thị thông tin tài khoản và nút bỏ chặn.
- Hỗ trợ chế độ Light Mode và Dark Mode.

*Hình 14: Giao diện trang Danh sách chặn (Light Mode và Dark Mode)*

---

## 3.15. Giao diện các màn hình thông tin

Ứng dụng cung cấp ba màn hình thông tin dạng hộp thoại, được truy cập từ trang Cài đặt. Mỗi màn hình có nút "Đóng" để quay lại màn hình trước.

### 3.15.1. Giới thiệu về Hidden Gem

- Mô tả sứ mệnh của ứng dụng.
- Trình bày ba giá trị cốt lõi:
  - Tìm kiếm tọa độ lý tưởng: hỗ trợ khám phá quán cà phê specialty, góc chụp ảnh nghệ thuật và khung cảnh thiên nhiên.
  - Kết nối cộng đồng: cho phép chia sẻ địa điểm và theo dõi người dùng có cùng sở thích.
  - Trải nghiệm du lịch bền vững: khuyến khích tôn trọng thiên nhiên và cộng đồng địa phương.

### 3.15.2. Điều khoản dịch vụ

- Quy định về trách nhiệm bảo mật tài khoản của người dùng.
- Tiêu chuẩn nội dung được phép đăng tải trên nền tảng.
- Quyền hạn của ứng dụng trong việc kiểm duyệt và xử lý nội dung vi phạm.

### 3.15.3. Chính sách quyền riêng tư

- Phạm vi thu thập thông tin: email, tên người dùng và dữ liệu GPS khi được cấp quyền.
- Cam kết không chia sẻ dữ liệu cá nhân với bên thứ ba vì mục đích thương mại.
- Cơ chế bảo mật: mật khẩu được mã hóa một chiều bằng thuật toán BCrypt trước khi lưu vào cơ sở dữ liệu.

*Hình 15: Giao diện các màn hình thông tin (Giới thiệu, Điều khoản, Chính sách)*
