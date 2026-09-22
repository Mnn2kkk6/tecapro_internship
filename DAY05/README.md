# ⚡ BÁO CÁO NGÀY 5 — AIRFLOW, ICEBERG, NESSIE & DATA CATALOG

## 🛠️ Công việc đã thực hiện

Tiếp tục hoàn thiện flow Data Lakehouse từ ngày 4 với các thành phần **Airflow, Iceberg, Nessie và Data Catalog**.

* Tạo DAG Airflow gồm 3 task: `bronze_task → silver_task → gold_task`.
* Thiết lập dependency để các task chạy đúng thứ tự Bronze → Silver → Gold.
* Chạy thử DAG trên **Airflow UI** và kiểm tra log của từng task.
* Tìm hiểu vai trò của **Airflow**: dùng để điều phối và lập lịch các bước xử lý, không trực tiếp xử lý dữ liệu như Spark.
* Tìm hiểu vai trò của **Iceberg, Nessie và Data Catalog** trong hệ thống Data Lakehouse.

## 📚 Kiến thức rút ra

Hiểu rõ hơn vai trò của từng thành phần:

* **Spark:** xử lý dữ liệu.
* **MinIO:** lưu trữ file dữ liệu.
* **Iceberg:** quản lý dữ liệu trên Data Lake dưới dạng table.
* **Nessie:** quản lý catalog và version của table.
* **Data Catalog:** quản lý thông tin về dataset, schema và vị trí dữ liệu.
* **Airflow:** điều phối và schedule các job trong pipeline.

## ✅ Kết quả

Hoàn thành flow Data Lakehouse cơ bản:

`Source CSV → Spark → Bronze → Silver → Gold → MinIO`

Kết hợp thêm **Airflow** để điều phối pipeline và **Iceberg/Nessie/Data Catalog** để quản lý table, catalog và metadata, giúp hiểu rõ hơn cách các thành phần kết hợp trong một hệ thống Data Lakehouse thực tế.

