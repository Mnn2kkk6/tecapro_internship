# ⚡ BÁO CÁO NGÀY 10 — HOÀN THIỆN PIPELINE VỚI AIRFLOW

## 🛠️ Công việc đã thực hiện

Hoàn thiện luồng xử lý dữ liệu **QTTG BHXH** bằng cách kết hợp **PySpark và Airflow**.

* Đọc và thực hiện theo tài liệu `HUONG_DAN_AIRFLOW_SPARK_LOCAL.md`.
* Tạo DAG Airflow điều phối 4 job:

  * `bronze_qttg`
  * `silver_qttg`
  * `gold_qttg`
  * `validate_qttg`
* Thiết lập dependency theo thứ tự:
  `Bronze → Silver → Gold → Validate`
* Chạy thử pipeline trên **Airflow UI** và kiểm tra trạng thái các task.
* Tổng hợp kết quả xử lý dữ liệu trong tuần.

## 📚 Kiến thức rút ra

Hiểu rõ hơn cách **Airflow** được sử dụng để điều phối một pipeline Data Engineering:

* **Airflow:** quản lý thứ tự, dependency và trạng thái các job.
* **PySpark:** thực hiện các bước ingest, transform và aggregation.
* Pipeline có thể tổ chức theo luồng **Ingest → ETL → Result → Validate**.
* Việc tách Bronze, Silver và Gold giúp quá trình xử lý dữ liệu rõ ràng và dễ kiểm tra.

## ✅ Kết quả

Hoàn thiện pipeline xử lý dữ liệu **QTTG BHXH** với khoảng **1.000.000 dòng detail**:

* **Bronze:** ingest dữ liệu raw thành công.
* **Silver:** làm sạch và xử lý nghiệp vụ thành công.
* **Gold:** tạo báo cáo tổng hợp theo tháng.
* **Validate:** kiểm tra kết quả sau xử lý.
* Các output được lưu lần lượt tại `output/spark_lake/bronze`, `silver` và `gold`.
* DAG Airflow điều phối thành công toàn bộ luồng **Bronze → Silver → Gold → Validate**.

Qua đó hoàn thiện flow **Ingest → ETL → Result**, đồng thời cập nhật README hướng dẫn cách chạy và kiểm tra kết quả của pipeline.
