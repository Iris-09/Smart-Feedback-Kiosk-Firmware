# 📠 Đồ án: Smart Interactive Feedback Kiosk (Firmware)

Đây là kho lưu trữ mã nguồn (Source Code) cho đồ án "Trạm thu thập đánh giá dịch vụ khách hàng thông minh". Dự án sử dụng vi điều khiển ESP32, lập trình qua **PlatformIO** trên VS Code.

## 👥 Phân công nhóm (4 Thành viên)
* **Thành viên 1:** Hardware, Thiết kế Kiosk 2D/3D & Mạch thật.
* **Thành viên 2:** Core Firmware (Nút nhấn, Debounce, Non-blocking Delay).
* **Thành viên 3:** Data & UI (Giao diện LCD I2C, Lưu trữ EEPROM).
* **Thành viên 4 (Admin):** Quản lý Git, QA/Testing, Hợp nhất Code & Docs.

## 🔗 Các liên kết quan trọng
* **Mạch mô phỏng (Wokwi):** `[Thành viên 1 - Hãy dán link Wokwi mạch ESP32 vào đây]`
* **Tài liệu báo cáo:** `[Link Google Docs/Folder của nhóm]`

---

## 🛠 Hướng dẫn Cài đặt Môi trường (Bắt buộc)
Để code không bị lỗi thư viện, tất cả thành viên **phải** làm theo các bước sau:
1. Cài đặt **VS Code**.
2. Mở tab Extensions trong VS Code, tìm và cài đặt tiện ích **PlatformIO IDE**.
3. Cài đặt thêm tiện ích **C/C++ Extension Pack** của Microsoft.

---

## 🚦 Quy trình Git (Git Workflow) - ĐỌC KỸ ĐỂ KHÔNG LÀM HỎNG CODE
**⚠️ QUY TẮC:** Không ai được phép gõ lệnh `git push` thẳng lên nhánh `main` hoặc `dev`. 

### Bước 1: Lấy code về máy (Chỉ làm 1 lần đầu)
Mở Terminal, di chuyển đến thư mục muốn lưu code và gõ:
```bash
git clone [https://github.com/Tên-Tài-Khoản-GitHub/Smart-Feedback-Kiosk-Firmware.git]
cd Smart-Feedback-Kiosk-Firmware
git checkout dev
```

---

### Bước 2: Bắt đầu làm việc (Tạo nhánh mới)
Trước khi code tính năng của bạn, HÃY LUÔN TẠO NHÁNH MỚI từ nhánh dev:
```bash
git pull origin dev 
git checkout -b feat/ten-tinh-nang-cua-ban (Ví dụ: git checkout -b feat/test-led hoặc git checkout -b feat/lcd-menu)
```

---

### Bước 3: Code và Lưu lịch sử (Commit)
Chỉ code vào các file được phân công trong thư mục src/. Làm xong thì lưu lại:
```bash
git add .
git commit -m "feat: mô tả ngắn gọn vừa làm gì"
```
### Bước 4: Đẩy code lên và nhờ Review (Pull Request)
```bash
git push origin feat/ten-tinh-nang-cua-ban
```
## Sơ đồ chân (Pin Mapping)

Dưới đây là cấu hình chân (Pinout) kết nối giữa vi điều khiển ESP32 và các module linh kiện trong hệ thống Kiosk:

| Linh kiện | Chân trên ESP32 | Loại tín hiệu | Ghi chú |
| :--- | :--- | :--- | :--- |
| Nút TỐT | GPIO 13 | `INPUT_PULLUP` | Tích cực mức THẤP (LOW) |
| Nút KHÁ | GPIO 32 | `INPUT_PULLUP` | Tích cực mức THẤP (LOW) |
| Nút TỆ | GPIO 33 | `INPUT_PULLUP` | Tích cực mức THẤP (LOW) |
| Đèn LED & Còi | GPIO 25 | `OUTPUT` | Tích cực mức CAO (HIGH) |
| LCD I2C (SDA) | GPIO 21 | I2C Data | Nguồn cấp 5V |
| LCD I2C (SCL) | GPIO 22 | I2C Clock | Nguồn cấp 5V |

**Link Wokwi mô phỏng mạch ảo:**
 https://wokwi.com/projects/477044635174522881