# ⚡ BÁO CÁO NGÀY 14 — UDF, PANDAS UDF VÀ UDTF TRONG PYSPARK

## 🔗 Link GitHub

https://github.com/Mnn2kkk6/pyspark-udf-practice

## 🛠️ Công việc đã thực hiện

### Bài 1 — Python UDF

Tìm hiểu cách sử dụng **Python UDF** để xử lý dữ liệu khách hàng.

* Đọc dữ liệu `customers.csv` bằng PySpark.
* Chuẩn hóa `customer_name` bằng cách loại bỏ khoảng trắng và chuyển sang chữ hoa.
* Phân loại khách hàng theo `amount` thành `VIP`, `STANDARD` và `BASIC`.
* Tạo các cột `customer_name_clean` và `customer_segment`.

### Bài 2 — So sánh với Built-in Spark Function

Đối chiếu cách xử lý bằng UDF với các hàm có sẵn của Spark.

* Sử dụng `trim()` và `upper()` để chuẩn hóa tên.
* Sử dụng `when()` và `otherwise()` để phân loại khách hàng.
* So sánh độ dễ đọc và khả năng tối ưu giữa UDF và built-in functions.
* Tìm hiểu lý do nên ưu tiên built-in function khi đã có hàm phù hợp.

### Bài 3 — Pandas UDF

Tìm hiểu **Pandas UDF** và cách xử lý dữ liệu theo dạng batch/vector.

* Áp dụng công thức xử lý trên cột `amount`.
* So sánh Python UDF và Pandas UDF.
* Tìm hiểu trường hợp Pandas UDF phù hợp hơn khi xử lý dữ liệu dạng vector.

### Bài 4 — UDTF

Tìm hiểu **UDTF** thông qua bài toán tách dữ liệu `tags`.

* Tạo DataFrame với cột `tags`, ví dụ `spark,python,etl`.
* Tách một record thành nhiều record tương ứng với từng tag.
* Tạo output `customer_tags` gồm `customer_id` và `tags`.
* Phân biệt cách hoạt động của UDF và UDTF.

## 📚 Kiến thức rút ra

* **UDF** cho phép tự định nghĩa logic xử lý dữ liệu trong Spark.
* **UDTF** có thể chuyển một input row thành nhiều output row.
* **Pandas UDF** hỗ trợ xử lý dữ liệu theo batch/vector.
* **Built-in Spark functions** nên được ưu tiên khi đã có sẵn logic tương ứng vì Spark có thể tối ưu quá trình thực thi tốt hơn.
* Việc lựa chọn giữa UDF, Pandas UDF, UDTF và built-in function cần dựa trên yêu cầu xử lý và hiệu năng.

## ✅ Kết quả

* Xử lý dữ liệu khách hàng bằng Python UDF.
* Đối chiếu với built-in Spark functions.
* Áp dụng Pandas UDF cho dữ liệu số.
* Sử dụng UDTF để tách dữ liệu `tags`.
* Tạo hai output `customers_processed` và `customer_tags`.
* Nắm được cách lựa chọn phương pháp phù hợp khi xử lý dữ liệu bằng PySpark.
