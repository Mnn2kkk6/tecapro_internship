# ⚡ BÁO CÁO NGÀY 16 — BÀI TỔNG HỢP PYSPARK

## 🛠️ Công việc đã thực hiện

Thực hiện bài tổng hợp nhằm kết hợp các kiến thức PySpark đã học thành một quy trình xử lý dữ liệu hoàn chỉnh từ **Read → Clean → Validate → Deduplicate → Join → Transform → Aggregate → Write → Check**.

### 1. Read + Clean

* Chuẩn bị 2 file dữ liệu:

  * `orders.csv`: thông tin đơn hàng.
  * `customers.csv`: thông tin khách hàng.
* Chủ động tạo các trường hợp dữ liệu lỗi:

  * `order_id` bị duplicate.
  * `amount` bị null hoặc `<= 0`.
  * `status` không đồng nhất về hoa/thường.
  * `order_date` sai định dạng.
  * `customer_id` không tồn tại trong bảng customers.
* Tự khai báo **schema** cho cả hai file.
* Đọc dữ liệu bằng PySpark và kiểm tra cấu trúc, kiểu dữ liệu.
* Chuẩn hóa `status` về **uppercase**.
* Cast và kiểm tra tính hợp lệ của `amount`.
* Parse `order_date` sang kiểu ngày.
* Kiểm tra và xác định các record không hợp lệ.

### 2. Deduplicate + Validate

* Sử dụng **Window Function** kết hợp `row_number()` để xử lý `order_id` bị duplicate.
* Với các record trùng `order_id`, giữ lại bản ghi có `updated_at` mới nhất.
* Tách dữ liệu thành:

  * `valid_orders`
  * `invalid_orders`
* Bổ sung cột `error_reason` cho `invalid_orders`.
* Phân loại lỗi gồm:

  * `INVALID_AMOUNT`
  * `INVALID_DATE`
  * `CUSTOMER_NOT_FOUND`

### 3. Join + Transform

* Thực hiện **Left Join** giữa orders và customers theo `customer_id`.
* Kiểm tra các order không tìm thấy customer tương ứng.
* Tạo thêm cột `order_level` dựa trên giá trị `amount` với các mức:

  * `HIGH`
  * `MEDIUM`
  * `LOW`

### 4. Aggregate

Tổng hợp dữ liệu theo `province` và xây dựng báo cáo gồm:

* `total_orders`
* `total_customers`
* `total_amount`
* `avg_amount`
* `success_orders`
* `failed_orders`

Qua bước này có thể theo dõi số lượng đơn hàng, khách hàng và giá trị giao dịch theo từng tỉnh.

### 5. Write + Check

* Ghi `valid_orders` ra định dạng **Parquet**.
* Ghi `invalid_orders` ra thư mục output riêng.
* Ghi `province_report` ra **Parquet hoặc CSV**.
* Ghi `valid_orders` với `partitionBy("province")`.
* Đọc lại các output sau khi ghi.
* Kiểm tra:

  * `count`
  * `schema`
  * tổng `amount` trước và sau khi write.
* Đối chiếu kết quả để đảm bảo dữ liệu sau khi lưu trữ không bị sai lệch.

## 📚 Kiến thức rút ra

### Window và `dropDuplicates()`

Sử dụng **Window** thay vì `dropDuplicates()` khi cần xác định chính xác record nào được giữ lại dựa trên một tiêu chí cụ thể, trong bài này là `updated_at` mới nhất.

`dropDuplicates()` chỉ loại bỏ record trùng theo key nhưng không đảm bảo giữ lại bản ghi mới nhất.

### Left Join

Sử dụng **Left Join** để giữ toàn bộ order từ bảng chính, kể cả những order không có customer tương ứng. Qua đó có thể phát hiện và thống kê các trường hợp `CUSTOMER_NOT_FOUND`.

### `partitionBy()`

`partitionBy("province")` tổ chức dữ liệu vật lý thành các thư mục theo từng tỉnh. Khi truy vấn có điều kiện lọc theo `province`, Spark có thể chỉ đọc các partition liên quan thay vì quét toàn bộ dữ liệu.

### Xử lý `amount` và `order_date` lỗi trong ETL

Dữ liệu lỗi cần được phát hiện trong bước validation và tách khỏi dữ liệu hợp lệ. Có thể lưu các record lỗi vào một output riêng kèm `error_reason` để phục vụ kiểm tra, sửa dữ liệu hoặc xử lý lại ở các bước sau.

### Các bước có khả năng gây Shuffle

Các thao tác có khả năng gây **shuffle** trong bài gồm:

* `Window` khi xử lý duplicate theo `order_id`.
* `join` giữa orders và customers.
* `groupBy` khi tổng hợp theo `province`.
* `partitionBy("province")` khi ghi dữ liệu nếu cần phân phối lại dữ liệu theo partition key.

## ✅ Kết quả

Hoàn thiện bài thực hành tổng hợp PySpark, kết nối các bước xử lý dữ liệu thành một pipeline hoàn chỉnh:

**Read → Clean → Validate → Deduplicate → Join → Transform → Aggregate → Write → Check**

Qua bài thực hành, củng cố cách xây dựng pipeline xử lý dữ liệu thực tế với **schema, validation, Window Function, Join, Aggregation, Parquet và Partitioning**, đồng thời hiểu rõ hơn các bước có thể phát sinh **shuffle** trong PySpark.
