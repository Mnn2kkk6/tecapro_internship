# ⚡ BÁO CÁO NGÀY 12 — JOIN VÀ XỬ LÝ DỮ LIỆU GIAO DỊCH TRONG PYSPARK

## 🛠️ Công việc đã thực hiện

### Bài 1 — Join và xử lý dữ liệu không mapping

Thực hành các kỹ thuật **Join trong PySpark** với hai dataset `orders` và `customers`.

* Tạo dữ liệu `orders` và `customers`.
* Thực hiện **Inner Join** và **Left Join**.
* Tạo trường hợp order không tìm thấy customer tương ứng.
* Tách dữ liệu thành hai nhóm **mapped** và **unmapped**.
* So sánh kết quả giữa `inner join` và `left join`.
* Kiểm tra dữ liệu không mapping để phục vụ việc kiểm tra chất lượng dữ liệu.

### Bài 2 — Xử lý transaction end-to-end

Thực hành flow xử lý dữ liệu thực tế với `customers.csv` và `transactions.csv`.

* Khai báo schema thủ công, không sử dụng `inferSchema`.
* Validate dữ liệu và tách record lỗi:

  * Thiếu `customer_id`.
  * `amount <= 0`.
* Xử lý duplicate `transaction_id` bằng **Window Function**, giữ record có `updated_at` mới nhất.
* Join transactions với customers bằng **Left Join**.
* Tách các transaction không mapping được customer.
* Dùng Window Function để tìm transaction gần nhất của từng customer.
* Tính tổng số transaction, tổng amount và số transaction `SUCCESS` theo customer.
* Tìm top 3 customer có tổng amount cao nhất theo từng province.
* Ghi dữ liệu hợp lệ ra Parquet và partition theo `province`.
* Ghi dữ liệu lỗi và unmapped ra output riêng.
* Đọc lại output và kiểm tra count sau khi ghi.
* Sử dụng `explain()` để quan sát execution plan và các bước có `join`, `shuffle`, `sort`.

## 📚 Kiến thức rút ra

* Hiểu sự khác nhau giữa **Inner Join** và **Left Join** trong ETL.
* Hiểu vai trò của việc giữ lại dữ liệu **unmapped** để kiểm tra chất lượng dữ liệu.
* Biết sử dụng **Window Function** để xử lý duplicate theo điều kiện thay vì chỉ dùng `dropDuplicates()`.
* Hiểu cách sử dụng Window để tìm bản ghi mới nhất hoặc transaction gần nhất.
* Biết kết hợp `groupBy` và aggregation để tạo các chỉ số theo customer.
* Hiểu cách partition dữ liệu Parquet theo `province`.
* Biết sử dụng `explain()` để quan sát execution plan.
* Nhận biết các bước **join, window, aggregation** có thể tạo shuffle và tiêu tốn tài nguyên khi dữ liệu tăng lên.
* Hiểu rõ hơn flow xử lý dữ liệu:

`Raw Data → Validate → Deduplicate → Join → Window → Aggregate → Partitioned Output`

## ✅ Kết quả

Hoàn thành cả hai bài thực hành về **Join và xử lý dữ liệu bằng PySpark**.

* Thực hiện được Inner Join, Left Join và xử lý dữ liệu unmapped.
* Hoàn thành pipeline transaction từ validate đến output Parquet.
* Xử lý được duplicate transaction và dữ liệu lỗi.
* Hoàn thành các phép tính tổng hợp theo customer và province.
* Kiểm tra được execution plan bằng `explain()`.
* Đọc lại output và kiểm tra count sau khi ghi.
* Củng cố quy trình xử lý dữ liệu thực tế bằng PySpark từ **raw data đến dữ liệu đã được làm sạch và tổng hợp**.
