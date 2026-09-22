# ⚡ BÁO CÁO NGÀY 9 — XÂY DỰNG GOLD LAYER VỚI PYSPARK

## 🛠️ Công việc đã thực hiện

Tiếp tục xử lý dữ liệu từ **Silver layer** để xây dựng **Gold layer** cho dữ liệu QTTG BHXH bằng PySpark.

* Viết job `gold_qttg.py` để xử lý dữ liệu Gold.
* Tạo `DIM_THANG` làm danh sách các tháng báo cáo.
* Đọc dữ liệu master và detail từ Silver.
* Join dữ liệu tháng với khoảng thời gian tham gia BHXH `TU_THANG → DEN_THANG`.
* Tổng hợp dữ liệu theo từng tháng báo cáo.
* Tính các chỉ tiêu:

  * `SO_NGUOI_THAM_GIA`
  * `SO_DON_VI`
  * `TONG_QUY_LUONG`
  * `LUONG_BINH_QUAN`
  * `SO_NGUOI_LUONG_0`
* Ghi kết quả Gold ra `output/spark_lake/gold/bao_cao_bhxh_thang`.
* Kiểm tra số liệu sau khi xử lý với dữ liệu Silver.

## 📚 Kiến thức rút ra

Hiểu rõ hơn vai trò của **Gold layer** trong Data Lakehouse:

* **Gold:** chứa dữ liệu đã được tổng hợp theo nghiệp vụ, phục vụ báo cáo và phân tích.
* `DIM_THANG` giúp xác định tập các tháng cần lập báo cáo.
* Sử dụng điều kiện khoảng `TU_THANG → DEN_THANG` để xác định người lao động tham gia BHXH trong từng tháng.
* Có thể sử dụng các hàm tổng hợp để tính số người, số đơn vị và các chỉ tiêu về tiền lương.
* Gold sử dụng dữ liệu đã được làm sạch và chuẩn hóa từ Silver thay vì xử lý trực tiếp dữ liệu raw.

## ✅ Kết quả

Hoàn thành bước xây dựng **Gold layer** cho dữ liệu QTTG BHXH:

* Tạo được báo cáo tổng hợp theo từng tháng.
* Tính được các chỉ tiêu `SO_NGUOI_THAM_GIA`, `SO_DON_VI`, `TONG_QUY_LUONG`, `LUONG_BINH_QUAN` và `SO_NGUOI_LUONG_0`.
* Xử lý được dữ liệu detail quy mô **1.000.000 dòng**.
* Dữ liệu Gold được ghi tại `output/spark_lake/gold/bao_cao_bhxh_thang`.
* Thực hiện kiểm tra và đối chiếu số liệu sau khi chạy.

Qua đó hoàn thành luồng xử lý **Bronze → Silver → Gold**, trong đó Gold cung cấp dữ liệu tổng hợp phục vụ báo cáo QTTG BHXH theo tháng.
