# ⚡ BÁO CÁO NGÀY 13 — PARTITIONING VÀ PERFORMANCE TRONG PYSPARK

## 🛠️ Công việc đã thực hiện

### Bài thực hành — Partitioning và Performance

Thực hành cách **Spark chia dữ liệu thành các partition** và tìm hiểu ảnh hưởng của partition đến hiệu năng xử lý.

* Đọc dữ liệu `orders.csv` bằng PySpark.
* Kiểm tra số partition ban đầu bằng `df.rdd.getNumPartitions()`.
* Thử các cách chia partition:

  * `repartition(2)`
  * `repartition(4)`
  * `repartition(8)`
  * `repartition("province")`
  * `coalesce(2)`
* Với mỗi trường hợp, kiểm tra số partition, `groupBy province` và tính tổng số order, tổng amount và average amount.
* Ghi kết quả ra Parquet và kiểm tra số file `part-*` được tạo.
* So sánh `repartition` và `coalesce`, đặc biệt về shuffle và số lượng file output.
* Thử ghi Parquet có và không sử dụng `partitionBy("province")` để quan sát cấu trúc thư mục.
* Thử tạo số lượng partition lớn để kiểm tra tình trạng **small files** và ảnh hưởng đến hiệu năng.

## 📚 Kiến thức rút ra

* Hiểu partition là cách Spark chia dữ liệu để thực hiện xử lý song song.
* `repartition()` có thể tăng hoặc giảm số partition và thường gây **shuffle**.
* `coalesce()` chủ yếu dùng để giảm số partition và hạn chế shuffle.
* `repartition("province")` chia dữ liệu dựa trên giá trị của column, khác với việc chỉ chỉ định số partition.
* `partitionBy("province")` khi ghi dữ liệu sẽ tạo cấu trúc thư mục theo từng province, khác với partition dùng trong quá trình xử lý của Spark.
* Số partition phù hợp giúp cân bằng giữa khả năng xử lý song song và chi phí shuffle.
* Quá nhiều partition có thể tạo nhiều file nhỏ, làm tăng overhead khi đọc và quản lý dữ liệu.

## ✅ Kết quả

Hoàn thành bài thực hành **Partitioning và Performance trong PySpark**.

* Kiểm tra và thay đổi được số lượng partition.
* So sánh được `repartition` và `coalesce`.
* Thực hành partition theo column và `partitionBy` khi ghi Parquet.
* Quan sát được sự khác nhau về số file và cấu trúc output.
* Hiểu được ảnh hưởng của partition, shuffle và small files đến hiệu năng xử lý dữ liệu.

