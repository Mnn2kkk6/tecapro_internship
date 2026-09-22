# ⚡ BÁO CÁO NGÀY 12 — JOIN, DEDUPLICATE VÀ WINDOW TRONG PYSPARK

## 🛠️ Công việc đã thực hiện

Thực hành xử lý dữ liệu giao dịch bằng PySpark với 2 file `customers.csv` và `transactions.csv`.

* Khai báo **schema thủ công** cho dữ liệu, không sử dụng `inferSchema`.
* Kiểm tra và tách các record lỗi:

  * Thiếu `customer_id`.
  * `amount <= 0`.
* Xử lý các `transaction_id` bị trùng bằng **Window Function**, chỉ giữ bản ghi có `updated_at` mới nhất.
* Thực hiện **left join** giữa `transactions` và `customers`.
* Tách các transaction không mapping được với customer thành một DataFrame riêng.
* Sử dụng **Window Function** để tìm transaction gần nhất của từng customer.
* Tính các chỉ số theo customer:

  * Tổng số transaction.
  * Tổng `amount`.
  * Số transaction có `status = SUCCESS`.
* Tìm **top 3 customer có tổng amount cao nhất theo từng province**.
* Ghi dữ liệu hợp lệ ra **Parquet**, partition theo `province`.
* Ghi dữ liệu lỗi và dữ liệu không mapping được ra output riêng.
* Đọc lại dữ liệu sau khi ghi và kiểm tra count để validate kết quả.
* Sử dụng `explain()` để quan sát execution plan, xác định các bước có **join, shuffle và sort**.

## 📚 Kiến thức rút ra

Hiểu rõ hơn về flow xử lý dữ liệu thực tế trong PySpark:

* **Window Function** phù hợp để xử lý duplicate có điều kiện, ví dụ giữ record mới nhất theo `updated_at`.
* `dropDuplicates()` chỉ loại bỏ duplicate theo các cột được chỉ định, không phù hợp khi cần xác định bản ghi nào được ưu tiên giữ lại.
* **Left Join** giúp giữ toàn bộ transaction, kể cả những record không tìm thấy customer tương ứng, từ đó có thể tách và kiểm tra dữ liệu unmapped.
* Có thể sử dụng Window để xác định **transaction gần nhất của mỗi customer** dựa trên `transaction_time`.
* `groupBy` kết hợp với aggregation để tính các chỉ số tổng hợp theo customer.
* Partition theo `province` giúp tổ chức dữ liệu output theo khu vực và hỗ trợ truy vấn theo partition.
* `explain()` giúp quan sát cách Spark thực thi query và phát hiện các bước có khả năng gây **shuffle, sort hoặc join**.
* Khi dữ liệu tăng lên vài triệu record, các bước như **join, window và aggregation** có thể tạo nhiều shuffle và tiêu tốn tài nguyên.

## ✅ Kết quả

Hoàn thành bài thực hành xử lý transaction end-to-end:

`Raw Data → Validate → Deduplicate → Join → Window → Aggregate → Partitioned Output`

* Dữ liệu lỗi được tách riêng.
* Duplicate transaction được xử lý theo `updated_at` mới nhất.
* Transaction không mapping customer được giữ lại để kiểm tra.
* Hoàn thành các phép tính tổng hợp theo customer.
* Xác định được top 3 customer theo từng province.
* Dữ liệu hợp lệ được lưu dạng Parquet và partition theo `province`.
* Đọc lại output và kiểm tra count thành công.
* Hiểu rõ hơn cách Spark sử dụng **join, shuffle và sort** trong execution plan.
