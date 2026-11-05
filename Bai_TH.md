# BÀI TẬP TỔNG HỢP: RÀ SOÁT AN TOÀN THÔNG TIN TRƯỚC KHI BÀN GIAO DỰ ÁN SMARTCAMPUS

## PHẦN 1 – NHẬN DIỆN RỦI RO VÀ XỬ LÝ SỰ CỐ

### Câu 1. Tình huống 1

Đây là hình thức **Phishing kết hợp Typosquatting**.

Dấu hiệu giả mạo:

* Email yêu cầu nhập lại mật khẩu để mở khóa tài khoản.
* Link `githuh-security.com` giả tên miền GitHub.
* Tên miền viết sai gần giống `github.com` để đánh lừa người dùng.

### Câu 2. Tình huống 2

Đây là cạm bẫy **Mã độc Crack (Malware)**.

Yêu cầu tắt Windows Defender rất nguy hiểm vì làm giảm khả năng bảo vệ máy tính, tạo điều kiện cho virus và mã độc xâm nhập, đánh cắp dữ liệu.

### Câu 3. Áp dụng Quy tắc 5 KHÔNG

1. Không bấm vào link lạ.
2. Không tải file không rõ nguồn gốc.
3. Không cung cấp mật khẩu hoặc mã OTP cho người khác.
4. Không tắt phần mềm bảo vệ máy tính.
5. Không chủ quan trước email và tin nhắn đáng ngờ.

Áp dụng:

* Tình huống 1: Không bấm link lạ, không nhập mật khẩu.
* Tình huống 2: Không tải phần mềm crack, không tắt Windows Defender.

### Câu 4. Quy trình Cấp cứu 4 Bước

1. **Ngắt kết nối:** Tắt Wi-Fi và rút dây mạng.
2. **Báo cáo:** Thông báo cho trưởng nhóm hoặc người phụ trách kỹ thuật.
3. **Quét và xử lý:** Kiểm tra, cách ly và xóa mã độc.
4. **Khôi phục:** Đổi mật khẩu trên thiết bị an toàn, thu hồi phiên đăng nhập và kiểm tra lại máy tính.

\---

## PHẦN 2 – CHUYỂN SANG PASSWORD MANAGER

### Câu 1. Điều gì xảy ra nếu email nhóm bị lộ mật khẩu?

Hacker có thể dùng mật khẩu đó để đăng nhập vào GitHub và Vercel vì cả 3 tài khoản dùng chung mật khẩu.

Đây là kiểu tấn công **Credential Stuffing**.

### Câu 2. Vì sao Zero-Knowledge giúp bảo vệ dữ liệu?

Zero-Knowledge là kiến trúc mà Bitwarden không thể đọc mật khẩu của người dùng.

Dữ liệu được mã hóa trước khi gửi lên máy chủ. Nếu hacker tấn công máy chủ, họ chỉ lấy được dữ liệu đã mã hóa mà không có khóa giải mã.

### Câu 3. Cấu hình Generator

|Thông số|Giá trị|
|-|-|
|Độ dài|24 ký tự|
|Chữ hoa (A-Z)|Có|
|Chữ thường (a-z)|Có|
|Chữ số (0-9)|Có|
|Ký tự đặc biệt|Có|

Tạo 3 mật khẩu khác nhau cho GitHub, Vercel và Email nhóm. Lưu vào Bitwarden.

\---

## PHẦN 3 – KÍCH HOẠT 2FA CHO GITHUB

### Câu 1. Vì sao nên dùng Authenticator App thay SMS OTP?

Nên dùng Google Authenticator vì bảo mật tốt hơn SMS OTP.

Hai nhược điểm của SMS OTP:

1. Có thể bị tấn công SIM Swapping, chiếm đoạt số điện thoại.
2. Có nguy cơ bị nghe lén hoặc đánh cắp tin nhắn qua lỗ hổng mạng viễn thông SS7.

### Câu 2. Các bước kích hoạt 2FA

1. Đăng nhập GitHub.
2. Mở Settings.
3. Chọn Password and authentication.
4. Chọn bật Two-factor authentication.
5. Chọn Authenticator App.
6. Mở Google Authenticator trên điện thoại.
7. Quét mã QR trên GitHub.
8. Nhập mã OTP 6 số để xác nhận.
9. Lưu lại 10 mã khôi phục.

### Câu 3. Nơi lưu trữ Backup Codes

**Nên lưu:**

* In ra giấy và cất trong két sắt.
* Lưu trong Bitwarden có mật khẩu bảo vệ.

**Không nên lưu:**

* Không gửi vào nhóm chat.
* Không lưu trong file công khai trên GitHub.
* Không để ảnh mã khôi phục trong thư viện ảnh không được bảo vệ.

\---

## PHẦN 4 – BẢO VỆ SECRETS TRƯỚC KHI PUSH CODE

### Câu 1. Hai giá trị Secrets bị hardcode

1. `sk-proj-abc123456789`: API Key.
2. `SmartCampus@2026`: Mật khẩu Database.

### Câu 2. Code sau khi sửa

File `config.js`:

```javascript
const API\\\_KEY = process.env.API\\\_KEY;
const DB\\\_PASSWORD = process.env.DB\\\_PASSWORD;

function connectDatabase() {
  return connect(DB\\\_PASSWORD);
}
```

### Câu 3. Nội dung 3 file

**File `.env`**

```env
API\\\_KEY=gia\\\_tri\\\_API\\\_KEY\\\_that
DB\\\_PASSWORD=mat\\\_khau\\\_database\\\_that
```

Đây là giá trị minh họa, khi chạy dự án cần thay bằng thông tin thật và không push file này lên GitHub.

**File `.gitignore`**

```gitignore
.env
.env.\\\*
!.env.example
node\\\_modules/
```

**File `.env.example`**

```env
API\\\_KEY=
DB\\\_PASSWORD=
```

File này chỉ chứa tên biến, không chứa giá trị bí mật.

### Câu 4. Quy tắc 4 Bước Kiểm tra trước khi Push

1. Kiểm tra code, tìm API Key và mật khẩu bị ghi trực tiếp.
2. Kiểm tra `.gitignore` đã bỏ qua file `.env`.
3. Dùng `git status` để kiểm tra các file chuẩn bị đưa lên Git.
4. Kiểm tra lại nội dung commit, chắc chắn không có Secrets rồi mới `git push`.

Nếu Secrets đã bị push lên GitHub thì phải đổi hoặc thu hồi chúng ngay.

\---

## 

