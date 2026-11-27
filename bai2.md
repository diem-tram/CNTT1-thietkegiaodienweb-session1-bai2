# Rà soát prompt C.R.A.F.T và bản nháp của AI

---

## PHẦN 1: RÀ SOÁT PHÁT HIỆN LỖI

### 1. Phân tích Prompt theo khung C.R.A.F.T

| Prompt | Thành phần thiếu / yếu | Chi tiết sai sót |
| :--- | :--- | :--- |
| **P1** | Thiếu **Context, Role, Format, Tone** (chỉ có Action chung chung) | Không nêu rõ tên ứng dụng (ShopeeFood), màn hình thao tác (Giỏ hàng), tình huống lỗi (quán đóng cửa), không định nghĩa vai trò UX Writer, thiếu giới hạn ký tự ($\le 60$) và không quy định giọng điệu không đổ lỗi. |
| **P2** | Yếu **Format**, thiếu chi tiết **Action** | Phần Format ghi *"Ngắn gọn"* quá mơ hồ thay vì chốt cứng giới hạn **tối đa 20 ký tự** cho nút bấm CTA; Action chưa yêu cầu hiển thị kèm tổng số tiền thanh toán. |
| **P3** | Thiếu **Role**, thiếu dữ liệu đầu vào ở **Context** | Thiếu vai trò UX Copywriter; Context chỉ nêu mốc khuyến mãi 100.000đ nhưng không cung cấp giá trị tiền món hiện tại (64.000đ) để AI thực hiện phép tính chính xác. |

---

### 2. Phân tích 3 bản nháp do AI tạo ra

| Bản nháp | Nhóm lỗi mắc phải | Giải thích cụ thể |
| :--- | :--- | :--- |
| **D1** (Nhắc ưu đãi) | **Sai lệch toán học & Tràn ký tự** | - **Tính sai số tiền:** AI tính sai phép trừ ($100.000đ - 64.000đ = 26.000đ$), thiếu mất 10.000đ. Số tiền món cần mua thêm chính xác phải là **36.000đ**.<br>- **Tràn ký tự:** Chuỗi gốc dài **64 ký tự**, vượt quá giới hạn cho phép (tối đa 60 ký tự) **4 ký tự**. |
| **D2** (Nút CTA) | **Tràn số lượng ký tự thiết kế** | Chuỗi *"Xác nhận đặt món và thanh toán 80.000đ ngay"* dài tới **45 ký tự**, vượt quá giới hạn tối đa (20 ký tự) **25 ký tự**, gây vỡ giao diện nút bấm. |
| **D3** (Báo lỗi) | **Vi phạm UX Heuristic & Tràn ký tự** | - **Đổ lỗi người dùng:** Cụm *"vì bạn đặt quá muộn"* tạo cảm giác trách móc, gây trải nghiệm tiêu cực.<br>- **Dùng mã lỗi kỹ thuật vô nghĩa:** Hiển thị *"Lỗi 503"* khiến người dùng phổ thông hoang mang, không hiểu nguyên nhân.<br>- **Thiếu lối ra (Error Recovery):** Không cung cấp giải pháp hoặc gợi ý hành động tiếp theo cho khách hàng.<br>- **Tràn ký tự:** Chuỗi gốc dài **62 ký tự**, vượt quá giới hạn tối đa (60 ký tự) **2 ký tự**. |

---

## PHẦN 2: NỘI DUNG CHUẨN HÓA

### 1. Chuẩn hóa Prompt P1 (Đầy đủ 5 thành phần C.R.A.F.T)

* **Context:** Người dùng đang ở màn hình Giỏ hàng trên ứng dụng đặt đồ ăn ShopeeFood và bấm thanh toán, nhưng quán vừa đóng cửa ngừng nhận đơn.
* **Role:** Bạn là một UX Copywriter chuyên nghiệp cho ứng dụng giao đồ ăn.
* **Action:** Viết 1 thông báo lỗi ngắn gọn báo cho người dùng biết quán đã đóng cửa và gợi ý họ tìm quán khác tương tự.
* **Format:** 1 câu duy nhất, độ dài **tối đa 60 ký tự** (tính cả dấu cách và dấu câu).
* **Tone:** Tự nhiên, lịch sự, đồng cảm, tuyệt đối không đổ lỗi cho người dùng và không dùng mã lỗi kỹ thuật.

---

### 2. Viết lại 3 nội dung UI (Đã kiểm đếm ký tự chuẩn xác)

1. **D1 – Dòng nhắc ưu đãi (Giới hạn $\le 60$ ký tự):**
   > **Mua thêm 36.000đ tiền món để được giảm 15.000đ phí ship.**
   * *Số ký tự thực tế:* **59 ký tự** (bao gồm dấu cách và dấu chấm).
   * *Điểm cải thiện:* Tính đúng phần tiền món còn thiếu ($100.000đ - 64.000đ = 36.000đ$), diễn đạt rõ ràng và nằm gọn trong khung hiển thị.

2. **D2 – Nút bấm CTA (Giới hạn $\le 20$ ký tự):**
   > **Đặt đơn • 80.000đ**
   * *Số ký tự thực tế:* **17 ký tự** (bao gồm dấu cách và dấu chấm phân tách).
   * *Điểm cải thiện:* Thể hiện trực diện hành động đặt món và tổng số tiền thanh toán (80.000đ), đảm bảo không bị tràn nút trên màn hình di động.

3. **D3 – Thông báo quán đóng cửa (Giới hạn $\le 60$ ký tự):**
   > **