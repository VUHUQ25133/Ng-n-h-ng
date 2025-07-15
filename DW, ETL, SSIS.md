# Tổng quan về Data Warehouse (DW)

## 1. Định nghĩa

* **Data Warehouse (DWH)** là kho dữ liệu lớn của một tổ chức, được thiết kế đặc biệt để phục vụ **lập báo cáo và phân tích**.
* Dữ liệu trong DWH được **tổng hợp từ nhiều nguồn**, **làm sạch**, và lưu trữ theo cấu trúc hỗ trợ truy vấn hiệu quả.

## 2. Kiến trúc DWH

### Các vùng dữ liệu chính:

* **ODS (Operational Data Store)**: Lưu trữ dữ liệu hoạt động hàng ngày (sản phẩm, khách hàng, tài khoản...)
* **Staging Area**: Vùng đệm, chứa bản sao dữ liệu từ ODS, phục vụ ETL
* **Data Warehouse**:

  * **Dữ liệu thô đã làm sạch**
  * **Dữ liệu dẫn xuất** (đã tổng hợp, biến đổi)
  * **Siêu dữ liệu** (metadata)
* **Presentation Layer / Data Mart**: Dữ liệu được tổ chức theo nhu cầu phân tích của các phòng ban

### Kiến trúc phổ biến:

* **2 tầng**: Client - Server (Thin/Fat client)
* **3 tầng**:

  1. Dữ liệu thô
  2. Dữ liệu dẫn xuất
  3. Công cụ báo cáo, phân tích

## 3. Các đặc tính của DWH

* **Tính nguyên tử**: Dữ liệu từ nhiều nguồn cần được chuẩn hóa, rút gọn
* **Tính nhất quán**: Chỉ chứa dữ liệu liên quan (cùng chủ đề)
* **Tính cô lập**: Không bị tác động bởi dữ liệu khác
* **Tính bền vững**: Không cho phép cập nhật/xóa như CSDL thông thường

## 4. Nguyên lý thiết kế

* **Hướng chủ đề**: Loại bỏ dữ liệu không phục vụ phân tích
* **Tính toàn vẹn**: Tích hợp dữ liệu vào định dạng thống nhất
* **Tính bất biến**: Dữ liệu không thay đổi theo thời gian
* **Lưu trữ giá trị lịch sử**: Phân tích được các trạng thái qua các mốc thời gian

## 5. Cấu trúc bảng trong DWH

* **Dimension Table**: Bảng chứa các tiêu chí phân tích (thời gian, khách hàng, sản phẩm...)
* **Fact Table**: Bảng chứa dữ liệu định lượng (doanh thu, số lượng bán...)

## 6. Các mô hình lược đồ

### 6.1 Star Schema (Lược đồ hình sao):

* Bảng Fact ở trung tâm, liên kết với các bảng Dimension không phân cấp
* **Ưu điểm**: Truy vấn nhanh, ít bảng, đơn giản
* **Nhược điểm**: Có thể dư thừa dữ liệu

### 6.2 Snowflake Schema (Lược đồ bông tuyết):

* Bảng Dimension được phân cấp
* **Ưu điểm**: Kích thước nhỏ, dễ bảo trì, phù hợp truy vấn phức tạp
* **Nhược điểm**: Nhiều bảng, join phức tạp

### 6.3 Galaxy Schema (Lược đồ thiên hà):

* Kết hợp nhiều Fact Table dùng chung Dimension Table
* Phù hợp với hệ thống có nhiều nghiệp vụ phân tích độc lập nhưng có điểm chung

---

# Tổng quan về ETL

## 1. Khái niệm ETL

* **ETL (Extract - Transform - Load)** là quy trình chuyển dữ liệu từ các nguồn (database, file, API...) sang hệ thống đích (thường là Data Warehouse).
* Bao gồm 3 bước chính:

  1. **Extract (Trích xuất dữ liệu)**: Lấy dữ liệu từ các nguồn
  2. **Transform (Chuyển đổi dữ liệu)**: Làm sạch, chuẩn hóa, tổng hợp, map dữ liệu
  3. **Load (Tải dữ liệu)**: Đưa dữ liệu vào DWH

## 2. Vùng Staging

* **Staging Area** là vùng đệm trung gian chứa dữ liệu trong quá trình ETL
* Chỉ các tiến trình ETL có quyền truy cập
* Có thể lưu trữ bằng:

  * **Flat file (CSV, TXT)**: nhanh, không cần siêu dữ liệu, nhưng không có chỉ mục
  * **Bảng quan hệ**: rõ ràng, toàn vẹn dữ liệu, hỗ trợ SQL

## 3. Trích xuất dữ liệu (Extract)

* **Initial Extraction**: Trích xuất toàn bộ dữ liệu ban đầu
* **Ongoing Extraction**: Chỉ trích xuất phần thay đổi (insert/update/delete)
* Phương pháp xác định thay đổi:

  * Cột thời gian cập nhật
  * So sánh toàn bộ dữ liệu với bản trích trước

## 4. Chuyển đổi dữ liệu (Transform)

* Gồm các thao tác:

  * Làm sạch dữ liệu (remove null, chuẩn hóa format...)
  * Loại bỏ trùng lặp
  * Mapping / ánh xạ
  * Tổng hợp (aggregation)
* Đảm bảo dữ liệu:

  * **Chính xác**, **Nhất quán**, **Đầy đủ**, **Không mập mờ**

## 5. Tải dữ liệu (Load)

* **Tải lần đầu**:

  * Tạo dữ liệu cho dimension table
  * Tạo dữ liệu cho fact table
* **Tải các lần sau**:

  * Phân biệt dữ liệu cập nhật và dữ liệu mới
  * Dùng bulk loader để tăng hiệu năng
  * Có thể phục hồi và tiếp tục nếu gặp lỗi

## 6. Tần suất ETL

* ETL có thể chạy:

  * **Định kỳ**: hằng ngày, tuần, tháng
  * **Real-time**: khi có thay đổi từ nguồn

## 7. Thách thức

* Kết nối hệ thống dị biệt (nhiều loại DB, API, OS...)
* Dữ liệu lớn
* Đảm bảo tính toàn vẹn
* Hỗ trợ khôi phục khi lỗi

## 8. Công cụ ETL phổ biến

| Công cụ                  | Loại      |
| -------------------------------------- | ------------ |
| Pentaho Kettle               | Open source  |
| Talend                  | Open source  |
| Jaspersoft ETL               | Open source  |
| Inaplex Inaport              | Close source |
| SQL Server Integration Services (SSIS) | Close source |

---

# SQL Server Integration Services (SSIS)

## 1. Tổng quan

* **SSIS** là một nền tảng tích hợp dữ liệu của Microsoft dùng để thực hiện các hoạt động **ETL**, **di chuyển dữ liệu**, **biến đổi dữ liệu**, và **tự động hóa quy trình**.
* Được tích hợp trong bộ công cụ của **SQL Server**.

## 2. Thành phần chính

### a. Control Flow

* Điều khiển luồng xử lý chính của package SSIS
* Bao gồm các tác vụ như: gọi quy trình, vòng lặp, điều kiện rẽ nhánh
* Có thể cấu hình logic theo **Success**, **Failure**, **Completion**

### b. Data Flow

* Xử lý dữ liệu chi tiết trong quá trình ETL
* Bao gồm:

  * **Source**: lấy dữ liệu từ nguồn
  * **Transformations**: chuyển đổi dữ liệu
  * **Destination**: ghi dữ liệu đích

## 3. Một số thành phần hỗ trợ

* **Precedence Constraint**: điều kiện điều hướng giữa các task
* **Variables và Expressions**: dùng để truyền giá trị và điều kiện động
* **Event Handler**: xử lý các sự kiện xảy ra khi package chạy

## 4. Logging và Checkpoint

* **Logging**: ghi nhận các hoạt động, lỗi, thông tin thực thi của package
* **Checkpoint**: lưu lại trạng thái tại điểm lỗi để có thể chạy lại từ vị trí đó

## 5. Triển khai và lập lịch SSIS

* **Triển khai**:

  * Triển khai SSIS Project lên SQL Server
  * Tạo catalog database, folder, và deploy package
* **Lập lịch**:

  * Sử dụng SQL Server Agent để lên lịch thực hiện package
  * Có thể cấu hình các bước, thời gian, điều kiện lặp lại
