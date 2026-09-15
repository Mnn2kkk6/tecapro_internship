# ⚡ BÁO CÁO NGÀY 7 — XÂY DỰNG BRONZE LAYER VỚI PYSPARK

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY7#-b%C3%A1o-c%C3%A1o-ng%C3%A0y-7--x%C3%A2y-d%E1%BB%B1ng-bronze-layer-v%E1%BB%9Bi-pyspark)

## 🛠️ Công việc đã thực hiện

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY7#%EF%B8%8F-c%C3%B4ng-vi%E1%BB%87c-%C4%91%C3%A3-th%E1%BB%B1c-hi%E1%BB%87n)

Dựa trên phần đọc hiểu dữ liệu và nghiệp vụ của ngày 6, tiến hành xây dựng **Bronze layer** cho dữ liệu QTTG BHXH bằng PySpark.

* Viết job `bronze_qttg.py` để xử lý dữ liệu Bronze.
* Đọc 2 file CSV nguồn: `RAW_QTTG_BHXH.csv` và `RAW_QTTG_BHXH_DETAIL.csv`.
* Sử dụng schema tường minh theo DDL của 2 bảng thay vì để Spark tự suy luận kiểu dữ liệu.
* Giữ nguyên dữ liệu raw, chưa thực hiện các bước xử lý nghiệp vụ như lọc dữ liệu hoặc chọn bản ghi mới nhất.
* Bổ sung metadata gồm `source_file`, `load_time` và `layer = "BRONZE"`.
* Ghi dữ liệu Bronze dưới dạng Parquet vào thư mục `output/spark_lake/bronze`.
* Đọc lại dữ liệu sau khi ghi để kiểm tra số dòng thực tế và đối chiếu với dữ liệu input.

## 📚 Kiến thức rút ra

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY7#-ki%E1%BA%BFn-th%E1%BB%A9c-r%C3%BAt-ra)

Hiểu rõ hơn vai trò của **Bronze layer** trong Data Lakehouse:

* **Bronze:** lưu trữ dữ liệu raw gần như nguyên trạng từ nguồn, phục vụ việc kiểm tra và xử lý ở các layer tiếp theo.
* Bronze **không xử lý nghiệp vụ**, không loại bỏ bản ghi và không chọn phiên bản mới nhất.
* Việc sử dụng **schema tường minh** giúp kiểm soát kiểu dữ liệu và đảm bảo dữ liệu đọc vào đúng với cấu trúc bảng nguồn.
* Các cột metadata như `source_file`, `load_time`, `layer` giúp truy vết nguồn dữ liệu và thời điểm dữ liệu được ingest.
* Sau khi ghi Parquet cần **đọc lại và count dữ liệu trên output** để đảm bảo dữ liệu Bronze không bị mất hoặc sai lệch so với input.

## ✅ Kết quả

[svg](https://github.com/Mnn2kkk6/tecapro_internship/tree/main/DAY7#-k%E1%BA%BFt-qu%E1%BA%A3)

Hoàn thành Bronze layer cho 2 bảng QTTG BHXH:

* `RAW_QTTG_BHXH`: **142.857 dòng**.
* `RAW_QTTG_BHXH_DETAIL`: **1.000.000 dòng**.
* Dữ liệu được ghi thành công dưới dạng **Parquet** tại:

  * `output/spark_lake/bronze/raw_qttg_bhxh`
  * `output/spark_lake/bronze/raw_qttg_bhxh_detail`
* Số dòng sau khi ghi Bronze **khớp với số dòng input**.
* Job trả về trạng thái `SUCCESS` khi dữ liệu được ghi và kiểm tra hợp lệ.

Qua bài thực hành, hoàn thành bước **ingest dữ liệu raw vào Bronze layer** và tạo nền tảng cho bước xử lý nghiệp vụ tại **Silver layer**.
