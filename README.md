### Phần I: Phân tích sai lầm trong tư duy tìm kiếm

#### 1. Phân tích vì sao Query 1 là một Bad Query điển hình
Câu truy vấn *"thầy ơi cho em hỏi phần mềm sạc của công ty bị lỗi gì mà không mở được vậy ạ"* mắc các lỗi nghiêm trọng sau:
* **Dùng ngôn ngữ giao tiếp cảm tính:** Chứa nhiều từ ngữ hội thoại thừa thãi (*"thầy ơi"*, *"cho em hỏi"*, *"vậy ạ"*). Bộ máy tìm kiếm chỉ phân tích từ khóa, việc đưa văn nói vào làm loãng trọng tâm tìm kiếm.
* **Không cung cấp mã lỗi thực tế (Raw Error):** Mô tả chung chung là *"bị lỗi gì mà không mở được"* thay vì đưa mã lỗi gốc `0x80070005` hoặc `Access is denied`, khiến Google không thể khớp với các tài liệu kỹ thuật cụ thể.
* **Thiếu ngữ cảnh công nghệ (Context):** Chỉ nhắc đến *"phần mềm sạc của công ty"* (tên nội bộ mà Google không biết) thay vì nêu tên hệ điều hành **Windows 10** hay thư viện giao tiếp cổng **OCPP**.

#### 2. Chỉ ra hiểm họa an ninh mạng nghiêm trọng từ Query 5
Trong Query 5 (*"tải phần mềm fix lỗi 0x80070005 full crack"*), nếu nhân viên kỹ thuật tải và cài đặt tệp từ kết quả tìm kiếm này vào máy trạm Kiosk của công ty sẽ gây ra các hậu quả sau:
* **Nhiễm mã độc (Malware / Ransomware / Trojan):** Các trang web cung cấp phần mềm "full crack" hoặc "tool fix lỗi miễn phí" thường chèn sẵn mã độc đánh cắp dữ liệu, mã độc tống tiền hoặc cửa hậu (Backdoor).
* **Mất kiểm soát hệ thống trạm sạc toàn công ty:** Máy trạm Kiosk là thiết bị điều khiển phần cứng trạm sạc nhanh và kết nối với máy chủ trung tâm. Khi máy bị nhiễm mã độc, tin tặc có thể chiếm quyền điều khiển từ xa, làm gián đoạn dịch vụ sạc hoặc đánh cắp dữ liệu giao dịch và thông tin khách hàng.

---

### Phần II: Chuẩn hóa Cú pháp Tìm kiếm Chuyên nghiệp

#### 3. Bảng bóc tách thông báo lỗi thực tế thành 3 thành phần cốt lõi

| Thành phần cốt lõi | Nội dung trích xuất chuẩn | Mục đích phục vụ tìm kiếm |
| :--- | :--- | :--- |
| **1. Tên phần mềm / Môi trường** | `VoltCharge Controller Windows 10` | Khoanh vùng đúng phiên bản hệ điều hành đang gặp sự cố. |
| **2. Mã lỗi nguyên văn** | `0x80070005 Access is denied` | Tìm chính xác nguyên nhân hệ thống từ chối quyền truy cập tệp hoặc cổng thiết bị. |
| **3. Thao tác thực hiện** | `Init OCPP Port` | Xác định đúng tác vụ đang bị chặn khi khởi tạo kết nối giao tiếp trạm sạc. |

#### 4. Xây dựng 03 câu lệnh tìm kiếm Google chuẩn kỹ sư

* **Cách tiếp cận 1 (Tìm bài viết sửa lỗi chính xác trên diễn đàn Microsoft Community dành riêng cho Windows 10, loại bỏ Windows 7 và Windows 8):**
  ```text
  site:://microsoft.com "0x80070005" "Access is denied" "Windows 10" -Windows7 -Windows8 -"Windows 7" -"Windows 8"
  ```

* **Cách tiếp cận 2 (Tìm tài liệu đặc tả về lỗi phân quyền cổng OCPP từ trang chủ tổ chức liên minh gốc):**
  ```text
  site:openchargealliance.org "OCPP" "Access is denied" OR "0x80070005"
  ```

* **Cách tiếp cận 3 (Tìm hướng dẫn xử lý lỗi trên diễn đàn StackOverflow, loại bỏ quảng cáo và crack):**
  ```text
  site:stackoverflow.com "0x80070005" "Access is denied" "OCPP" port "Windows 10" -crack -ads -quảng-cáo
  ```
