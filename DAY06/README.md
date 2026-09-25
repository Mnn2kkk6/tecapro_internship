# ⚡ BÁO CÁO NGÀY 6 — ĐỌC HIỂU DỮ LIỆU VÀ NGHIỆP VỤ QTTG BHXH

## 🛠️ Công việc đã thực hiện

Tìm hiểu dữ liệu và nghiệp vụ của hệ thống **QTTG BHXH** thông qua file phân tích nghiệp vụ và DDL của các bảng.

* Đọc và tìm hiểu file `PHAN_TICH_NGHIEP_VU_QTTG_BHXH.md`.
* Phân tích 2 bảng `RAW_QTTG_BHXH` và `RAW_QTTG_BHXH_DETAIL`.
* Xác định grain dữ liệu của bảng master và detail.
* Đọc DDL để hiểu cấu trúc cột, khóa chính và mối quan hệ giữa hai bảng.
* Kiểm tra số lượng bản ghi và quan hệ `MASTER_ID` giữa bảng detail và master.
* Kiểm tra `NLD_ID` trong bảng detail có khớp với bản ghi master tương ứng hay không.

## 📚 Kiến thức rút ra

Hiểu rõ vai trò và mối quan hệ giữa hai bảng:

* **RAW_QTTG_BHXH:** lưu trạng thái tổng hợp của một người lao động tại từng thời điểm trích xuất dữ liệu.
* **RAW_QTTG_BHXH_DETAIL:** lưu chi tiết các giai đoạn tham gia BHXH tương ứng với từng bản ghi master.
* Một người lao động có thể xuất hiện nhiều lần trong bảng master do dữ liệu được trích xuất tại nhiều thời điểm khác nhau.
* Các bản ghi detail có thể bị nhân bản theo các phiên bản master, vì vậy Silver cần chọn bản ghi có `CREATED_AT` mới nhất theo `SO_SO_BHXH`.
* Việc chọn phiên bản mới nhất giúp giữ lại dữ liệu cập nhật nhất và tránh tính trùng các giai đoạn detail khi xử lý các layer phía sau.

## ✅ Kết quả

Hoàn thành việc kiểm tra và hiểu cấu trúc dữ liệu đầu vào:

* Bảng master có **142.857 dòng**.
* Bảng detail có **1.000.000 dòng**.
* Detail liên kết với master thông qua `MASTER_ID`.
* Kiểm tra tính nhất quán giữa `NLD_ID` của detail và master tương ứng.

Qua đó hiểu được cách tổ chức dữ liệu **master-detail**, grain của từng bảng và lý do cần xử lý phiên bản mới nhất theo `SO_SO_BHXH` tại Silver trước khi tiếp tục các bước phân tích và tổng hợp dữ liệu.
