# ⚡ BÁO CÁO NGÀY 13 — UDF, PANDAS UDF VÀ UDTF TRONG PYSPARK

##Link github : https://github.com/Mnn2kkk6/pyspark-udf-practice
## 🛠️ Công việc đã thực hiện

### Bài 1 — Python UDF

Thực hành sử dụng **Python UDF** để xử lý dữ liệu khách hàng.

* Đọc dữ liệu `customers.csv` bằng PySpark.
* Viết UDF để chuẩn hóa `customer_name` bằng cách loại bỏ khoảng trắng và chuyển sang chữ hoa.
* Viết UDF để phân loại khách hàng theo `amount` thành:

  * `VIP`
  * `STANDARD`
  * `BASIC`
* Tạo thêm các cột `customer_name_clean` và `customer_segment`.

### Bài 2 — So sánh với Built-in Spark Function

Viết lại các xử lý trên bằng các hàm có sẵn của Spark.

* Sử dụng `trim()` và `upper()` để xử lý tên khách hàng.
* Sử dụng `when()` và `otherwise()` để phân loại khách hàng.
* So sánh cách viết bằng UDF và built-in function.
* Tìm hiểu trường hợp nên ưu tiên built-in function để tận dụng khả năng tối ưu của Spark.

### Bài 3 — Pandas UDF

Thực hành **Pandas UDF** để xử lý dữ liệu dạng batch/vector.

* Xử lý cột `amount` bằng một công thức tính toán.
* So sánh cách viết Pandas UDF với Python UDF.
* Tìm hiểu cách Pandas UDF xử lý dữ liệu theo vector và trường hợp phù hợp để sử dụng.

### Bài 4 — UDTF

Thực hành **UDTF** với dữ liệu `tags`.

* Tạo DataFrame có cột `tags` dạng chuỗi như `spark,python,etl`.
* Tách một record thành nhiều record theo từng tag.
* Tạo output `customer_tags` với các cột `customer_id` và `tags`.
* Tìm hiểu sự khác nhau giữa UDF và UDTF:

  * UDF thường trả về một giá trị cho mỗi input row.
  * UDTF có thể tạo ra nhiều row từ một input row.

## 📚 Kiến thức rút ra

* Hiểu **UDF** là cách tự định nghĩa hàm để xử lý dữ liệu trong Spark khi các hàm có sẵn không đáp ứng được yêu cầu.
* Hiểu **UDTF** dùng để biến một input row thành nhiều output row.
* Biết khi nào nên sử dụng **built-in Spark function** thay vì UDF.
* Built-in function thường nên được ưu tiên khi có thể sử dụng vì Spark có thể tối ưu execution tốt hơn.
* Hiểu sự khác nhau giữa **Python UDF** và **Pandas UDF** trong cách xử lý dữ liệu.
* Pandas UDF phù hợp với một số trường hợp cần xử lý dữ liệu theo batch/vector.
* Hiểu việc sử dụng UDF không nên quá lạm dụng khi cùng một logic đã có sẵn trong Spark.

## ✅ Kết quả

Hoàn thành bài thực hành về **UDF, Pandas UDF và UDTF trong PySpark**.

* Xử lý và chuẩn hóa dữ liệu khách hàng bằng Python UDF.
* Viết lại logic bằng built-in Spark functions để so sánh.
* Thực hành Pandas UDF trên dữ liệu số.
* Tách dữ liệu `tags` bằng UDTF và tạo output `customer_tags`.
* Hoàn thành hai output `customers_processed` và `customer_tags`.
* Hiểu rõ hơn cách lựa chọn giữa **built-in function, UDF, Pandas UDF và UDTF** trong quá trình xử lý dữ liệu bằng PySpark.
