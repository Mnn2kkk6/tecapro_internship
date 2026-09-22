# ⚡ BÁO CÁO NGÀY 7 — XÂY DỰNG BRONZE LAYER VỚI PYSPARK

## 🛠️ Công việc đã thực hiện

Dựa trên phần đọc hiểu dữ liệu và nghiệp vụ của ngày 6, tiến hành xây dựng **Bronze layer** cho dữ liệu QTTG BHXH bằng PySpark.

* Viết job `bronze_qttg.py` để xử lý dữ liệu Bronze.
* Đọc 2 file CSV nguồn: `RAW_QTTG_BHXH.csv` và `RAW_QTTG_BHXH_DETAIL.csv`.
* Sử dụng schema tường minh theo DDL của 2 bảng.
* Giữ nguyên dữ liệu raw, chưa thực hiện xử lý nghiệp vụ.
* Bổ sung metadata gồm `source_file`, `load_time` và `layer = "BRONZE"`.
* Ghi dữ liệu Bronze dưới dạng Parquet vào `output/spark_lake/bronze`.
* Đọc lại dữ liệu sau khi ghi để kiểm tra số dòng thực tế và đối chiếu với dữ liệu input.

## 📚 Kiến thức rút ra

Hiểu rõ hơn vai trò của **Bronze layer** trong Data Lakehouse:

* **Bronze:** lưu trữ dữ liệu raw gần như nguyên trạng từ nguồn.
* Bronze chưa thực hiện các bước xử lý nghiệp vụ như lọc dữ liệu hoặc chọn bản ghi mới nhất.
* **Schema tường minh** giúp kiểm soát kiểu dữ liệu và đảm bảo cấu trúc dữ liệu đúng với bảng nguồn.
* Các cột metadata `source_file`, `load_time`, `layer` giúp theo dõi nguồn và thời điểm dữ liệu được ingest.
* Kiểm tra số dòng sau khi ghi giúp đảm bảo dữ liệu Bronze khớp với dữ liệu đầu vào.

## ✅ Kết quả

Hoàn thành Bronze layer cho 2 bảng QTTG BHXH:

* `RAW_QTTG_BHXH`: **142.857 dòng**.
* `RAW_QTTG_BHXH_DETAIL`: **1.000.000 dòng**.
* Dữ liệu được ghi thành công dưới dạng **Parquet** tại:

  * `output/spark_lake/bronze/raw_qttg_bhxh`
  * `output/spark_lake/bronze/raw_qttg_bhxh_detail`
* Số dòng sau khi ghi Bronze **khớp với số dòng input**.

Hoàn thành bước **ingest dữ liệu raw vào Bronze layer**, tạo nền tảng cho bước xử lý nghiệp vụ tại **Silver layer**.

## ⚠️ Vấn đề đã gặp và cách xử lý

* **`PATH_NOT_FOUND` khi đọc CSV:** do đường dẫn `--input-dir` chưa trỏ đúng thư mục chứa 2 file CSV. Kiểm tra lại cấu trúc thư mục và cập nhật đường dẫn chính xác.
* **`HADOOP_HOME and hadoop.home.dir are unset` khi ghi Parquet:** Spark trên Windows yêu cầu môi trường Hadoop phù hợp để thao tác với filesystem. Thiết lập `HADOOP_HOME` và bổ sung các file Hadoop cần thiết.
* **Biến môi trường chưa được nhận trong VS Code Terminal:** sau khi cập nhật biến môi trường, cần khởi động lại VS Code để terminal nhận cấu hình mới.
