# 📚 BÁO CÁO NGÀY ĐẦU TIÊN

Đã tìm hiểu và nắm được các khái niệm cơ bản về **Data Lakehouse,so sánh Data Lake với Data Warehouse, Bronze/Silver/Gold, Ingest, ETL/ELT, Data Catalog, Table Format, Spark, MinIO và Nessie**.

Trình bày lại về **khái niệm, tác dụng và ứng dụng thực tế** của các công nghệ trên. Ngoài ra, tiếp tục tìm hiểu thêm về **cách kết hợp Spark và Kafka** trong hệ thống Big Data.

---

# 📝 Tóm tắt ghi nhớ kiến thức

* **Data Lakehouse** là một kiến trúc quản lý dữ liệu được thiết kế để kết hợp những ưu điểm tốt nhất của cả **Data Warehouse (Kho dữ liệu)** và **Data Lake (Hồ dữ liệu)**.

* **Data Lake và Data Warehouse** khác nhau cốt lõi ở cách xử lý dữ liệu thô, cấu trúc lưu trữ và đối tượng phục vụ.

* **Bronze / Silver / Gold** là cách chia dữ liệu thành 3 tầng tùy theo mức độ xử lý:

  * 🥉 **Bronze** = Dữ liệu thô (**Raw Data**)
  * 🥈 **Silver** = Dữ liệu sạch (**Cleaned Data**)
  * 🥇 **Gold** = Dữ liệu đã sẵn sàng để sử dụng cho **AI/BI (Business/AI Ready Data)**

* **Ingest**: Đưa dữ liệu vào một hệ thống để hệ thống có thể xử lý.

  * Ví dụ: file CSV đưa vào Data Warehouse hoặc dữ liệu realtime từ ứng dụng đưa vào Kafka.
  * **Data Ingestion** = quá trình thu thập và đưa dữ liệu từ nguồn vào hệ thống dữ liệu.

* **ETL** (**Extract → Transform → Load**) và **ELT** (**Extract → Load → Transform**):

  * **ETL**: Xử lý dữ liệu trước khi lưu.
  * **ELT**: Lưu dữ liệu trước rồi mới xử lý sau.

* **Data Catalog** là hệ thống quản lý và mô tả dữ liệu, giúp người dùng dễ dàng tìm kiếm và quản lý dữ liệu trong hệ thống.

  * Ví dụ: Công ty có bảng `customers` chứa thông tin khách hàng. Data Catalog giúp nhân viên biết bảng nằm ở đâu, chứa dữ liệu gì và được sử dụng cho mục đích gì.

* **Table Format** = định dạng bảng, giúp tổ chức và quản lý dữ liệu theo cấu trúc hàng và cột, đồng thời hỗ trợ quản lý dữ liệu hiệu quả hơn.

* **Apache Spark** là một công cụ tính toán và xử lý dữ liệu lớn, có khả năng chia nhỏ công việc và thực hiện song song trên nhiều máy tính.

  * Phân tích dữ liệu lớn.
  * Xử lý dữ liệu nhanh nhờ khả năng xử lý trên RAM.
  * Hỗ trợ cả **Batch Processing** và **Streaming**.
  * Hỗ trợ truy vấn **SQL**.
  * Hỗ trợ Machine Learning thông qua **MLlib**.

* **MinIO** là một hệ thống lưu trữ **Object Storage** mã nguồn mở, được sử dụng để lưu trữ nhiều loại dữ liệu như **JSON, CSV, hình ảnh, Parquet,...**

* **Nessie** dùng để quản lý **metadata và version** của các bảng dữ liệu trong Data Lake, có thể hình dung tương tự như **Git dành cho Data Lake**.

