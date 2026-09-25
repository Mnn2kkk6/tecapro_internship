# ⚡ BÁO CÁO NGÀY 15 — PYSPARK READ/WRITE NÂNG CAO

## 🔗 Link GitHub

https://github.com/Mnn2kkk6/pyspark-lab

## 🛠️ Công việc đã thực hiện

Tiếp tục thực hành các thao tác **Read/Write trong PySpark**, tập trung vào schema, kiểm tra dữ liệu, Parquet, partition và các chế độ ghi dữ liệu.

* Khai báo **StructType** tường minh cho dữ liệu đầu vào thay vì sử dụng `inferSchema`.
* Đọc dữ liệu CSV và kiểm tra schema, số lượng bản ghi và giá trị null.
* Chuẩn hóa dữ liệu `status` và kiểm tra tính hợp lệ của `amount`, `order_date`, `province`.
* Tách dữ liệu thành `valid_orders` và `invalid_orders`, đồng thời ghi nhận nguyên nhân lỗi qua `error_reason`.
* Ghi dữ liệu hợp lệ dưới dạng **Parquet** theo hai cách:

  * Ghi Parquet thông thường.
  * Ghi Parquet với `partitionBy("province")`.
* Thực hành và so sánh hai chế độ ghi **append** và **overwrite**.
* Đọc lại dữ liệu Parquet sau khi ghi để kiểm tra schema, số lượng bản ghi và dữ liệu theo từng province.
* Sử dụng `exceptAll` hai chiều để kiểm tra dữ liệu trước và sau khi ghi có khớp hoàn toàn hay không.

## 📚 Kiến thức rút ra

Hiểu rõ hơn cách PySpark xử lý dữ liệu trong quá trình **read → validate → write → read lại**:

* **Schema tường minh** giúp kiểm soát kiểu dữ liệu và hạn chế rủi ro khi dữ liệu nguồn thay đổi.
* **Validation** giúp phân loại dữ liệu hợp lệ và không hợp lệ trước khi đưa vào các bước xử lý tiếp theo.
* **Parquet** phù hợp cho việc lưu trữ dữ liệu phân tích nhờ hỗ trợ schema và định dạng cột.
* `partitionBy()` giúp tổ chức dữ liệu vật lý theo các cột thường được sử dụng để filter, hỗ trợ **partition pruning** khi truy vấn.
* `append` giữ lại dữ liệu cũ và thêm dữ liệu mới, trong khi `overwrite` thay thế dữ liệu hiện có.
* Sử dụng `append` nhiều lần cho cùng một batch có thể dẫn đến **duplicate data** nếu không có cơ chế kiểm soát.
* Số lượng file `part-*` phụ thuộc vào số partition của DataFrame khi ghi dữ liệu.
* Partition theo cột có cardinality quá cao có thể gây **small file problem** và làm giảm hiệu năng.
* Việc đọc lại dữ liệu sau khi ghi giúp kiểm chứng tính toàn vẹn của pipeline.

## ✅ Kết quả

Hoàn thành bài thực hành **PySpark Read/Write nâng cao**:

* Phân loại được dữ liệu thành **90 dòng hợp lệ** và **15 dòng không hợp lệ** trên bộ dữ liệu mẫu.
* Ghi thành công dữ liệu hợp lệ dưới dạng Parquet thông thường và Parquet có partition theo `province`.
* Kiểm chứng được sự khác nhau giữa `append` và `overwrite`.
* Sau khi `overwrite`, dữ liệu được ghi bằng `append` trước đó không còn tồn tại.
* Đọc lại Parquet và kiểm tra schema, số lượng bản ghi, số lượng và tổng `amount` theo province.
* Sử dụng `exceptAll` để xác nhận dữ liệu trước và sau khi ghi **khớp 100%**.

Qua bài thực hành, củng cố quy trình xử lý dữ liệu bằng PySpark từ **đọc dữ liệu, kiểm tra chất lượng, ghi Parquet đến kiểm chứng dữ liệu sau khi lưu trữ**, đồng thời hiểu rõ hơn về **partitioning và các chế độ write**.
