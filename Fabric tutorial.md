# Giới thiệu về Microsoft Fabric

## 1. Giới thiệu

Microsoft Fabric là một nền tảng phân tích đầu-cuối (end-to-end analytics platform) cung cấp môi trường tích hợp duy nhất để các chuyên gia dữ liệu và doanh nghiệp cộng tác trong các dự án dữ liệu. Fabric bao gồm tập hợp các dịch vụ tích hợp cho phép người dùng thu thập (ingest), lưu trữ (store), xử lý (process), và phân tích (analyze) dữ liệu trong cùng một môi trường.

Microsoft Fabric cung cấp công cụ cho cả người dùng chuyên nghiệp và người dùng không chuyên về dữ liệu (citizen data practitioners), đồng thời tích hợp với các công cụ cần thiết cho việc ra quyết định trong doanh nghiệp. Các dịch vụ của Fabric bao gồm:

* Data engineering (Kỹ thuật dữ liệu)
* Data integration (Tích hợp dữ liệu)
* Data warehousing (Kho dữ liệu)
* Real-time intelligence (Trí tuệ thời gian thực)
* Data science (Khoa học dữ liệu)
* Business intelligence (Thông minh doanh nghiệp)

## 2. Khám phá phân tích dữ liệu đầu-cuối với Microsoft Fabric

Phân tích dữ liệu ở quy mô lớn thường phức tạp, phân mảnh và tốn kém. Microsoft Fabric đơn giản hóa giải pháp phân tích bằng cách cung cấp một sản phẩm duy nhất, dễ sử dụng, tích hợp nhiều công cụ và dịch vụ trên một nền tảng thống nhất.

### OneLake

OneLake là kiến trúc lưu trữ dữ liệu tập trung của Fabric, cho phép cộng tác mà không cần sao chép hoặc di chuyển dữ liệu. OneLake được xây dựng trên Azure Data Lake Storage (ADLS), hỗ trợ nhiều định dạng như Delta, Parquet, CSV và JSON.

Tất cả các công cụ tính toán (compute engines) trong Fabric tự động lưu dữ liệu vào OneLake, đảm bảo khả năng truy cập dữ liệu trực tiếp mà không cần di chuyển hoặc sao chép. Dữ liệu dạng bảng sẽ sử dụng định dạng delta-parquet.

**Shortcuts** (đường dẫn tắt) là các tham chiếu đến file hoặc vị trí lưu trữ bên ngoài OneLake, cho phép truy cập dữ liệu đám mây hiện có mà không cần sao chép.

### Workspaces

Workspaces trong Fabric là các vùng chứa logic giúp tổ chức và quản lý dữ liệu, báo cáo và tài nguyên khác. Mỗi workspace có hệ thống phân quyền riêng (admin, contributor, member, viewer), đảm bảo an toàn và hỗ trợ cộng tác.

Workspaces hỗ trợ:

* Quản lý tài nguyên tính toán
* Tích hợp Git để kiểm soát phiên bản
* Tùy chỉnh hiệu suất và chi phí

### Quản trị và quản lý (Administration & Governance)

OneLake được quản lý tập trung và hỗ trợ cộng tác. Fabric có trung tâm quản trị (Admin portal) để:

* Quản lý nhóm và phân quyền
* Cấu hình nguồn dữ liệu và gateway
* Theo dõi hiệu suất sử dụng
* Truy cập API và SDK

**OneLake catalog** cung cấp thông tin nhãn nhạy cảm, siêu dữ liệu và trạng thái cập nhật dữ liệu để hỗ trợ giám sát và cải thiện tuân thủ dữ liệu.

## 3. Khám phá các vai trò dữ liệu trong Microsoft Fabric

Fabric hợp nhất quy trình phát triển phân tích bằng cách tích hợp các công cụ vào nền tảng SaaS duy nhất, giúp loại bỏ silo dữ liệu và tăng khả năng cộng tác.

### Các vai trò:

* **Data engineers**: Nhập, biến đổi, tải dữ liệu vào OneLake bằng Pipelines; sử dụng notebooks cho xử lý nâng cao.
* **Data analysts**: Biến đổi dữ liệu bằng dataflows, tạo báo cáo trực tiếp từ OneLake qua Direct Lake mode.
* **Data scientists**: Dùng notebooks (Python, Spark), kết nối Azure Machine Learning để huấn luyện và triển khai mô hình.
* **Analytics engineers**: Quản lý chất lượng dữ liệu trong lakehouse, tạo mô hình ngữ nghĩa trong Power BI.
* **Low/no-code users**: Tìm kiếm dữ liệu qua OneLake Hub, dùng Power BI templates và dataflows để tự động hóa ETL đơn giản.

## 4. Kích hoạt và sử dụng Microsoft Fabric

### Kích hoạt Fabric

Để sử dụng Fabric, tổ chức cần kích hoạt qua Power BI Admin portal. Các vai trò có thể kích hoạt:

* Fabric admin
* Power Platform admin
* Microsoft 365 admin

Có thể kích hoạt toàn tổ chức hoặc theo nhóm Entra/Microsoft 365. Fabric cũng cung cấp bản dùng thử miễn phí.

### Tạo workspace

Workspace là môi trường cộng tác để tạo và quản lý lakehouse, warehouse và báo cáo. Tất cả dữ liệu được lưu trong OneLake.

Cài đặt Workspace bao gồm:

* Loại license để dùng tính năng Fabric
* Truy cập OneDrive
* Kết nối Azure Data Lake Gen2
* Tích hợp Git
* Thiết lập Spark workload

### Khám phá dữ liệu với OneLake catalog

OneLake Hub cho phép người dùng khám phá dữ liệu trong tổ chức:

* Lọc theo workspace hoặc domain
* Tìm kiếm theo từ khóa hoặc loại mục (item type)

### Tạo mục với Fabric workloads

Sau khi tạo workspace, người dùng có thể tạo mục dữ liệu với các workloads:

* **Data Engineering**: tạo lakehouses, xử lý và chia sẻ dữ liệu
* **Data Factory**: ingest, transform, orchestrate dữ liệu
* **Data Science**: học máy (ML)
* **Data Warehouse**: phân tích dữ liệu từ nhiều nguồn
* **Databases**: quản lý và truy vấn dữ liệu
* **Industry Solutions**: giải pháp dữ liệu ngành
* **Real-Time Intelligence**: xử lý dữ liệu streaming
* **Power BI**: tạo báo cáo và dashboard

Fabric tích hợp các công cụ hiện có như Power BI, Azure Synapse Analytics và Azure Data Factory vào một nền tảng thống nhất, hỗ trợ kiến trúc **data mesh** (mạng dữ liệu), giúp phân quyền dữ liệu hiệu quả mà vẫn đảm bảo quản lý tập trung.

## 5. Câu hỏi trắc nghiệm (Module assessment)

**1. Lợi ích chính khi sử dụng Microsoft Fabric trong các dự án dữ liệu là gì?**

* [ ] Cho phép chuyên gia dữ liệu làm việc độc lập không cần cộng tác
* [ ] Yêu cầu sao chép dữ liệu giữa các hệ thống để đảm bảo khả năng truy cập
* [x] Cung cấp môi trường tích hợp duy nhất để cộng tác trong các dự án dữ liệu

**2. Định dạng lưu trữ mặc định của OneLake là gì?**

* [x] Delta-Parquet
* [ ] JSON
* [ ] CSV

**3. Trải nghiệm nào của Fabric được sử dụng để di chuyển và biến đổi dữ liệu?**

* [ ] Data Science
* [ ] Data Warehousing
* [x] Data Factory

## 6. Tóm tắt

Các chuyên gia dữ liệu ngày càng cần có khả năng làm việc với dữ liệu quy mô lớn, an toàn, tuân thủ và hiệu quả chi phí. Doanh nghiệp cũng cần sử dụng dữ liệu hiệu quả hơn để đưa ra quyết định nhanh chóng.

Microsoft Fabric cung cấp tập hợp công cụ và dịch vụ giúp tổ chức thực hiện điều đó. Trong module này, bạn đã tìm hiểu về:

* Lưu trữ OneLake
* Các workloads có trong Fabric
* Cách kích hoạt và sử dụng Fabric trong tổ chức


Practice: 
1. Một lợi ích đáng kể của schema-on-read trong lakehouse của Microsoft Fabric so với các schema được định nghĩa trước trong các kho dữ liệu truyền thống là gì?
    a. Schema-on-read đảm bảo truy xuất dữ liệu nhanh hơn các schema được định nghĩa trước.
    b. Schema-on-read cho phép nhập và biến đổi dữ liệu linh hoạt hơn.
    c. Schema-on-read yêu cầu ít không gian lưu trữ hơn.

2. Tính năng nào của lakehouse trong Microsoft Fabric hỗ trợ phân tích học máy và mô hình dự đoán?
    a. Công cụ Spark và SQL
    b. Chia sẻ cấp mục
    c. Định dạng schema-on-read

3. Tính năng nào của Microsoft Fabric đảm bảo tính toàn vẹn và nhất quán của dữ liệu trong một lakehouse?
    a. Biến đổi Power Query
    b. Bảng định dạng Delta Lake
    c. Định dạng schema-on-read

4. Công cụ nào nên được sử dụng để nhập và biến đổi dữ liệu có cấu trúc bằng giao diện trực quan trong lakehouse của Microsoft Fabric?
    a. Dataflows Gen2
    b. Notebook Apache Spark
    c. Điểm cuối phân tích SQL

5. Tổ chức của bạn có kế hoạch đào tạo các mô hình học máy sử dụng dữ liệu từ một lakehouse của Microsoft Fabric. Công cụ nào phù hợp nhất để thực hiện nhiệm vụ này?
    a. Notebooks
    b. Dataflows Gen2
    c. Điểm cuối phân tích SQL

6. Trong lakehouse của Microsoft Fabric, bạn nhận thấy các vấn đề không nhất quán dữ liệu khi biến đổi dữ liệu. Tính năng nào của bảng định dạng Delta Lake giúp đảm bảo tính toàn vẹn và nhất quán của dữ liệu?
    a. Phím tắt (Shortcuts)
    b. Định dạng schema-on-read
    c. Giao dịch ACID

7. Một lakehouse của Microsoft Fabric khác với một data lake điển hình về khả năng xử lý dữ liệu như thế nào?
    a. Lakehouse tự động biến đổi tất cả dữ liệu thành các định dạng có cấu trúc.
    b. Data lake vốn dĩ hỗ trợ phân tích thời gian thực mà không cần công cụ bổ sung.
    c. Lakehouse tích hợp công cụ SQL và Spark để xử lý dữ liệu nâng cao.

8. Tổ chức của bạn muốn kết hợp dữ liệu giao dịch có cấu trúc với các nguồn cấp dữ liệu mạng xã hội để phân tích. Tại sao một lakehouse của Microsoft Fabric có thể phù hợp hơn một kho dữ liệu truyền thống?
    a. Lakehouse có thể lưu trữ tất cả các định dạng dữ liệu và hỗ trợ phân tích dựa trên SQL.
    b. Lakehouse yêu cầu ít không gian lưu trữ hơn kho dữ liệu.
    c. Kho dữ liệu truyền thống không hỗ trợ truy vấn SQL.

9. Khi thiết kế quy trình ETL cho một lakehouse của Microsoft Fabric, công cụ nào có thể được sử dụng để trực quan hóa các biến đổi mà không cần lập trình truyền thống?
    a. Notebooks
    b. Điểm cuối phân tích SQL
    c. Dataflows Gen2