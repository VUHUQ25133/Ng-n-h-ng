## **Bài giảng: Data Pipeline - Đường ống dữ liệu**

---

### 1. Khái niệm về Data Pipeline

Chúng ta đã nhắc đến "pipeline" (đường ống) khá nhiều lần, giờ là lúc tìm hiểu rõ hơn. Nếu dữ liệu là "dầu mỏ mới" như tờ The Economist từng ví von vào năm 2017, thì quá trình xử lý dữ liệu cũng giống như quy trình lọc dầu vậy.

### 2. So sánh với quy trình lọc dầu

* **Khai thác**: Dầu thô được hút lên từ các giếng dầu.
* **Vận chuyển**: Dầu thô được dẫn qua các đường ống.
* **Chưng cất**: Dầu được tách thành các thành phần như dầu nặng, dầu diesel, dầu hỏa (kerosene), naphtha, xăng (gasoline)...
* **Phân phối**:

  * Dầu hỏa đến thẳng sân bay.
  * Xăng được lưu trữ tại các bồn chứa và chuyển đến các trạm xăng.
  * Naphtha được chuyển hóa hóa học thành nhựa dùng cho sản phẩm như đĩa CD.

Tất cả các bước này được kết nối bởi hệ thống đường ống – đó chính là hình ảnh tương tự với hệ thống dữ liệu.

### 3. Quay lại với Data Engineering

Tại công ty giải trí số Spotflix, dữ liệu được thu thập từ nhiều nguồn:

* Ứng dụng Spotflix trên **điện thoại**
* Ứng dụng Spotflix trên **máy tính**
* **Website** Spotflix
* Các hệ thống nội bộ như **HRM**

Tất cả dữ liệu này được **ingest** (nạp) vào hệ thống và đưa vào **data lake** – hồ dữ liệu (sẽ học kỹ ở chương sau).

### 4. Xây dựng các Pipeline đầu tiên

Sau khi dữ liệu được đưa vào, ta xây dựng các pipeline để chuyển dữ liệu vào các **cơ sở dữ liệu** khác nhau:

* **Artists**: tên, số lượng người theo dõi, nghệ sĩ liên quan
* **Albums**: tên hãng đĩa, nhà sản xuất, năm phát hành
* **Tracks**: tên bài hát, độ dài, nghệ sĩ hợp tác, số lượt nghe
* **Playlists**: tên danh sách, các bài hát trong danh sách, ngày tạo
* **Customers**: tên người dùng, ngày mở tài khoản, gói dịch vụ
* **Employees**: tên, lương, người quản lý, cập nhật bởi phòng nhân sự

Tổng cộng: **6 pipeline mới**.

### 5. Một số pipeline đặc biệt khác

* **Album covers**: Ảnh bìa album cùng định dạng, lưu trực tiếp.
* **Employees theo phòng ban**: sales, engineering, support...
* **Employees theo quốc gia**: Mỹ, Bỉ, Anh...

Nếu nhà phân tích dữ liệu muốn nghiên cứu về tỷ lệ nghỉ việc, họ sẽ dùng các dữ liệu này.

### 6. Xử lý và làm sạch dữ liệu

Một pipeline quan trọng khác:

* **Tracks** cần được kiểm tra:

  * Có thể đọc được không?
  * Nghệ sĩ có tồn tại không?
  * Định dạng và kích thước đúng không?

\=> Sau khi xử lý, lưu vào **clean tracks database**, dùng cho việc gợi ý bài hát tương tự.

### 7. Tổng kết vai trò của Data Pipeline

Data pipeline đảm bảo dòng chảy dữ liệu xuyên suốt tổ chức. Chúng **tự động hóa** các bước:

* Trích xuất (Extract)
* Biến đổi (Transform)
* Nạp vào cơ sở dữ liệu (Load)

\=> Giảm lỗi do con người, tăng tốc độ xử lý dữ liệu.

### 8. ETL và Data Pipeline

* **ETL** là mô hình phổ biến trong thiết kế pipeline:

  * **E**: Extract – trích xuất dữ liệu
  * **T**: Transform – xử lý dữ liệu
  * **L**: Load – nạp dữ liệu đã xử lý
* Không phải pipeline nào cũng tuân theo ETL. Có pipeline chỉ chuyển dữ liệu đến công cụ như Tableau hoặc Salesforce mà không cần biến đổi.

### 9. Kết luận chương 1

Giờ bạn đã hiểu:

* Pipeline là gì
* Dùng để làm gì
* Tại sao nó quan trọng
* Ứng dụng của nó tại Spotflix
* ETL nằm ở đâu trong hệ thống

### 10. Thực hành chương 1

Hãy cùng làm vài bài tập để củng cố kiến thức, rồi ta sẽ bước sang **Chương 2**: lưu trữ dữ liệu.

---

## **Bài giảng: Chương 2 – Cấu trúc dữ liệu và lưu trữ**

### 1. Giới thiệu

Chúc mừng bạn đã hoàn thành Chương 1! Giờ chúng ta sẽ đến với chương thứ hai, tập trung vào việc lưu trữ dữ liệu, bắt đầu bằng tìm hiểu về **cấu trúc dữ liệu**.

### 2. Dữ liệu có cấu trúc (Structured Data)

* Là loại dữ liệu **dễ tìm kiếm và tổ chức**.
* Tuân theo **một cấu trúc cứng nhắc**, giống như bảng tính (Excel): mỗi cột có kiểu dữ liệu xác định (chữ, số, ngày tháng…).
* Dễ dàng xây dựng mối quan hệ => hình thành cơ sở dữ liệu **quan hệ** (Relational Database).
* Khoảng **20% dữ liệu hiện nay** là có cấu trúc.
* Dữ liệu dạng này thường được truy vấn bằng **SQL (Structured Query Language)**.

### 3. Ví dụ bảng nhân viên

* Bảng nhân viên của Spotflix là ví dụ điển hình:

  * Mỗi hàng là 1 nhân viên.
  * Mỗi cột là 1 thông tin: tên, phòng ban, chức vụ…
  * Một số cột là kiểu logic (true/false), như "làm bán thời gian hay không".
  * Mỗi hàng có **ID duy nhất** để phân biệt, kể cả khi trùng tên.

### 4. Cơ sở dữ liệu quan hệ

* Vì có cấu trúc, ta có thể kết nối bảng này với bảng khác (ví dụ bảng văn phòng) thông qua một cột chung như "office".
* Các bảng liên kết với nhau như vậy tạo thành **cơ sở dữ liệu quan hệ**.

### 5. Dữ liệu bán cấu trúc (Semi-structured Data)

* Có cấu trúc tương đối, nhưng **linh hoạt hơn nhiều**.
* Vẫn có thể tổ chức và nhóm để tạo quan hệ, nhưng **không dễ dàng như structured data**.
* Thường được lưu trữ trong **NoSQL database**, định dạng phổ biến: **JSON**, **XML**, **YAML**.

### 6. Ví dụ JSON yêu thích nghệ sĩ

* Một file JSON lưu danh sách nghệ sĩ yêu thích theo từng người dùng Spotflix.
* Dữ liệu có mô hình lặp lại, nhưng **không cố định số lượng nghệ sĩ yêu thích**.

  * Ví dụ: Tôi có 4 nghệ sĩ, Sara có 2, Lis có 3.
* Cơ sở dữ liệu quan hệ không cho phép sự linh hoạt này, nhưng **dữ liệu bán cấu trúc thì có thể**.

### 7. Dữ liệu phi cấu trúc (Unstructured Data)

* **Không tuân theo bất kỳ mô hình nào**, không thể tổ chức thành hàng – cột.
* Khó tìm kiếm và tổ chức.
* Dạng phổ biến: văn bản, âm thanh, hình ảnh, video…
* Được lưu trong **data lake** (hoặc warehouse).
* Chiếm **đa số dữ liệu trong thế giới thực**.
* Trước đây không thể tận dụng, nhưng giờ với **machine learning và AI**, ta có thể khai thác giá trị từ chúng.

### 8. Ví dụ tại Spotflix

* Lời bài hát
* Bài hát (file nhạc)
* Ảnh album, ảnh nghệ sĩ
* Video âm nhạc

### 9. Thêm cấu trúc cho dữ liệu phi cấu trúc

* Có thể dùng **machine learning** để phân tích nhịp độ, hợp âm, thể loại...
* Hoặc yêu cầu nghệ sĩ cung cấp thêm thông tin khi tải lên (thể loại, thẻ – tags).
* Điều này biến **dữ liệu phi cấu trúc** thành **bán cấu trúc**, giúp dễ tìm kiếm hơn.

### 10. Tổng kết chương 2

Giờ bạn đã biết:

* Đặc điểm của **structured**, **semi-structured** và **unstructured data**.
* Khác biệt giữa ba loại dữ liệu.
* Ví dụ minh họa cụ thể cho mỗi loại.

### 11. Thực hành chương 2

Hãy làm vài bài tập để củng cố kiến thức này trước khi tiếp tục chương tiếp theo!

---


## **Bài giảng: Chương 3 – Cơ sở dữ liệu SQL và mô hình quan hệ**

### 1. Giới thiệu

Chúc mừng bạn đã hoàn thành các bài tập trước! Trong chương này, chúng ta sẽ tìm hiểu về **SQL** – ngôn ngữ quan trọng bậc nhất trong lĩnh vực kỹ thuật dữ liệu.

### 2. SQL là gì?

* **SQL** viết tắt của **Structured Query Language** – ngôn ngữ truy vấn dữ liệu có cấu trúc.
* SQL đối với cơ sở dữ liệu giống như tiếng Anh đối với nhạc pop: **rất phổ biến và ảnh hưởng sâu rộng**.
* SQL được dùng để truy vấn **RDBMS** – hệ quản trị cơ sở dữ liệu quan hệ.
* SQL cho phép:

  * Truy vấn nhiều bản ghi cùng lúc
  * Nhóm, lọc, tổng hợp dữ liệu dễ dàng
* Dễ học vì **cú pháp gần với tiếng Anh tự nhiên**.
* **Kỹ sư dữ liệu** dùng SQL để **tạo và duy trì cơ sở dữ liệu**.
* **Nhà khoa học dữ liệu** dùng SQL để **truy vấn dữ liệu phục vụ phân tích**.

### 3. Nhớ lại bảng nhân viên

* Ta sẽ không học sâu SQL trong khóa này, nhưng sẽ xem một số ví dụ để hiểu rõ hơn.
* Nhớ lại bảng "employees" của Spotflix:

  * Cột đầu là số nguyên (ID)
  * Cột gần cuối là giá trị logic (true/false)
  * Các cột còn lại là văn bản

### 4. SQL cho kỹ sư dữ liệu – Tạo bảng

* Ví dụ lệnh tạo bảng bằng SQL:

```sql
CREATE TABLE employees (
  employee_id INTEGER,
  first_name VARCHAR(255),
  last_name VARCHAR(255),
  role VARCHAR(255),
  team VARCHAR(255),
  full_time BOOLEAN,
  office VARCHAR(255)
);
```

* `VARCHAR(255)` nghĩa là chuỗi văn bản tối đa 255 ký tự.
* `BOOLEAN` chỉ nhận giá trị 0 (false) hoặc 1 (true).

### 5. SQL cho nhà khoa học dữ liệu – Truy vấn bảng

* Ví dụ Julian muốn tìm tên nhân viên có chức vụ chứa từ "data":

```sql
SELECT first_name, last_name
FROM employees
WHERE role LIKE '%data%';
```

* `%data%` nghĩa là "data" có thể nằm ở bất kỳ vị trí nào trong vai trò.

### 6. Mô hình cơ sở dữ liệu – Schema

* Cơ sở dữ liệu gồm nhiều bảng được **liên kết với nhau**.
* Cách các bảng kết nối gọi là **database schema**.

### 7. Ví dụ cơ sở dữ liệu Spotflix

* Bảng **albums**: album\_id, artist\_id, tiêu đề...
* Bảng **artists**: artist\_id, tên, tiểu sử...
* **albums** và **artists** liên kết qua **artist\_id**.
* Bảng **songs**: song\_id, album\_id, tiêu đề...
* **songs** liên kết với **albums** qua **album\_id**.
* Bảng **playlists**: playlist\_id, user\_id, song\_id...
* **playlists** liên kết với **songs** qua **song\_id**.

Các bảng khác có thể bao gồm: hãng đĩa, thể loại, người dùng, v.v.

Đây là lý do vì sao gọi đây là **cơ sở dữ liệu quan hệ** – vì mọi bảng đều có **mối liên hệ rõ ràng**.

### 8. Các phiên bản SQL khác nhau

* Có nhiều phiên bản (implementation) của SQL:

  * MySQL, PostgreSQL, SQLite, Microsoft SQL Server, Oracle SQL...
* Khác nhau như **bàn phím QWERTY và AZERTY**, hoặc **tiếng Anh – Anh và Anh – Mỹ**.
* Về cơ bản, phần lớn cú pháp vẫn giống nhau.

### 9. Tổng kết chương 3

Bạn đã biết:

* SQL là ngôn ngữ chuẩn cho hệ quản trị cơ sở dữ liệu quan hệ (RDBMS)
* Kỹ sư dữ liệu và nhà khoa học dữ liệu dùng SQL khác nhau
* Ví dụ cách tạo bảng và truy vấn bằng SQL
* Cách các bảng liên kết trong một **database schema**
* Có nhiều phiên bản SQL, phần lớn khá giống nhau

### 10. Thực hành chương 3

Giờ hãy làm một số bài tập để áp dụng kiến thức về SQL!


---

## **Bài giảng: Chương 4 – Data Lakes, Data Warehouses và Databases**

### 1. Giới thiệu

Chúc mừng bạn đã hoàn thành các bài tập trước! Bây giờ là lúc làm rõ một số khái niệm thường bị nhầm lẫn: **data lake**, **data warehouse**, và **database**.

### 2. Nhớ lại bài học về Pipeline

Ở cuối Chương 1, chúng ta đã nhắc đến **data lake** trong hệ thống pipeline. Trong suốt khóa học, ta cũng nói nhiều về **database** và ngay từ đầu đã đề cập đến **data warehouse**.

### 3. Phân biệt: Data Lake vs Data Warehouse

* **Data Lake**:

  * Nơi chứa **toàn bộ dữ liệu thô**, chưa xử lý, được tải lên từ các nguồn khác nhau.
  * Có thể lưu trữ **mọi loại dữ liệu**: structured, semi-structured, unstructured.
  * **Không áp đặt mô hình** lưu trữ → tiết kiệm chi phí.
  * Rất lớn, có thể lên đến **petabyte**.
  * **Khó phân tích** nếu không có công cụ học máy/phân tích lớn.
  * Dùng bởi **data scientists** cho phân tích thời gian thực.

* **Data Warehouse**:

  * Lưu trữ **dữ liệu đã chọn lọc** cho mục đích phân tích cụ thể (ví dụ: dữ liệu người dùng và phiên nghe nhạc).
  * Áp dụng **cấu trúc rõ ràng** → tốn kém hơn nhưng **dễ phân tích hơn**.
  * Tối ưu cho phân tích **tổng hợp, thống kê** → hỗ trợ ra quyết định kinh doanh.
  * Dùng bởi **data analysts** với các truy vấn đọc-only.

### 4. Vai trò của Data Catalog

* Do data lake quá linh hoạt nên cần có **data catalog** để:

  * Theo dõi nguồn gốc dữ liệu, người phụ trách, tần suất cập nhật.
  * Đảm bảo quản trị dữ liệu (data governance): sẵn sàng, chính xác, an toàn.
  * Tránh biến data lake thành **data swamp** (ao dữ liệu hỗn độn).
  * Tăng tính **tái sử dụng và minh bạch**.
  * Giúp quá trình tìm, xử lý, phân tích dữ liệu không phụ thuộc vào "truyền miệng" hay nhân sự.

### 5. Vậy database là gì?

* **Database** là một khái niệm chung, chỉ nơi **lưu trữ và truy cập dữ liệu có tổ chức** trên máy tính.
* **Data warehouse** chính là một **loại cụ thể** của database.
* Có thể hiểu:

  * Database: khái niệm tổng quát
  * Data warehouse: chuyên dùng để phân tích, với dữ liệu đã được xử lý và cấu trúc rõ ràng

### 6. Tổng kết chương 4

Giờ bạn đã nắm được:

* Đặc điểm của **data lake**, **data warehouse** và **database**
* Sự khác nhau giữa chúng
* Vai trò thiết yếu của **data catalog** trong việc tổ chức dữ liệu lớn

### 7. Thực hành chương 4

Hãy củng cố kiến thức vừa học bằng một vài bài tập, rồi chúng ta sẽ bước sang **Chương 5**: Dịch chuyển và xử lý dữ liệu (Data Movement & Processing).

---

## **Bài giảng: Chương 5 – Xử lý và Di chuyển Dữ liệu (Data Processing)**

### 1. Giới thiệu

Chào mừng bạn đến với **chương cuối cùng** của khóa học! Giờ ta đã hiểu rõ về data engineering và cách lưu trữ dữ liệu. Chương này sẽ tập trung vào **bước cuối cùng trong chu trình dữ liệu**: **di chuyển và xử lý dữ liệu**.

### 2. Nhìn lại hệ thống pipeline

* Khi ta:

  * Di chuyển dữ liệu vào **data lake**
  * Phân tách dữ liệu thành **nhiều bảng**
  * Xoá bỏ các bản ghi hỏng
  \=> Đó đều là **các hành động xử lý dữ liệu**.

### 3. Định nghĩa xử lý dữ liệu

* **Xử lý dữ liệu** là quá trình **chuyển đổi dữ liệu thô thành thông tin có ý nghĩa**.

### 4. Tại sao cần xử lý dữ liệu?

* Có nhiều dữ liệu **không còn cần thiết** sau khi thử nghiệm hoặc đã ổn định.
* **Tiết kiệm chi phí** lưu trữ, xử lý và truyền tải dữ liệu.
* Dữ liệu nén có thể nhỏ hơn dữ liệu chưa nén **gấp 10 lần**.
* Một số dữ liệu nên được **chuyển sang định dạng dễ sử dụng hơn** (ví dụ: nhạc chất lượng cao → nhạc stream).

### 5. Tại Spotflix

* Nghệ sĩ **tải lên file nhạc chất lượng cao** (wav, flac).
* Spotflix **xử lý và chuyển đổi** sang định dạng nhẹ hơn (.ogg) để stream.
* Đồng thời, Spotflix **trích xuất metadata** từ file nhạc (tên nghệ sĩ, thể loại, v.v.) và lưu trữ riêng.
* Dữ liệu như bảng nhân viên cũng được xử lý để phù hợp với **schema** chuẩn: phân tách tên – họ, dùng giá trị logic thay cho văn bản...
* **Tự động hóa** bước chuẩn bị giúp **data scientists** có thể phân tích ngay khi nhận dữ liệu.

### 6. Vai trò của kỹ sư dữ liệu trong xử lý

* Thực hiện các tác vụ như:

  * Làm sạch, sắp xếp, loại bỏ file hỏng
  * Xử lý giá trị thiếu (ví dụ: thiếu thể loại → để trống, điền mặc định, hay loại bỏ?)
  * Đảm bảo dữ liệu được lưu trữ theo **cấu trúc hợp lý**
  * Tạo **views** (kết quả từ các truy vấn lưu sẵn) để truy cập nhanh

  * Ví dụ: tạo view kết hợp bảng "nghệ sĩ" và "album"
  * **Tối ưu hiệu năng** bằng cách tạo **chỉ mục (index)** để truy xuất nhanh hơn

### 7. Công cụ xử lý dữ liệu

* Có vô số công cụ xử lý dữ liệu (ngoài phạm vi khóa học)
* Một ví dụ tiêu biểu là **Apache Spark** – có thể học riêng trên các khóa chuyên sâu

### 8. Tổng kết chương 5

Bạn đã hiểu:

* **Xử lý dữ liệu là gì**, tại sao cần thiết
* **Cách xử lý tại Spotflix**
* **Vai trò của kỹ sư dữ liệu** trong quá trình xử lý
* Một số **công cụ** phổ biến để xử lý dữ liệu

### 9. Thực hành chương 5

Hãy luyện tập để củng cố kiến thức, và như vậy bạn đã hoàn thành toàn bộ khóa học!

---

## **Bài giảng: Chương 6 – Lập lịch và Phân phối Dữ liệu (Scheduling & Delivery)**

### 1. Giới thiệu

Chúc mừng bạn đã hoàn thành các bài tập trước! Giờ chúng ta sẽ nói về một phần không thể thiếu của hệ thống kỹ thuật dữ liệu: **lập lịch (scheduling)**.

### 2. Lập lịch là gì?

* Lập lịch có thể áp dụng cho **mọi tác vụ xử lý dữ liệu**, ví dụ: cập nhật bảng, dọn sạch dữ liệu, tính toán tổng hợp...
* Nó giống như **keo dán** trong hệ thống kỹ thuật dữ liệu: giúp các thành phần chạy đúng thứ tự, đúng thời điểm, xử lý phụ thuộc giữa các tác vụ.

### 3. Các kiểu lập lịch phổ biến

* **Thủ công**: ví dụ khi nhân viên chuyển văn phòng, có thể cập nhật bảng ngay lập tức.

  * Phụ thuộc vào con người → không tối ưu.
* **Theo thời gian (time scheduling)**:

  * Ví dụ: mỗi sáng 6 giờ cập nhật bảng nhân viên.
* **Theo điều kiện (sensor scheduling)**:

  * Ví dụ: chỉ cập nhật bảng phòng ban nếu có nhân viên mới được thêm vào.
  * Tuy tối ưu nhưng cần hệ thống luôn "lắng nghe" thay đổi → tốn tài nguyên.
* **Kết hợp**:

  * Người dùng tự nâng cấp gói → hệ thống tự động cập nhật billing, unlock tính năng mới...

### 4. Batch vs Stream

* **Batch processing** (xử lý theo lô):

  * Dữ liệu được gửi theo cụm tại các khoảng thời gian nhất định.
  * Thường **rẻ hơn**, chạy vào lúc hệ thống rảnh (ví dụ ban đêm).
  * Ví dụ:

  * Bài hát tải lên được batch mỗi 10 phút.
  * Bảng nhân viên cập nhật mỗi sáng.
  * Bảng doanh thu cập nhật vào ban đêm.

* **Stream processing** (xử lý dòng):

  * Dữ liệu được xử lý **ngay khi có thay đổi**.
  * Ví dụ:

  * Người dùng mới đăng ký → cần được kích hoạt ngay.
  * Nghe nhạc online → stream từng phần.
  * Nghe offline → tải toàn bộ bài hát (batch).

* **Real-time**:

  * Một dạng đặc biệt (ví dụ: phát hiện gian lận).
  * Trong khóa học này, ta coi **real-time ≈ streaming**.

### 5. Công cụ lập lịch

Một số công cụ phổ biến:

* **Apache Airflow**
* **Luigi**

### 6. Tổng kết chương 6

Giờ bạn đã biết:

* Lập lịch là gì và tại sao quan trọng
* Các phương thức lập lịch (thủ công, theo thời gian, theo cảm biến)
* Sự khác biệt giữa **batch** và **stream**
* Cách Spotflix áp dụng lập lịch vào hệ thống
* Các công cụ lập lịch phổ biến

### 7. Thực hành chương 6

Hãy luyện tập để củng cố kiến thức trước khi tổng kết toàn khóa học!

---

## **Bài giảng: Chương 7 – Xử lý Song song (Parallel Computing)**

### 1. Giới thiệu

Chúc mừng bạn tiếp tục đến phần nâng cao! Một khái niệm rất quan trọng trong kỹ thuật dữ liệu hiện đại là **xử lý song song (parallel computing)** – còn gọi là xử lý đồng thời.

### 2. Xử lý song song là gì?

* Là nền tảng của hầu hết các công cụ xử lý dữ liệu hiện nay.
* Mục tiêu chính:

  * **Giảm tải bộ nhớ cho mỗi máy tính**
  * **Tăng tốc độ xử lý nhờ phân phối công việc**
* Hệ thống sẽ chia tác vụ lớn thành nhiều **tác vụ nhỏ**, phân phối cho nhiều máy tính xử lý cùng lúc.

### 3. Ví dụ: Gấp áo thun

* Bạn có một cửa hàng bán đồ nhạc cần gấp **1000 áo thun**.
* Nhân viên chính gấp 100 áo trong 15 phút.
* Nhân viên mới mất 30 phút cho 100 áo.
* Nếu chỉ 1 người làm: chọn người nhanh nhất.
* Nhưng nếu chia đều cho **4 nhân viên mới**, mỗi người gấp 250 áo, thì hoàn thành trong **1h15 phút**, nhanh hơn **1 người chính làm 2h30 phút**.

### 4. Lợi ích và rủi ro của xử lý song song

* **Lợi ích**:

  * Tăng sức mạnh xử lý nhờ nhiều đơn vị tính toán
  * Giảm áp lực bộ nhớ: mỗi máy chỉ cần nạp **phần nhỏ dữ liệu**

* **Rủi ro**:

  * Chia nhỏ và ghép kết quả **tốn thời gian** và tài nguyên
  * Truyền dữ liệu giữa các máy **có chi phí**
  * Nếu tác vụ nhỏ không đáng kể, **việc chia nhỏ có thể gây lãng phí**

### 5. Trở lại ví dụ gấp áo

* Chia áo thành 4 đống mất 10 phút
* Gom lại áo sau khi gấp mất thêm 5 phút
* Tổng thời gian = **1h30 phút** → nhiều hơn dự kiến 1h15 phút

### 6. Ứng dụng tại Spotflix

* Spotflix dùng xử lý song song để:

  * **Chuyển đổi file nhạc từ định dạng lossless sang .ogg**
  * Tránh phải tải tất cả nhạc vào 1 máy tính
  * Tăng tốc độ xử lý nhờ chạy script chuyển đổi trên nhiều máy

### 7. Tổng kết chương 7

Bạn đã hiểu:

* **Khái niệm xử lý song song** là gì
* **Lợi ích & rủi ro** của nó trong thực tế
* **Ví dụ minh họa** dễ hiểu (gấp áo)
* **Cách Spotflix triển khai xử lý song song** cho chuyển đổi file nhạc

### 8. Thực hành chương 7

Hãy luyện tập thêm để hiểu sâu hơn về xử lý song song nhé!

---

## **Bài giảng: Chương 8 – Điện toán đám mây (Cloud Computing)**

### 1. Giới thiệu

Đây là chặng cuối cùng của khóa học! Chúng ta sẽ tìm hiểu về **cloud computing – điện toán đám mây**, một xu hướng không thể thiếu trong ngành dữ liệu.

### 2. Điện toán đám mây cho xử lý dữ liệu

* Trước đây, công ty phải **mua máy chủ, lưu trữ tại văn phòng**, chịu mọi chi phí bảo trì, điện, vận chuyển...
* Nếu hệ thống cần **tải cao tại một số thời điểm**, thì phần lớn thời gian còn lại sẽ bị lãng phí tài nguyên.
* Với **cloud**, ta thuê máy chủ:

  * Không cần mua phần cứng
  * **Chỉ dùng khi cần**, tiết kiệm chi phí
  * Không cần phòng máy
* Để phục vụ người dùng toàn cầu, ta cần **máy chủ đặt ở nhiều vị trí địa lý** để giảm độ trễ.

### 3. Điện toán đám mây cho lưu trữ dữ liệu

* Cloud đảm bảo **độ tin cậy**:

  * Dữ liệu được **sao lưu tại nhiều nơi**, đề phòng thiên tai như cháy nổ.
* Tuy nhiên, khi dữ liệu nhạy cảm được lưu bởi bên thứ ba, có thể phát sinh:

  * Rủi ro an ninh
  * Lo ngại về **giám sát chính phủ**

### 4. Các nhà cung cấp Cloud lớn

3 ông lớn theo thị phần:

1. **Amazon Web Services (AWS)**
2. **Microsoft Azure**
3. **Google Cloud Platform (GCP)**

Dịch vụ tương ứng:

* **Lưu trữ file**:

  * AWS S3
  * Azure Blob Storage
  * Google Cloud Storage
* **Xử lý tính toán**:

  * AWS EC2
  * Azure Virtual Machines
  * Google Compute Engine
* **Cơ sở dữ liệu**:

  * AWS RDS
  * Azure SQL Database
  * Google Cloud SQL

### 5. Ứng dụng Cloud tại Spotflix

* Spotflix chọn AWS:

  * Dùng **S3** để lưu ảnh bìa album
  * Dùng **EC2** để xử lý nhạc
  * Dùng **RDS** để lưu thông tin nhân viên

### 6. Mô hình đa đám mây (Multicloud)

* Không bắt buộc phải dùng 1 nhà cung cấp.
* Có thể dùng nhiều nhà cung cấp → gọi là **multicloud**.
* Lợi ích:

  * Tránh phụ thuộc vào 1 vendor
  * Tối ưu chi phí
  * Tuân thủ luật pháp địa phương
  * Chống thảm hoạ (ví dụ: AWS từng bị sự cố năm 2017 khiến nửa internet ngừng hoạt động)
* **Nhược điểm**:

  * Các dịch vụ giữa các bên **có thể không tương thích**
  * Quản lý bảo mật và quyền truy cập **phức tạp hơn**
  * Cloud vendors thường **muốn khóa người dùng** bằng hệ sinh thái riêng

### 7. Tổng kết chương 8

Bạn đã hiểu:

* **Lợi ích & rủi ro** của điện toán đám mây
* Tại sao cloud giúp tối ưu chi phí và mở rộng dễ dàng
* Các nhà cung cấp lớn và dịch vụ đi kèm
* Ứng dụng cloud tại Spotflix
* Ưu nhược điểm của **mô hình đa đám mây (multicloud)**

### 8. Thực hành chương 8

Cùng luyện tập thêm, và như đã hứa từ Chương 1 – playlist học tập đang chờ bạn khám phá!

---

## **Tổng kết khóa học: Data Engineering for Everyone**

### 1. Xin chúc mừng!

🎉 Alright alright alright! Bạn đã hoàn thành toàn bộ khóa học! 👏

### 2. Bạn là nhà vô địch!

* Bạn đã trải qua hành trình dài, học hỏi từ đầu đến cuối.
* Có thể bạn mắc sai lầm, nhưng bạn đã vượt qua và **về đích một cách xuất sắc**.

### 3. Những gì bạn đã học – Chương 1

* Định nghĩa được **Data Engineering** là gì
* Phân biệt **kỹ sư dữ liệu** và **nhà khoa học dữ liệu**
* Hiểu được tầm quan trọng của **data pipeline** và cách dữ liệu luân chuyển trong tổ chức

### 4. Những gì bạn đã học – Chương 2

* Phân loại được **dữ liệu có cấu trúc**, **bán cấu trúc**, **phi cấu trúc**
* Hiểu vai trò của **SQL** trong kỹ thuật dữ liệu
* So sánh **data lake**, **data warehouse**, **database**

### 5. Những gì bạn đã học – Chương 3 trở đi

* Giải thích được **data processing** là gì
* Hiểu **lập lịch (scheduling)** hoạt động như thế nào
* Nắm được khái niệm **xử lý song song (parallel computing)**
* Hiểu và ứng dụng **điện toán đám mây (cloud computing)**

### 6. Và nhiều hơn nữa!

* Bạn đã nhìn thấy **SQL code mẫu**
* Làm quen với các **công cụ phổ biến** như Apache Airflow, Spark…
* Tự tay "xây dựng" nên một **data pipeline mẫu**

### 7. Tài liệu bổ sung

* Trên trang khóa học (bên phải, cuối trang), bạn sẽ tìm thấy mục **datasets** → tại đó chứa **lexicon (từ vựng kỹ thuật)** của khóa học mà bạn có thể tải xuống.

### 8. Playlist – Lời hứa đã giữ!

* Như đã hứa từ Chương 1: tất cả tên bài tập trong khóa học đều là **tên bài hát**.
* Bạn có thể tìm playlist trên **Spotify** bằng cách gõ "**datachamp**".

### 9. Chúc mừng một lần nữa!

🎓 Bạn giờ đây đã có nền tảng vững chắc về **Data Engineering**.
💡 Hy vọng bạn đã có khoảng thời gian học vui vẻ như chúng tôi khi tạo nên khóa học này.

**Cảm ơn bạn đã tham gia khóa học "Data Engineering for Everyone" – chúc bạn thành công trên chặng đường phía trước!** 🚀
