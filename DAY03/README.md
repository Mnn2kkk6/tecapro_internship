# ⚡ BÁO CÁO NGÀY 3 — THỰC HÀNH PYSPARK & XỬ LÝ DỮ LIỆU ĐƠN HÀNG

🔗 **GitHub:** https://github.com/Mnn2kkk6/pyspark-orders-repo

---

## 🛠️ Công việc đã thực hiện

* Nghiên cứu **PySpark User Guide**, tập trung vào:

  * DataFrame
  * Functions
  * Spark SQL
  * Đọc và ghi dữ liệu

* Thực hành **ETL với PySpark** trên dữ liệu đơn hàng:

  * Tạo file `orders.csv` gồm **200 đơn hàng mẫu**.
  * Tạo DataFrame với **Explicit Schema** sử dụng `StructType` và `StructField`.
  * Thực hành các thao tác xử lý dữ liệu cơ bản:

    * `printSchema`
    * `show`
    * `select`
    * `filter`
    * `groupBy`
    * `count`
    * `sum`
  * Sử dụng **Spark SQL** để truy vấn và tính toán doanh thu theo từng tỉnh.
  * Đọc dữ liệu từ CSV và xuất kết quả thành các file CSV bằng `coalesce(1)`.
  * Hoàn thiện cấu trúc project và đẩy toàn bộ source code lên **GitHub**.

---

## 📚 Tóm tắt kiến thức rút ra được

* Hiểu sự khác nhau và mối liên hệ giữa **DataFrame API** và **Spark SQL**.

* Hiểu vai trò của **Explicit Schema**, đồng thời biết được hạn chế của `inferSchema` khi triển khai trong môi trường production.

* Hiểu cách sử dụng `coalesce(1)` để xuất dữ liệu thành **một file duy nhất**, đồng thời lưu ý không nên lạm dụng với dữ liệu lớn vì có thể gây bottleneck khi dữ liệu bị dồn về một partition.

* Nắm được quy trình **ETL cơ bản bằng PySpark**:

```text
Extract → Transform → Load
   ↓          ↓          ↓
  CSV      PySpark     Output
```

* Bước đầu làm quen với việc xây dựng một **data processing pipeline** bằng PySpark và hiểu cách Spark xử lý dữ liệu thông qua DataFrame và Spark SQL.

---

## ✅ Kết quả

Hoàn thành một project ETL cơ bản sử dụng **PySpark**, từ khâu tạo dữ liệu, đọc dữ liệu, định nghĩa schema, xử lý và phân tích dữ liệu đến xuất kết quả.

Đồng thời củng cố thêm kiến thức về **DataFrame, Spark SQL, Explicit Schema và các thao tác xử lý dữ liệu cơ bản**, tạo nền tảng để tiếp tục thực hành các pipeline dữ liệu phức tạp hơn.

