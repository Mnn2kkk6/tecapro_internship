# ⚡ BÁO CÁO NGÀY 4 — DATA LAKEHOUSE PIPELINE

🔗 **GitHub:** https://github.com/Mnn2kkk6/pyspark-orders-repo

## 🛠️ Công việc đã thực hiện

Tiếp tục từ bài PySpark hôm trước, xây dựng một pipeline Data Lakehouse đơn giản theo mô hình **Bronze → Silver → Gold**, kết hợp với **MinIO** để lưu trữ dữ liệu.

* Tạo `orders.csv` gồm 250 dòng, có thêm một số dữ liệu lỗi để thực hành xử lý.
* **Bronze:** đọc và giữ nguyên dữ liệu gốc, thêm `source_file` và `load_time`.
* **Silver:** làm sạch dữ liệu, bỏ `order_id` rỗng, lọc `amount > 0`, chuẩn hóa `status` và chuyển kiểu dữ liệu.
* **Gold:** group theo `province`, tính tổng số đơn, tổng tiền và số đơn thành công/thất bại.
* Dùng **Docker + MinIO** tạo bucket `lakehouse-demo` và lưu dữ liệu của từng layer.
* Xử lý một số lỗi môi trường liên quan đến **Docker Desktop và PYSPARK_PYTHON**.

## 📚 Kiến thức rút ra

Hiểu rõ hơn cách hoạt động của mô hình **Bronze/Silver/Gold**, đặc biệt là việc giữ dữ liệu gốc ở Bronze để có thể kiểm tra hoặc xử lý lại khi cần.

Đồng thời hiểu thêm về **MinIO** và cách kết hợp **PySpark + MinIO** để xây dựng một pipeline dữ liệu cơ bản.

**Flow:**
`CSV → Bronze → Silver → Gold → MinIO`

## ✅ Kết quả

Hoàn thành một pipeline Data Lakehouse cơ bản bằng PySpark, đi từ dữ liệu thô có lỗi cố ý, qua từng tầng xử lý Bronze → Silver → Gold, đến lưu trữ trên MinIO. Đồng thời củng cố kiến thức về kiến trúc lakehouse, nguyên tắc thiết kế từng layer, và cách vận hành một pipeline dữ liệu nhiều bước trong môi trường thực tế (kể cả xử lý lỗi môi trường khi triển khai trên Windows).
