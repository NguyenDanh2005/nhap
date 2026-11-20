# 📖 HƯỚNG DẪN KHỞI CHẠY VÀ SỬ DỤNG SÀN GIAO DỊCH NFT (METAMASK + WEB3.JS)

> 💡 **MÔI TRƯỜNG GIẢ LẬP (LOCAL TESTNET):**
> Dự án chạy hoàn toàn trên mạng Blockchain cục bộ **Hardhat Localnet (127.0.0.1:8545)** với **ETH giả lập** và **NFT thử nghiệm**, không sử dụng tiền thật. Mọi giao dịch được xác nhận và ký trực tiếp thông qua ví **MetaMask** chuẩn dApp Web3.

---

## 📑 MỤC LỤC
1. [Kiến trúc & Công nghệ dự án](#1-kiến-trúc--công-nghệ-dự-án)
2. [Bảng thông tin 3 Tài khoản Giả lập mặc định](#2-bảng-thông-tin-3-tài-khoản-giả-lập-mặc-định)
3. [Các bước khởi chạy hệ thống (3 Terminal)](#3-các-bước-khởi-chạy-hệ-thống-3-terminal)
4. [Hướng dẫn cấu hình & Kết nối MetaMask](#4-hướng-dẫn-cấu-hình--kết-nối-metamask)
5. [Quy trình kiểm thử các chức năng qua MetaMask](#5-quy-trình-kiểm-thử-các-chức-năng-qua-metamask)
6. [Cách xử lý lỗi Nonce khi khởi động lại node](#6-cách-xử-lý-lỗi-nonce-khi-khởi-động-lại-node)
7. [Kịch bản dòng lệnh Web3.js & Kiểm thử tự động (Unit Tests)](#7-kịch-bản-dòng-lệnh-web3js--kiểm-thử-tự-động-unit-tests)

---

## 1. KIẾN TRÚC & CÔNG NGHỆ DỰ ÁN

- **Smart Contracts (Solidity ^0.8.24, OpenZeppelin Contracts v5):**
  - [NFTMarketplace.sol](./contracts/NFTMarketplace.sol): Quản lý đăng bán (`listNFT`), mua (`buyNFT`), hủy bán (`cancelListing`), tính phí giao dịch sàn, cho phép chủ sàn đổi tỷ lệ phí (`setFeePercent`) và rút phí về ví (`withdrawFees`).
  - [MyNFT.sol](./contracts/MyNFT.sol): Hợp đồng NFT chuẩn ERC-721, **phân bổ sẵn 10,000 NFT** cho từng tài khoản mà không tốn gas tạo ban đầu.
- **Thư viện kết nối Blockchain:** **Web3.js v4** & **Ethers.js v6**.
- **Backend API:** Node.js, Express, TypeScript (`http://localhost:3000`).
- **Frontend dApp:** React 19, Vite, Tailwind CSS, Lucide Icons (`http://localhost:5173`).

---

## 2. BẢNG THÔNG TIN 3 TÀI KHOẢN GIẢ LẬP MẶC ĐỊNH

Các tài khoản này được tạo cố định từ Hardhat Node. Mỗi tài khoản có sẵn **10,000 ETH** và **10,000 NFT**:

| Vai trò | Tên tài khoản | Địa chỉ Ví (Public Address) | Khóa riêng tư (Private Key nhập vào MetaMask) | Kho NFT có sẵn |
| :--- | :--- | :--- | :--- | :--- |
| 👑 **Chủ Sàn** | Account #0 (Owner) | `0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266` | `0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80` | **10,000 NFT** (#1 -> #10,000) |
| 👤 **Người dùng 1** | Alice (User 1) | `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` | `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d` | **10,000 NFT** (#10,001 -> #20,000) |
| 👤 **Người dùng 2** | Bob (User 2) | `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC` | `0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a` | **10,000 NFT** (#20,001 -> #30,000) |

> 🔑 **Mẹo:** Trên đầu trang web dApp có sẵn nút màu vàng **"🔑 3 Tài Khoản Mẫu (Private Keys)"** giúp bạn copy 1-click mà không cần quay lại file này.

---

## 3. CÁC BƯỚC KHỞI CHẠY HỆ THỐNG (3 TERMINAL)

Mở khu vực Terminal tại thư mục gốc `d:\NFT-Marketplace`:

### 🖥️ Bước 1: Khởi động Blockchain giả lập (Terminal 1)
```powershell
npm run chain
```
> *Lệnh này khởi động mạng Hardhat node tại `http://127.0.0.1:8545` (Chain ID `31337`). Giữ cửa sổ này chạy liên tục.*

---

### 📦 Bước 2: Triển khai Smart Contract (Terminal 2)
Bấm dấu **`+`** ở góc phải khu vực Terminal để mở tab PowerShell thứ hai, chạy:
```powershell
npm run deploy
```
> *Lệnh này sẽ nạp Smart Contract `NFTMarketplace` và `MyNFT` vào node, tự động nạp 10,000 NFT cho mỗi tài khoản và lưu địa chỉ vào `frontend/src/contracts.json`.*

*(Tùy chọn: Sau khi deploy xong, bạn có thể gõ tiếp lệnh khởi động backend API `
npm run backend:dev` ở tab này nếu cần dùng REST API).*

---

### 🌐 Bước 3: Khởi động Giao diện Web Frontend (Terminal 3)
Mở thêm một tab PowerShell thứ 3 và chạy:
```powershell
npm run frontend:dev
```
- Truy cập trình duyệt tại: **`http://localhost:5173`**

---

## 4. HƯỚNG DẪN CẤU HÌNH & KẾT NỐI METAMASK

### 1. Thêm mạng Hardhat Localnet vào MetaMask:
- Bấm nút **"Kết nối Ví MetaMask"** trên góc phải trang web.
- Nếu MetaMask đang ở mạng khác, website sẽ hiện nút: **"Chuyển mạng ngay trên MetaMask"**. Bấm vào nút này, MetaMask sẽ tự động hiện popup thêm mạng **Hardhat Localnet** (`http://127.0.0.1:8545`, Chain ID `31337`) mà bạn không cần nhập tay.

### 2. Nhập 3 tài khoản mẫu vào MetaMask:
1. Mở tiện ích MetaMask > Bấm vào menu chọn tài khoản ở trên cùng.
2. Chọn **"Thêm tài khoản hoặc ví phần cứng"** > Chọn **"Nhập tài khoản" (Import account)**.
3. Dán chuỗi **Private Key** của từng tài khoản ở bảng Mục 2 vào và bấm **Nhập**.
4. Thực hiện cho cả 3 tài khoản để chuyển đổi qua lại thuận tiện khi test.

---

## 5. QUY TRÌNH KIỂM THỬ CÁC CHỨC NĂNG QUA METAMASK

### 🔹 Kịch bản 1: Người dùng 1 (Alice) đăng bán NFT
1. Trên MetaMask, chuyển sang tài khoản **Người dùng 1 (Alice - 0x7099...79C8)**.
2. Trên web, chuyển sang tab **"Kho NFT của tôi"**:
   - Bạn sẽ thấy có sẵn **10,000 NFT sở hữu** (Token ID từ `#10,001` đến `#20,000`).
3. Chọn thẻ NFT `#10001` và bấm nút **"Đăng bán"** (hoặc dùng ô Đăng bán nhanh: nhập Token ID `10001`, giá `1.5` ETH) > Bấm **"Đăng bán ngay"**.
4. **Xác nhận qua MetaMask:**
   - **Lần 1 (nếu là lần đầu):** Popup MetaMask yêu cầu Phê duyệt cấp quyền (`setApprovalForAll`) > Bấm **Xác nhận**.
   - **Lần 2:** Popup MetaMask yêu cầu Ký giao dịch đăng bán (`listNFT`) > Bấm **Xác nhận**.
5. Thông báo *Đăng bán thành công! 🎉* xuất hiện, NFT được đưa lên sàn.

---

### 🔹 Kịch bản 2: Người dùng 2 (Bob) mua NFT
1. Trên MetaMask, chuyển sang tài khoản **Người dùng 2 (Bob - 0x3C44...93BC)**.
2. Trang web tự động nhận diện ví Bob và cập nhật số dư **10,000 ETH**.
3. Tại tab **"Khám phá Sàn"**, bạn sẽ thấy thẻ NFT `#10001` do Alice đăng bán với giá `1.5 ETH`.
4. Bấm nút **"Mua ngay"**:
   - Popup MetaMask bật lên yêu cầu thanh toán `1.5 ETH` + phí gas.
   - Bấm **Xác nhận** trên MetaMask.
5. Giao dịch thành công:
   - NFT `#10001` được chuyển về tab **Kho NFT của tôi** của Bob.
   - Alice nhận được tiền bán (`1.4625 ETH` - đã trừ 2.5% phí sàn).
   - Quỹ sàn tích lũy được `0.0375 ETH` phí giao dịch.

---

### 🔹 Kịch bản 3: Chủ sàn xem phí, đổi % phí và rút phí về ví
1. Trên MetaMask, chuyển sang tài khoản **Chủ Sàn (Owner - 0xf39F...2266)**.
2. Bấm vào tab **"Quản trị sàn (Chủ sàn)"**:
   - Nhãn màu vàng **"BẠN LÀ CHỦ SÀN"** xuất hiện.
   - Mục **"Phí tích lũy có thể rút"** hiển thị số ETH phí sàn vừa thu được.
3. **Thử đổi tỷ lệ phí sàn:**
   - Nhập `% phí mới`: ví dụ `5` (tương ứng 5%) > Bấm **"Lưu Tỷ Lệ Phí Mới"**.
   - Popup MetaMask bật lên > Bấm **Xác nhận** > Tỷ lệ phí được cập nhật thành 5%.
4. **Thử rút phí về ví:**
   - Bấm nút **"Rút toàn bộ phí về ví"**.
   - Popup MetaMask bật lên > Bấm **Xác nhận** > Toàn bộ ETH phí sàn tích lũy được chuyển thẳng về ví MetaMask của Chủ sàn!

---

### 🔹 Kịch bản 4: Người bán hủy tin đăng bán
1. Chuyển MetaMask về ví người bán (Alice hoặc Chủ sàn).
2. Đăng bán 1 NFT mới (ví dụ Token `#10002`).
3. Tại tab **"Khám phá Sàn"**, trên thẻ NFT bạn vừa đăng sẽ có nút màu đỏ **"Hủy bán"**.
4. Bấm **"Hủy bán"** > Xác nhận trên popup MetaMask > Lệnh bán bị hủy và NFT được hoàn lại kho cá nhân.

---

## 6. CÁCH XỬ LÝ LỖI NONCE KHI KHỞI ĐỘNG LẠI NODE

Khi bạn tắt và khởi động lại `npm run chain`, blockchain sẽ quay về block 0, nhưng MetaMask vẫn lưu lịch sử số Nonce cũ dẫn đến lỗi:
> `MetaMask - RPC Error: Nonce too high. Expected nonce to be 4 but got 12.`

**Cách xử lý trong 5 giây:**
1. Mở MetaMask > Bấm vào **menu 3 chấm `...`** ở góc trên bên phải > Chọn **Cài đặt (Settings)**.
2. Chọn thẻ **Nâng cao (Advanced)**.
3. Cuộn xuống bấm nút: **"Xóa dữ liệu tab hoạt động"** *(hoặc **"Clear activity and nonce data"**)* > Bấm **Xóa**.
*(Thao tác này chỉ xóa cache bộ đếm bị lệch, không ảnh hưởng đến tài khoản).*

---

## 7. KỊCH BẢN DÒNG LỆNH WEB3.JS & KIỂM THỬ TỰ ĐỘNG (UNIT TESTS)

### 1. Kiểm thử dòng lệnh qua Web3.js:
```powershell
npm run demo:web3
```
*Script dùng thư viện Web3.js v4 đọc số dư, kho 10,000 NFT và tỷ lệ phí sàn.*

### 2. Các kịch bản CLI giao dịch mẫu:
- Đăng bán NFT bằng script: `npm run demo:list`
- Mua NFT bằng script: `npm run demo:buy`
- Hủy lệnh bán bằng script: `npm run demo:cancel`
- Rút phí sàn bằng script: `npm run demo:withdraw`

### 3. Chạy 10 bài kiểm thử hợp đồng tự động:
```powershell
npm test
```
*Tất cả 10 bài unit test kiểm tra toàn bộ logic phân bổ 10,000 NFT, đăng bán, mua, tính phí, rút phí và phân quyền đều đạt 100% PASS.*
