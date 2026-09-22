# ⚡ BÁO CÁO NGÀY 8 — XÂY DỰNG SILVER LAYER VỚI PYSPARK

## 🛠️ Công việc đã thực hiện

Tiếp tục xử lý dữ liệu từ **Bronze layer** để xây dựng **Silver layer** cho dữ liệu QTTG BHXH bằng PySpark.

* Viết job `silver_qttg.py` để xử lý dữ liệu Silver.
* Đọc dữ liệu `RAW_QTTG_BHXH` và `RAW_QTTG_BHXH_DETAIL` từ Bronze.
* Với bảng master, sử dụng `row_number()` để chọn bản ghi mới nhất của mỗi `SO_SO_BHXH`:

  * `partitionBy(SO_SO_BHXH)`
  * `orderBy(CREATED_AT desc, ID desc)`
  * Chỉ giữ bản ghi có `row_number = 1`.
* Với bảng detail, chỉ giữ các bản ghi thuộc những `MASTER_ID` đã được chọn ở master Silver.
* Chuẩn hóa dữ liệu `TU_THANG` và `DEN_THANG`.
* Kiểm tra định dạng tháng theo `YYYYMM`.
* Cast `MUC_LUONG` sang kiểu dữ liệu số khi cần thiết.
* Kiểm tra và xử lý các record có dữ liệu tháng không hợp lệ hoặc không liên kết được với master.

## 📚 Kiến thức rút ra

Hiểu rõ hơn vai trò của **Silver layer** trong Data Lakehouse:

* **Silver:** làm sạch, chuẩn hóa và xử lý các quy tắc nghiệp vụ trên dữ liệu từ Bronze.
* Sử dụng **Window Function** với `row_number()` để xác định bản ghi master mới nhất theo từng `SO_SO_BHXH`.
* Khi có cùng `CREATED_AT`, sử dụng `ID desc` làm điều kiện ưu tiên tiếp theo để xác định bản ghi mới nhất.
* Detail phải được lọc theo các `MASTER_ID` hợp lệ của master Silver để đảm bảo quan hệ **master-detail** chính xác.
* Kiểm tra định dạng `TU_THANG`, `DEN_THANG` giúp đảm bảo dữ liệu thời gian có thể sử dụng cho các bước phân tích tiếp theo.
* Kiểm tra kiểu dữ liệu và các bản ghi lỗi giúp nâng cao chất lượng dữ liệu trước khi đưa sang Gold layer.

## ✅ Kết quả

Hoàn thành bước xử lý **Silver layer** cho dữ liệu QTTG BHXH:

* Mỗi `SO_SO_BHXH` chỉ còn **1 bản ghi master mới nhất**.
* Bản ghi mới nhất được xác định dựa trên `CREATED_AT desc, ID desc`.
* Detail Silver chỉ chứa các bản ghi thuộc **master Silver**.
* Dữ liệu `TU_THANG`, `DEN_THANG` được chuẩn hóa và kiểm tra theo format `YYYYMM`.
* `MUC_LUONG` được chuyển sang kiểu số phù hợp.
* Thực hiện kiểm tra các lỗi về định dạng tháng và liên kết `MASTER_ID`.

Dữ liệu Silver sau khi xử lý được ghi tại:

* `output/spark_lake/silver/qttg_bhxh`
* `output/spark_lake/silver/qttg_bhxh_detail`

Qua đó hoàn thành bước **làm sạch và xử lý nghiệp vụ từ Bronze → Silver**, tạo dữ liệu đầu vào phù hợp cho bước tổng hợp tại **Gold layer**.
