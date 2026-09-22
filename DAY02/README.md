# 🚀 BÁO CÁO NGÀY 2

Đã hoàn thành việc **cài đặt và thiết lập môi trường** cho các công nghệ/framework phục vụ hệ thống Big Data, bao gồm:

* **Docker & Docker Compose**: Sử dụng để tạo và quản lý môi trường chạy các service/container.
* **Apache Spark / PySpark**: Cài đặt và thiết lập môi trường xử lý dữ liệu phân tán bằng Python.
* **Java**: Cài đặt JDK, là môi trường cần thiết để Spark hoạt động.
* **MinIO**: Thiết lập Object Storage để lưu trữ dữ liệu theo mô hình tương tự S3.
* **Apache Iceberg**: Tìm hiểu và thiết lập Table Format để quản lý dữ liệu dạng bảng trên Data Lake.
* **Project Nessie**: Thiết lập Data Catalog hỗ trợ quản lý metadata và versioning cho Iceberg Tables.

---

## 🛠️ Cách thực hiện

Tiến hành kiểm tra và cài đặt từng thành phần, sau đó kiểm tra lại **phiên bản và khả năng hoạt động** của các framework thông qua Terminal/PowerShell.

Đối với hệ thống Big Data, sử dụng **Docker Compose** để định nghĩa và chạy các service trong cùng một hệ thống. Việc sử dụng Docker giúp các thành phần như **Spark, MinIO, Iceberg và Nessie** hoạt động trong môi trường độc lập, đồng thời dễ dàng kết nối và quản lý.

---

## 🏗️ Hệ thống nhỏ đã build

Thực hành build một hệ thống Big Data cơ bản trên Docker với các thành phần chính:

```text
             Data / Files
                  │
                  ▼
             ┌─────────┐
             │  Spark  │
             │ PySpark │
             └────┬────┘
                  │
                  ▼
             ┌─────────┐
             │ Iceberg │
             └────┬────┘
                  │
          ┌───────┴───────┐
          ▼               ▼
      ┌────────┐      ┌────────┐
      │  MinIO │      │ Nessie │
      │ Storage│      │ Catalog│
      └────────┘      └────────┘
```

Trong quá trình thực hành, làm quen với:

1. Khởi chạy các container bằng **Docker Compose**.
2. Kết nối **Spark/PySpark** với các service trong Docker Network.
3. Sử dụng **PySpark** để thực hiện một số thao tác xử lý dữ liệu cơ bản.
4. Tìm hiểu cách lưu trữ dữ liệu trên **MinIO**.
5. Tìm hiểu cách **Iceberg** quản lý dữ liệu dạng Table trên Data Lake.
6. Tìm hiểu vai trò của **Nessie** trong việc quản lý Catalog và Metadata của Iceberg.
7. Thực hành **build, start, stop** và kiểm tra trạng thái các container trong hệ thống.

---

## ✅ Kết quả

Đến cuối ngày, đã hoàn thành việc **thiết lập môi trường** và bước đầu hiểu được cách các công nghệ:

**Docker + Spark/PySpark + MinIO + Iceberg + Nessie**

kết hợp với nhau để xây dựng một hệ thống **xử lý và lưu trữ dữ liệu Big Data**.

Hoàn thành thêm một số bài tập cơ bản để làm quen với **Spark/PySpark và Docker**, đồng thời hiểu rõ hơn về quy trình **build, triển khai và vận hành** một hệ thống Big Data trên Docker.
