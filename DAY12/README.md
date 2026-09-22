# ⚡ BÁO CÁO NGÀY 12 — JOIN TRONG PYSPARK

## 🛠️ Công việc đã thực hiện

Thực hành các kỹ thuật **Join trong PySpark** và xử lý dữ liệu không mapping được.

* Tạo 2 dataset `orders` và `customers`.
* Thực hành `inner join` và `left join`.
* Tạo trường hợp `order` không tìm thấy `customer` tương ứng.
* Tách các record thành 2 nhóm **mapped** và **unmapped**.
* So sánh kết quả giữa `inner join` và `left join`.

## 📚 Kiến thức rút ra

Hiểu rõ hơn cách sử dụng **Join trong ETL**:

* `Inner Join` chỉ giữ các record có dữ liệu mapping ở cả hai bảng.
* `Left Join` giữ lại toàn bộ dữ liệu từ bảng bên trái, kể cả khi không tìm thấy bản ghi tương ứng.
* Các record **unmapped** cần được giữ lại để kiểm tra và xử lý dữ liệu nguồn.
* Việc kiểm soát dữ liệu không mapping giúp phát hiện các vấn đề về khóa liên kết và chất lượng dữ liệu trong quá trình ETL.

## ✅ Kết quả

Hoàn thành bài thực hành **Join trong PySpark**, thực hiện được `inner join`, `left join`, phân loại mapped/unmapped và hiểu vai trò của việc giữ lại dữ liệu không mapping trong quy trình ETL.
