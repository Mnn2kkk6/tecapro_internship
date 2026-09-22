# ⚡ BÁO CÁO NGÀY 6 — ĐỌC HIỂU DỮ LIỆU VÀ NGHIỆP VỤ QTTG BHXH

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY6#-b%C3%A1o-c%C3%A1o-ng%C3%A0y-6--%C4%91%E1%BB%8Dc-hi%E1%BB%83u-d%E1%BB%AF-li%E1%BB%87u-v%C3%A0-nghi%E1%BB%87p-v%E1%BB%A5-qttg-bhxh)

## 🛠️ Công việc đã thực hiện

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY6#%EF%B8%8F-c%C3%B4ng-vi%E1%BB%87c-%C4%91%C3%A3-th%E1%BB%B1c-hi%E1%BB%87n)

Tìm hiểu dữ liệu và nghiệp vụ của hệ thống **QTTG BHXH** thông qua file phân tích nghiệp vụ và DDL của các bảng.

* Đọc và tìm hiểu file `PHAN_TICH_NGHIEP_VU_QTTG_BHXH.md`.
* Phân tích 2 bảng `RAW_QTTG_BHXH` và `RAW_QTTG_BHXH_DETAIL`.
* Xác định grain dữ liệu của bảng master và detail.
* Đọc DDL để hiểu cấu trúc cột, khóa chính và mối quan hệ giữa hai bảng.
* Kiểm tra số lượng bản ghi và quan hệ `MASTER_ID` giữa bảng detail và master.
* Kiểm tra `NLD_ID` trong bảng detail có khớp với bản ghi master tương ứng hay không.

## 📚 Kiến thức rút ra

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY6#-ki%E1%BA%BFn-th%E1%BB%A9c-r%C3%BAt-ra)

Hiểu rõ vai trò và mối quan hệ giữa hai bảng:

* **RAW_QTTG_BHXH:** lưu trạng thái tổng hợp của một người lao động tại từng thời điểm trích xuất dữ liệu.
* **RAW_QTTG_BHXH_DETAIL:** lưu chi tiết các giai đoạn tham gia BHXH tương ứng với từng bản ghi master.
* Một người lao động có thể xuất hiện nhiều lần trong bảng master do dữ liệu được trích xuất tại nhiều thời điểm khác nhau.
* Các bản ghi detail có thể bị nhân bản theo các phiên bản master, vì vậy Silver cần chọn bản ghi có `CREATED_AT` mới nhất theo `SO_SO_BHXH`.
* Việc chọn phiên bản mới nhất giúp giữ lại dữ liệu cập nhật nhất và tránh tính trùng các giai đoạn detail khi xử lý các layer phía sau.

## ✅ Kết quả

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY6#-k%E1%BA%BFt-qu%E1%BA%A3)

Hoàn thành việc kiểm tra và hiểu cấu trúc dữ liệu đầu vào:

* Bảng master có **142.857 dòng**.
* Bảng detail có **1.000.000 dòng**.
* Detail liên kết với master thông qua `MASTER_ID`.
* Kiểm tra tính nhất quán giữa `NLD_ID` của detail và master tương ứng.

Qua đó hiểu được cách tổ chức dữ liệu **master-detail**, grain của từng bảng và lý do cần xử lý phiên bản mới nhất theo `SO_SO_BHXH` tại Silver trước khi tiếp tục các bước phân tích và tổng hợp dữ liệu.
