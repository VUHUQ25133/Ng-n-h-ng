# Tổng quan về Phân tích & Trực quan hóa Dữ liệu với Power BI

## 1. Phân tích dữ liệu và Trực quan hóa dữ liệu

### 1.1 Kiến trúc và sự tiến hóa dữ liệu 

* Dữ liệu trong doanh nghiệp phát triển theo thời gian từ đơn giản đến phức tạp:

  * **Dữ liệu đơn giản**: biến, con trỏ, struct, list, stack, queue.
  * **Dữ liệu có cấu trúc**: dữ liệu bán hàng, lưu trữ trong RDBMS → SQL.
  * **Dữ liệu phân tán**: từ nhiều hệ thống → cần tích hợp, phân tích → Data Warehouse.
  * **Dữ liệu phi cấu trúc**: văn bản, ảnh, video, hành vi người dùng → NoSQL, Big Data, Data Lake.

### 1.2 Xử lý giao dịch và phân tích dữ liệu

* **Xử lý giao dịch (OLTP - Online Transaction Processing)**:

  * Là các thao tác như: đặt hàng, xuất hóa đơn, rút tiền…
  * Cần tốc độ xử lý cao, độ tin cậy lớn.
  * Hệ thống OLTP xử lý dữ liệu hiện tại, tập trung vào tính nhất quán.

* **Phân tích dữ liệu (OLAP - Online Analytical Processing)**:

  * Dựa trên tổng hợp dữ liệu để đưa ra quyết định chiến lược.
  * Truy vấn phức tạp theo nhiều chiều (sản phẩm, thời gian, khu vực…)
  * Hệ thống OLAP thường truy cập dữ liệu lịch sử, phục vụ báo cáo và phân tích.

### 1.3 Bảng so sánh chi tiết OLTP vs OLAP

| Tiêu chí       | OLTP                      | OLAP                      |
| ----------------- | ------------------------------------------ | -------------------------------------------- |
| Mục đích       | Xử lý giao dịch nghiệp vụ hằng ngày    | Hỗ trợ phân tích và ra quyết định       |
| Người dùng    | Nhân viên vận hành (kế toán, bán hàng...)  | Quản lý, lãnh đạo, nhà phân tích dữ liệu   |
| Cấu trúc dữ liệu  | Dữ liệu chi tiết, thường xuyên cập nhật  | Dữ liệu tổng hợp, có tính lịch sử       |
| Kiểu truy vấn   | Ngắn, đơn giản (select, insert, update...) | Phức tạp, nhiều phép toán tổng hợp      |
| Số lượng truy cập | Nhiều người dùng đồng thời          | Ít người dùng hơn, nhưng yêu cầu cao      |
| Hiệu năng      | Tối ưu hóa cho tốc độ ghi dữ liệu       | Tối ưu hóa cho tốc độ đọc và truy vấn    |
| Tính nhất quán  | Rất cao, yêu cầu chặt chẽ          | Có thể dùng snapshot, không yêu cầu tức thời |

### 1.4 Mô hình dữ liệu nhiều chiều

* OLAP sử dụng mô hình **dữ liệu khối (cube)** để biểu diễn dữ liệu:

  * **Fact Table**: chứa số liệu định lượng (doanh thu, số lượng bán...)
  * **Dimension Table**: chứa thông tin mô tả (thời gian, sản phẩm, khu vực...)
* Cho phép phân tích theo nhiều chiều đồng thời.
* Có thể áp dụng các thuật toán phân tích:

  * Phân lớp (classification)
  * Phân cụm (clustering)
  * Dự báo (forecasting)
  * Khai thác luật kết hợp (association rules)

### 1.5 Trực quan hóa dữ liệu

* Trực quan hóa là việc biến đổi dữ liệu thành hình ảnh dễ hiểu:

  * Biểu đồ (chart), bản đồ (map), bảng (table), dashboard...
* **Lợi ích:**

  * Dễ hiểu, dễ trình bày cho người không chuyên
  * Phát hiện nhanh xu hướng, bất thường, điểm nổi bật
  * Giúp đưa ra quyết định nhanh và chính xác hơn
* **Hạn chế:**

  * Có thể gây hiểu lầm nếu trình bày sai, hoặc thiếu logic
  * Biểu đồ bị ảnh hưởng bởi cách chọn màu, loại biểu diễn, tỷ lệ...

### 1.6 Các hình thức trực quan hóa phổ biến

* **Biểu đồ:**

  * Cột (bar), đường (line), tròn (pie), vùng (area), phân tán (scatter), bong bóng (bubble)...
* **Bản đồ:**

  * Gắn dữ liệu với không gian địa lý
* **Dashboard:**

  * Trang tổng hợp nhiều biểu đồ để giám sát, phân tích thời gian thực
* **Infographics:**

  * Trình bày số liệu bằng hình ảnh minh họa, biểu tượng, văn bản

## 2. Power BI (Chi tiết hơn)

### 2.1 Giới thiệu Power BI

* Power BI là bộ công cụ của Microsoft cho phép:

  * Kết nối đến nhiều nguồn dữ liệu (file, cơ sở dữ liệu, web...)
  * Làm sạch, biến đổi dữ liệu với Power Query
  * Mô hình hóa dữ liệu với Power Pivot
  * Trực quan hóa dữ liệu với nhiều biểu đồ sinh động
* Gồm 2 thành phần chính:

  * **Power BI Desktop**: xây dựng báo cáo
  * **Power BI Service**: chia sẻ, cộng tác trên cloud

### 2.2 Dashboard & Report

* **Report**:

  * Gồm nhiều trang, nhiều biểu đồ tương tác.
  * Có thể drill down, drill through giữa các cấp độ dữ liệu.
* **Dashboard**:

  * Trang tổng quan từ nhiều nguồn report khác nhau.
  * Dùng để theo dõi hiệu suất hoạt động theo thời gian thực.

### 2.3 Các loại biểu đồ phổ biến trong Power BI

* **Bar Chart / Column Chart**: so sánh giá trị giữa các danh mục.
* **Line Chart**: hiển thị xu hướng theo thời gian.
* **Area Chart**: như line chart nhưng biểu diễn thêm khối lượng.
* **Pie/Donut Chart**: biểu diễn cơ cấu thành phần theo phần trăm.
* **Gauge Chart**: theo dõi mức độ đạt KPI.
* **Scatter/Bubble Chart**: phân tích mối tương quan giữa biến.
* **Map Visuals**: biểu diễn dữ liệu trên bản đồ địa lý.
* **Card, Table, Matrix, Slicer**: hiển thị giá trị cụ thể và bộ lọc tương tác.

### 2.4 Kỹ thuật trình bày & thiết kế báo cáo

* **Màu sắc**: dùng màu tương phản, tuân thủ nguyên tắc thẩm mỹ và tiếp cận
* **Trục & nhãn**: đặt rõ ràng, dễ hiểu
* **Sắp xếp**: theo logic: từ tổng quan đến chi tiết
* **Tương tác**: dùng slicer, drill down để nâng cao trải nghiệm người dùng

### 2.5 Góc nhìn phân tích (Business Use Cases)

* Tổng hợp các KPI chính:

  * Doanh thu, số đơn hàng, số khách hàng, % hoàn thành kế hoạch
* Phân tích theo:

  * Nhóm sản phẩm
  * Vùng địa lý
  * Nhân viên
  * Thời gian (ngày, tháng, quý, năm)
* Câu hỏi thường gặp:

  * Top sản phẩm bán chạy?
  * Nhân viên nào có doanh số cao nhất?
  * Doanh thu theo từng khu vực ra sao?
  * So sánh thực tế và kế hoạch tháng này?

## 3. DAX và Tính năng nâng cao của Power BI

### 3.1 Giới thiệu DAX (Data Analysis Expressions)

* DAX là ngôn ngữ dùng trong Power BI để thực hiện tính toán động
* Cho phép tạo:

  * **Calculated Columns**: cột mới dựa trên dữ liệu có sẵn
  * **Measures**: tính toán động như tổng doanh thu, tỷ lệ tăng trưởng
  * **Tables**: tạo bảng mới từ điều kiện lọc/phép toán

### 3.2 Nhóm hàm DAX phổ biến

* **Hàm tập hợp**: `SUM`, `AVERAGE`, `COUNT`, `MIN`, `MAX`, `DISTINCTCOUNT`, ...
* **Hàm thời gian**: `YEAR`, `MONTH`, `NOW`, `TODAY`, `DATEDIFF`, `CALENDAR`...
* **Hàm lọc dữ liệu**: `FILTER`, `ALL`, `REMOVEFILTERS`, `KEEPFILTERS`, ...
* **Hàm logic**: `IF`, `SWITCH`, `AND`, `OR`
* **Hàm quan hệ**: `RELATED`, `RELATEDTABLE` - khai thác dữ liệu từ các bảng liên kết

### 3.3 Drill Down & Drill Through

* **Drill Down**:

  * Cho phép đi sâu vào cấp dữ liệu cụ thể hơn (ví dụ: từ năm → quý → tháng → ngày)
  * Áp dụng cho biểu đồ có phân cấp như thời gian, địa lý, danh mục sản phẩm

* **Drill Through**:

  * Cho phép chuyển sang một trang khác chi tiết hơn, dựa vào dữ liệu được chọn
  * Ví dụ: từ dashboard doanh thu tổng → chi tiết đơn hàng của 1 nhân viên

### 3.4 Phân quyền trong Power BI

* Đảm bảo an toàn và phù hợp theo vai trò người dùng:

  * **Row-Level Security (RLS)**: ẩn/hiện dữ liệu theo từng người dùng dựa trên dòng dữ liệu
  * **Object-Level Security (OLS)**: giới hạn truy cập vào bảng hoặc trường cụ thể

### 3.5 Tính năng phân tích nâng cao

* **Min/Max/Average/Median/Percentile Line**: hiển thị đường chỉ số thống kê trên biểu đồ
* **Find Anomalies**: tự động phát hiện điểm bất thường trong dữ liệu
* **Trend Line**: thêm đường xu hướng để thấy được quỹ đạo dữ liệu
* **Forecast**: dự báo xu hướng tương lai dựa trên dữ liệu lịch sử
