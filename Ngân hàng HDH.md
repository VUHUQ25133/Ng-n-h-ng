# Chương 1
## Loại 1 điểm
### 1.1. Trình bày về giao diện lập trình của HĐH.
- Để các chương trình có thể sử dụng được dịch vụ, HĐH Cung cấp giao diện lập trình bao gồm các lời gọi hệ thống *(System Call)*
- Lời gọi hệ thống: Các lệnh đặc biệt mà CTƯD gọi khi cần yêu cầu HĐH thực hiện một việc gì đó.
- Lời gọi hệ thống được thực hiện qua các thư viện hàm gọi là thư viện hệ thống.

### 1.2. Trình bày kỹ thuật xử lý theo mẻ (lô) và ưu điểm của kỹ thuật này.Hệ thống xử lý theo mẻ có cần HĐH không?
**Xử lí theo mẻ**:
- Chương trình được phân thành các mẻ gồm những chương trình có yêu cầu giống nhau.
- Toàn bộ mẻ được nạp vào băng từ và được tải vào máy để thực hiện lần lượt.
    + Chương trình giám sát *(monitor)*: Tự động nạp chương trình tiếp theo vào máy và cho phép nó chạy.
    => Giảm đáng kể thời gian chuyển đổi giữa 2 chương trình trong cùng một mẻ. Trình giám sát là dạng đơn giản nhất của HĐH.
- Hệ thống xử lý theo mẻ ***có cần*** HĐH.

### 1.3. Đa chương trình là gì? Lý do sử dụng đa chương trình trong máy tính? Yêu cầu đối với phần cứng khi sử dụng đa chương trình.
- Đa chương trình là hệ thống chứa đồng thời nhiều chương trình trong bộ nhớ.
- Lý do sử dụng: 
  - Mặc dù việc xử lý theo mẻ giảm thời gian chuyển đổi giữa các chương trình trong ứng dụng, song Hiệu suất của CPU Tương đối thấp do CPU phải dừng việc xử lý dữ liệu khi có yêu cầu vào ra *(tốc độ vào ra thấp hơn tốc độ CPU rất nhiều)*
  - Đa chương trình sẽ giúp khắc phục điều đó, bằng cách khi CPU đang phải dừng để thực hiện quá trình vào ra, HĐH sẽ chuyển CPU sang thực hiện một chương trình khác.Nếu chương trình nằm trong bộ nhớ đủ nhiều thì hầu như lúc nào CPU Cũng có việc để thực hiện.
  **=> Giảm thời gian chạy không tải của CPU.** 
- Yêu cầu đối với phần cứng: Khả năng vào/ra bằng ngắt và DMA

### 1.4. Trình bày về các thành phần của hệ thống máy tính và vai trò của HĐH trong đó.
- **Phần cứng**: Cung cấp tài nguyên cần thiết.
- **Phần mềm**: Các chương trình cụ thể.
- HĐH: Phần mềm đóng vai trò trung gian làm cho việc sử dụng hệ thống máy tính được tiện lợi và hiệu quả. *(Quản lý tài nguyên và quản lý việc thực hiện các chương trình)*

### 1.5. Trình bày về HĐH, chia sẻ thời gian.
- Chia sẻ thời gian có thể coi như đa chương trình cải tiến giao diện với người dùng.
- CPU lần lượt thực hiện các công việc khác nhau trong những khoảng thời gian ngắn gọi là lượng tử thời gian.
- Chuyển đổi giữa các công việc diễn ra với tần số cao và tốc độ CPU lớn.

**=> Tất cả người dùng đều có cảm giác máy tính chỉ thực hiện chương trình của mình.**
**=> CPU được chia sẻ giữa những người dùng khác nhau, tương tác trực tiếp với hệ thống.**

## Loại 2 điểm
### 2.1*. Trình bày ngắn gọn ***(3đ chi tiết)*** về các thành phần cơ bản của HĐH.
- **Quản lý tiến trình:**
  - Tạo và xóa tiến trình
  - Tạm treo và khôi phục các tiến trình bị treo
  - Đồng bộ hóa các tiến trình *(Lập lịch cho các tiến trình, v.v...)*
  - Giải quyết các bế tắc, ví dụ như khi có xung đột về tài nguyên.
  - Tạo cơ chế liên lạc giữa các tiến trình.
- **Quản lý bộ nhớ:**
  - Quản lý việc phân phối bộ nhớ giữa các tiến trình.
  - Tạo ra bộ nhớ ảo và ánh xạ địa chỉ bộ nhớ ảo và bộ nhớ thực.
  - Cung cấp và giải phóng bộ nhớ theo yêu cầu của tiến trình.
  - Quản lý không gian nhớ đã được cấp và không gian còn trống.
- **Quản lý vào ra:** Đơn giản hóa và tăng hiệu quả quá trình trao đổi thông tin giữa các tiến trình với thiết bị vào ra.
- **Quản lý tệp và thư mục**:
  - Tạo, xóa tệp và thư mục.
  - Đọc ghi tệp.
  - Ánh xạ tệp và thư mục sang bộ nhớ ngoài.
- **Hỗ trợ mạng và xử lý phân tán:** Quản lý thiết bị mạng, hỗ trợ các giao thức truyền thông, quản lý truyền thông, cân bằng tải.
- **Giao diện với người dùng:** Nhận lệnh từ người dùng và thực hiện các lệnh này.Có thể bằng cách sử dụng dịch vụ do các phần khác của HĐH cung cấp.
- **Các chương trình tiện ích và ứng dụng:** HĐH thường chứa sẳn một số các chương trình tiện ích và CTƯD.Đây là thành phần không bắt buộc của HĐH.

### 2.2. Trình bày về nhân của HĐH? Thế nào là chế độ nhân và chế độ người dùng?
- **Nhân của HĐH:**
  - Nhân (kernel) Là phần cốt lõi thực hiện các chức năng cơ bản nhất, quan trọng nhất của HĐH và thường xuyên được giữ trong bộ nhớ.
  - HĐH gồm nhiều thành phần chỉ tải những thành phần quan trọng không thể thiếu được vào bộ nhớ gọi là nhân.
  - Nhân chạy trong chế độ đặc quyền - **Chế độ nhân**
  - Các chương trình bình thường chạy trong **Chế độ người dùng**
- **Chế độ nhân và chế độ người dùng:**
  - Máy tính hiện đại thường được thiết kế với 2 chế độ thực hiện chương trình: Chế độ nhân và chế độ người dùng.
  - **Chế độ nhân** là chế độ mà chương trình thực hiện trong đó đầy đủ quyền truy cập và điều khiển phần cứng máy tính. Ví dụ có thể thay đổi nội dung tất cả các thanh ghi của CPU, hay có thể ghi vào bộ nhớ vật lý.
  - Ngược lại, chương trình thực hiện trong **chế độ người dùng** bị hạn chế rất nhiều quyền truy cập và điều khiển phần cứng. Việc quy định chế độ cụ thể phụ thuộc vào một bit, đặc biệt trong một thanh ghi của CPU.Nếu bít này có giá trị = 0 thì là chế độ nhân, = 1 tương ứng với chế độ bình thường.

### 2.3*. Trình bày cấu trúc nguyên khối và cấu trúc phân lớp của HĐH. Phân tích so sánh ưu nhược điểm của 2 kiểu cấu trúc này.
- **Cấu trúc nguyên khối:**
  - Toàn bộ chương trình và dữ liệu của HĐH có chung một không gian nhớ.
  - HĐH trở thành một tập hợp các thủ tục hay các chương trình con.
  - ***Ưu điểm:*** nhanh.
  - ***Nhược điểm:*** không an toàn, không mềm dẻo.
- **Cấu trúc phân lớp:**
  - Các thành phần được phân chia thành các lớp nằm chồng lên nhau.
  - Mỗi lớp chỉ có thể liên lạc với lớp nằm kề bên trên và kề bên dưới, Và chỉ có thể sử dụng dịch vụ do nước nằm ngay bên dưới cung cấp.
  - ***Ưu điểm:*** dễ sửa đổi.
  - ***Nhược điểm:*** tốc độ chậm hơn cấu trúc nguyên khối.

### 2.4*. Trình bày cấu trúc vi nhân của HĐH. So sánh ưu nhược điểm của cấu trúc này với cấu trúc nguyên khối và phân lớp.
- **Cấu trúc vi nhân:**
  - Nhân chỉ chứa các chức năng quan trọng nhất.
  - Các chức năng còn lại được đặt vào các modul riêng: Chạy trong chế độ đặc quyền hoặc người dùng.
  - ***Ưu điểm:*** mềm dẻo, an toàn
  - ***Nhược điểm:*** Tốc độ chậm hơn so với cấu trúc nguyên khối.
- **So sánh:**

| Cấu trúc   | Vi nhân          | Nguyên khối     | Phân lớp         |
|------------|------------------|-----------------|------------------|
| Ưu điểm    | Mềm dẻo, an toàn | Nhanh           | Dễ sửa lỗi       |
| Nhược điểm | Tốc độ chậm hơn  | Không an toàn,  | Tốc độ chậm hơn  |
|            | CT nguyên khối   | không mềm dẻo   | CT nguyên khối   |

### 2.5.Trình bày về HĐH đa chương trình. Lấy ví dụ minh họa để phân tích hiệu suất sử dụng CPU của HĐH đa chương trình cao hơn so với HĐH đơn chương trình.
- ***Đa chương trình:***
  - Hệ thống chứa, đồng thời nhiều chương trình trong bộ nhớ.
  - Khi một chương trình phải dừng lại để thực hiện vào da, HĐH sẽ chuyển CPU sang thực hiện một chương trình khác.
  **=> Giảm thời gian chạy không tải của CPU.**

![2 5](https://github.com/user-attachments/assets/1368a3dc-db09-41e3-bc2a-2a842fef3d47)


  - Theo gian chờ đợi của CPU trong chế độ đa chương giảm đáng kể so với trong trường hợp đơn chương.
  - HĐH phức tạp hơn rất nhiều so với HĐH đơn chương trình.
  - Đòi hỏi hỗ trợ từ phần cứng, đặc biệt khả năng vào/ra bằng ngắt và DMA.

## Loại 3 điểm
### 3.1. Trình bày khái niệm HĐH. Phân tích rõ 2 chức năng cơ bản của HĐH.
  - **Khái niệm HĐH:**
    - HĐH là hệ thống phần mềm đóng vai trò trung gian giữa người sử dụng và phần cứng của máy tính nhằm tạo ra môi trường giúp thực hiện các chương trình một cách thuận tiện.
    - Ngoài ra, HĐH còn quản lý và đảm bảo cho việc sử dụng phần cứng của máy tính được hiệu quả.
  - **2 chức năng cơ bản của HĐH:**
    - ***Quản lý tài nguyên***
      - Đảm bảo tài nguyên hệ thống được sử dụng một cách có ích và hiệu quả.
      - Các tài nguyên: bộ xử lý (CPU), bộ nhớ chính, bộ nhớ ngoài (cá đĩa), các thiết bị vào ra.
      - Phân phối tài nguyên cho các ứng dụng hiệu quả.
      - Yêu cầu tài nguyên được HĐH thu nhận và đáp ứng bằng cách cấp cho chương trình các tài nguyên tương ứng.
      - HĐH cần lưu trữ tình trạng tài nguyên.
      - Đảm bảo không xâm phạm tài nguyên cấp cho chương trình khác.
    - ***Quản lý việc thực hiện các chương trình***
      - Một chương trình đang trong quá trình chạy gọi là tiến trình (process).
      - HĐH giúp việc chạy chương trình dễ dàng hơn.
      - Tạo ra các máy ảo là máy logic với các tài nguyên ảo.
      - Tài nguyên ảo mô phỏng tài nguyên thực được thực hiện bằng phần mềm.
      - Cung cấp các dịch vụ cơ bản như tài nguyên thực.
      - Dễ sử dụng hơn.
      - Số lượng tài nguyên ảo có thể lớn hơn tài nguyên thực.

### 3.2. Dịch vụ của HĐH là gì? Trình bày những dịch vụ điển hình mà HĐH cung cấp. Làm rõ về quá trình tải và chạy HĐH khi mới khởi động.
- Dịch vụ của HĐH là những công việc mà HĐH thực hiện giúp người dùng hoặc chương trình ứng dụng.
- Những dịch vụ mà HĐH cung cấp:
  - **Tải và chạy chương trình**
    - Để thực hiện chương trình được tải từ đĩa và bộ nhớ, sau đó được trao quyền thực hiện các lệnh.
    - Khi thực hiện xong cần giải phóng bộ nhớ và các tài nguyên.
    ***=> HĐH sẽ thực hiện công việc này.***
    - HĐH tự tải mình vào bộ nhớ.
  - Giao diện với người dùng: Dưới dạng dòng lệnh hoặc giao diện đồ họa.
  - Thực hiện các thao tác vào ra dữ liệu.
  - Làm việc với hệ thống file.
  - Phát hiện và xử lý lỗi: Đảm bảo cho hệ thống hoạt động ổn định, an toàn.
  - Truyền thông: Cung cấp dịch vụ cho phép thiết lập liên lạc và truyền thông tin.
  - Cấp phát tài nguyên.
  - Dịch vụ an ninh và bảo mật.

# Chương 2.
## Loại 1 điểm
### 1.6. Trình bày khái niệm tiến trình và chỉ ra điểm khác nhau giữa tiến trình với chương trình. Nếu tên ít nhất 4 thao tác liên quan tới quản lý tiến trình.
- Tiến trình là một chương trình đang trong quá trình thực hiện.
  
| Chương trình                   | Tiến trình                                                      |
|--------------------------------|-----------------------------------------------------------------|
| Thực thể tĩnh                  | Thực thể động                                                   |
| Không sở hữu tài nguyên cụ thể | Được cấp một số tài nguyên để chứa tiến trình và thực hiện lệnh |

- Tiến trình được sinh ra khi chương trình được tải vào bộ nhớ để thực hiện:
  - Tiến trình người dùng
  - Tiến trình hệ thống
- Các thao tác liên quan tới quản lý tiến trình:
  - Tạo lập tiến trình
  - Tạm dừng tiến trình
  - Tái kích hoạt tiến trình
  - Chuyển đổi giữa các tiến trình
  - Kết thúc tiến trình

### 1.7. Trình bày về thao tác tạo mới tiến trình. Tiến trình có thể bị kết thúc trong những trường hợp nào?
- **Tạo mới tiến trình:**
  - Gán số định danh cho tiến trình được tạo mới và tạo một ô trong bản tiến trình.
  - Tạo không gian nhớ cho tiến trình và PCB.
  - Khởi tạo PCB.
  - Liên kết PCB của tiến trình vào các danh sách quản lý.
- **Tiến trình kết thúc** trong các trường hợp:
  - Bị tiến trình cha kết thúc.
  - Do các lỗi: Lỗi số học, lỗi truy cập, lỗi vào ra.
  - Yêu cầu nhiều bộ nhớ hơn số lượng hệ thống có thể cung cấp.
  - Thực hiện lâu hơn thời gian giới hạn.
  - Do quản trị hệ thống hoặc HĐH kết thúc.

### 1.8*. Trình bày về khái niệm dòng (thread) thực hiện. Thế nào là dòng mức người dùng và mức nhân?
- Mỗi đơn vị thực hiện lệnh của tiến trình, tức là một chuỗi lệnh được cấp phát CPU để thực hiện độc lập gọi là một luồng thực hiện.
  - Luồng mức người dùng: Được tạo ra và quản lý không có sự hỗ trợ của HĐH.
  - Luồng mức nhân: Được tạo ra và quản lý bởi HĐH.
### 1.9. Trình bày về điều độ quay vòng. Cho ví dụ minh họa về tính thời gian chờ đợi trung bình khi điều độ theo kiểu này.
- Hết lượng tử thời gian mà tiến trình chưa kết thúc.
  - Tiến trình đang thực hiện bị dừng lại.
  - Quyền điều khiển chuyển cho hàm xử lý ngắt của HĐH.
  - HĐH chuyển tiến trình về cuối hàng đợi lấy tiến trình ở đầu và tiếp tục.
- Cải thiện thời gian đáp ứng so với FCFS
- Thời gian chờ đợi trung bình vẫn dài.
- VD:

| Tiến trình | Độ dài chu kì CPU |
|------------|-------------------|
| P1         | 10                |
| P2         | 4                 |
| P3         | 2                 |

![1 9](https://github.com/user-attachments/assets/05d59a83-2001-4ea8-9043-d0b2186cb99b)


Thời gian chờ đợi của P1, P2, P3 lần lượt là 6, 6, và 4.
Thời gian chờ đợi trung bình = (6 + 6 + 4) / 3 = 5,33

### 1.10*. Các thông tin nào được lưu trữ trong khối quản lý tiến trình PCB?
- **Số định danh của tiến trình** (PID)
- **Trạng thái tiến trình**.
- **Nội dung một số thanh ghi CPU:**
  - Thanh ghi con trỏ lệnh: trỏ tới lệnh tiếp theo
  - Thanh ghi con trỏ ngăn xếp
  - Các thanh ghi điều kiện và trạng thái
  - Các thanh ghi đa năng.
- **Thông tin phục vụ điều độ tiến trình**: Mức độ ưu tiên của tiến trình, vị trí trong hàng đợi...
- **Thông tin về bộ nhớ của tiến trình**
- **Danh sách các tài nguyên khác:** Các file đang mở, thiết bị vào ra mà tiến trình sử dụng
- **Thông tin thống kê phục vụ quản lý:** Thời gian sử dụng CPU, giới hạn thời gian

### 1.11. Trình bày các tiêu chí đánh giá thuật toán điều độ tiến trình
**1. Lượng tiến trình được thực hiện xong:**   
  - Số lượng tiến trình thực hiện xong trongtrong một đơn vị thời gian
  - Đo tính hiệu quả của hệ thống

**2. Hiệu suất sử dụng CPU**
**3. Thời gian vòng đời trung bình của tiến trình**, Từ lúc có yêu cầu tạo tiến trình đến khi kết thúc.
**4. Thời gian chờ đợi:**
  - Tổng thời gian tiến trình nằm trong trạng thái sẳn sàng và chờ cấp CPU.
  - Ảnh hưởng trực tiếp của thuật toán điều độ tiến trình

**5. Thời gian đáp ứng**, từ lúc người dùng yêu cầu đến khi tiến trình có phản hồi.
**6. Tính dự đoán được**: Vòng đời, thời gian chờ đợi, thời gian đáp ứng phải ổn định, không phụ thuộc vào tải của hệ thống.
**7. Tính công bằng**: Các tiến trình cùng độ ưu tiên phải được đối xử như nhau.

### 1.12.Trình bày điều độ đến trước phục vụ trước FCFS. Cho ví dụ minh họa về tính thời gian chờ đợi trung bình khi điều độ kiểu này.
- Điều độ FCFS:
  - Tiến trình yêu cầu CPU trước sẽ được cấp trước.
  - HĐH xếp các tiến trình sẳn sàng vào hàng đợi FIFO.
  - Tiến trình mới được sắp xếp vào cuối hàng đợi.
  - Đơn giản, đảm bảo tính công bằng
  - Thời gian chờ đợi trung bình lớn
  **=> Ảnh hưởng lớn tới hiệu suất chung của hệ thống.**
  - Thường là thuật toán điều độ không phân phối lại.
VD:

| Tiến trình | Độ dài chu kì CPU |
|------------|-------------------|
| P1         | 10                |
| P2         | 4                 |
| P3         | 2                 |

![1 12](https://github.com/user-attachments/assets/2970fb58-66f9-472f-b782-429b965aeb35)


## Loại 2 điểm
### 2.7. Trình bày 5 trạng thái của tiến trình. Vẽ sơ đồ và giải thích về việc chuyển đổi giữa 5 trạng thái này.
**Mô hình 5 trạng thái:**
- ***Mới khởi tạo:*** Tiến trình đang được tạo ra.
- ***Sẳn sàng:*** Tiến trình chờ được cấp CPU để thực hiện lệnh của mình.
- ***Chạy:*** Lệnh của tiến trình được CPU thực hiện.
- ***Chờ đợi:*** Tiến trình chờ đợi một sự kiện gì đó xảy ra (blocked)
- ***Kết thúc:*** Tiến trình đã kết thúc việc thực hiện nhưng vẫn chưa bị xóa.


![2 7](https://github.com/user-attachments/assets/e5e6d4b3-0abf-4512-b07a-ba78a6ef92e9)


### 2.8. Điều độ tiến trình là gì? Điều độ dòng có khác điều độ tiến trình không? Trình bày về điều độ có phân phối lại và không phân phối lại.
- ***Điều độ*** (lập lịch) Là quyết định tiến trình nào được sử dụng tài nguyên phần cứng khi nào, trong thời gian bao lâu.
- Tập trung vào vấn đề điều độ đối với CPU *=> Quyết định thứ tự và thời gian sử dụng CPU.*
- **Điều độ tiến trình và điều độ dòng**:
  - Hệ thống trước kia: Tiến trình là đơn vị thực hiện chính 
  *=> Điều độ thực hiện với tiến trình.*
  - Hệ thống hỗ trợ dòng: dòng mức nhân là đơn vị HĐH cấp CPU.
=> Sử dụng thuật ngữ điều độ tiến trình rộng rãi <=> điều độ dòng

- Điều độ phân phối lại: HĐH có thể sử dụng cơ chế ngắt để thu hồi CPU của một tiến trình đang trong trạng thái chạy.
- Điều độ không phân phối lại: Tiến trình đang ở trạng thái chạy sẽ được sử dụng CPU Cho đến khi xảy ra một trong các tình huống:
  - Tiến trình kết thúc
  - Tiến trình phải chuyển sang trạng thái chờ đợi do thực hiện I/O.

### 2.9. Trình bày một giải pháp giúp không xảy ra bế tắc khi sử dụng cờ hiệu của bài toán **triết gia ăn cơm**.
- Đặt 2 thao tác lấy đũa của mỗi triết gia vào giai đoạn nguy hiểm để đảm bảo triết gia lấy được 2 đũa một lúc.
- Quy ước bất đối xứng về thứ tự lấy đũa, ví dụ người có số thứ tự chẵn lấy đũa trái trước đũa phải, người có số thứ tự lẻ lấy đũa phải trước đũa trái.
- Tại mỗi thời điểm chỉ cho tối đa 4 người ngồi vào bàn.

### 2.10. Trình bày thao tác và quá trình chuyển đổi giữa các tiến trình.
**Chuyển đổi giữa các tiến trình**:
- Thông tin về tiến trình hiện thời (chứa trong PCB) Được gọi là ngữ cảnh (context)
- Việc chuyển giữa các tiến trình còn được gọi là chuyển đổi ngữ cảnh.
- Xảy ra khi:
  - Có ngắt.
  -  Tiến trình gọi lời gọi hệ thống.
- Trước khi chuyển sang thực hiện tiến trình khác, ngữ cảnh được lưu vào PCB.
- Khi được cấp phát CPU thực hiện trở lại, ngữ cảnh được khôi phục từ PCB vào các thanh ghi và bảng tương ứng.
- Thông tin nào phải được cập nhật và lưu vào pc b khi chuyển tiến trình? => Tùy trường hợp
- Hệ thống chuyển sang thực hiện ngắt vào/ra rồi quay lại thực hiện tiếp tiến trình:
  - Ngữ cảnh gồm thông tin có thể bị hàm xử lý ngắt thay đổi
  => Nội dung thanh ghi, trạng thái CPU.

### 2.11. Trình bày dòng mức nhân và dòng mức người dùng. Phân tích ưu nhược điểm.
**Dòng mức nhân**
- HĐH cung cấp giao diện lập trình gồm các lời gọi hệ thống mà trình ứng dụng có thể yêu cầu tạo/xóa luồng.
- ***Ưu điểm:*** Đang tính đáp ứng và khả năng thực hiện đồng thời của các luồng trong cùng tiến trình.
- ***Nhược điểm:*** Tốc độ chậm

**Dòng mức người dùng:**
- Do trình ứng dụng tự tạo ra và quản lý.
- Sử dụng thư viện do ngôn ngữ lập trình cung cấp.
- HĐH vẫn coi tiến trình như một đơn vị duy nhất với một trạng thái duy nhất.
- Việc phân phối CPU được thực hiện cho cả tiến trình.
- ***Ưu điểm:***
  -  Việc chuyển đổi luồng không đòi hỏi chuyển sang chế độ nhân => Tiết kiệm thời gian.
  -  Trình ứng dụng có thể điều độ theo đặc điểm riêng của mình, không phụ thuộc vào cách điều độ của HĐH.
  -  Có thể sử dụng trên cả những HĐH không hỗ trợ đa luồng.
- ***Nhược điểm:***
  - Khi một luồng gọi lời gọi hệ thống và bị phong tỏa, Toàn bộ tiến trình bị phong tỏa.
  => Không cho phép tận dụng ưu điểm về tính đáp ứng của mô hình đa luồng.
  - Không cho phép tận dụng kiến trúc nhiều CPU.
  
### 2.12. Trình bày giải pháp sử dụng lệnh máy Test_and_Set Cho vấn đề loại trừ tương hỗ và đoạn nguy hiểm. Ưu nhược điểm của giải pháp này là gì?
Giải pháp sử dụng lệnh máy Test_and_Set:
- Phần cứng được thiết kế có một số lệnh máy đặc biệt.
- 2 thao tác kiểm tra và thay đổi giá trị cho một biến, hoặc thao tác so sánh và hoán đổi giá trị 2 biến được thực hiện trong cùng một loại máy.
  => Đảm bảo được thực hiện cùng nhau mà không bị xen vào giữa - thao tác nguyên tử (atomic)
```
bool Test_and_Set(bool & val) {
  bool temp = val;
  val = true;
  return temp;
}
```
- Ưu điểm:
  - Việc sử dụng tương đối đơn giản, trực quan
  - Có thể dùng đồng bộ nhiều tiến trình
  - Có thể sử dụng cho trường hợp đa xử lý với nhiều CPU nhưng có bộ nhớ chung
- Nhược điểm:
  - Chờ đợi tích cực.
  - Có thể gây đói.

## Loại 3 điểm
### 3.4. Trình bày khái niệm dòng và mô hình đa dòng. Vấn đề sở hữu tài nguyên của tiến trình và dòng. Phân tích ưu điểm của mô hình đa dòng.
**Khái niệm:**
  - Thread: Mỗi đơn vị thực hiện lệnh của tiến trình, Tức là một chuỗi lệnh được cấp phát CPU để thực hiện độc lập, được gọi là một luồng thực hiện.
  - Mô hình đa luồng:
    - Mỗi luồng cần có khả năng quản lý con trỏ lệnh, nội dung thanh ghi.
    - Luồng cũng có trạng thái riêng, Cũng cần có ngăn xếp riêng.
    - Tất cả các luật của một tiến trình chia sẻ không gian nhớ và tài nguyên.
    - Các luồng cũng có cùng không gian, địa chỉ và có thể truy cập tới dữ liệu của tiến trình.

**Vấn đề sở hữu tài nguyên của tiến trình và dòng:** Tất cả các luồng của một tiến trình chia sẻ không gian nhớ và tài nguyên.
**Ưu điểm của mô hình đa luồng:**
- Tăng hiệu năng và tiết kiệm thời gian
- Dễ dàng chia sẻ thông tin và tài nguyên.
- Tăng tính đáp ứng: Khi một luồng bị phong tỏa, các luồng khác vẫn có thể xử lý yêu cầu từ người dùng.
- Tận dụng kiến trúc, xử lý nhiều CPU. Mỗi luồng có thể được cấp một CPU riêng, nhờ vậy tăng tốc độ của tiến trình.
- Thuận lợi cho việc tổ chức chương trình: Có thể dưới dạng nhiều luồng thực hiện các công việc song song.

### **3.5**. Phân tích các vấn đề cần quan tâm trong sử dụng và quản lý tiến trình đồng thời đối với 3 dạng tiến trình: Tiến trình độc lập có cạnh tranh tài nguyên, Tiến trình hợp tác nhờ chia sẻ tài nguyên và tiến trình hợp tác nhờ trao đổi thông điệp.



### 3.6. Trình bày giải thuật Peterson cho đoạn nguy hiểm và ưu nhược điểm của phương pháp này. Phân tích xem giải thuật này có thỏa mãn các yêu cầu đối với giải pháp cho đoạn nguy hiểm, loại  trừ tương hỗ, tiến triển, chờ đợi có giới hạn hay không?
**Giải thuật Peterson:**
- Đây là giải pháp thuật toán phần mềm được đề xuất cho 2 tiến trình. P0 và P1 thực hiện đồng thời với một tài nguyên chung và một đoạn nguy hiểm chung.
- Mỗi tiến trình thực hiện vô hạn và xen kẽ giữa đoạn nguy hiểm với phần còn lại của tiến trình.
- Yêu cầu 2 tiến trình trao đổi thông tin qua 2 biến chung:
  - Turn: Xác định đến lượt tiến trình nào được vào đoạn nguy hiểm.
  - Cờ cho mỗi tiến trình: flag[i] = true nếu tiến trình thứ i yêu cầu được vào đoạn nguy hiểm
  - Thỏa mã các yêu cầu:
    - Điều kiện loại trừ tương hỗ.
    - Điều kiện tiến triển:
      - P0 chỉ có thể bị P1 ngăn cản và đoạn nguy hiểm nếu flag[1] = true và turn = 1 luôn đúng
      - Có 2 khả năng với P1 ở ngoài đoạn nguy hiểm:
        1. P1 chưa sẵn sàng vào đoạn nguy hiểm => flag[1] = false, P0 có thể vào ngay đoạn nguy hiểm
        2. P1 đã đặt flag[1] = true và đang trong vòng lặp while 
        => turn = 1 or 0 
          - Turn = 0: P0 vào đoạn nguy hiểm ngay
          - Turn = 1: P1 vào đoạn nguy hiểm, sau đó đặt flag[1] = false => quay lại khả năng 1
     - Chờ đợi có giới hạn:
       - Sử dụng trên thực tế tương đối phức tạp.
       - Đòi hỏi tiến trình đang yêu cầu vào đoạn nguy hiểm phải nằm trong trạng thái chờ đợi tích cực.
       - Chờ đợi tích cực: tiến trình vẫn phải sử dụng CPU để kiểm tra xem có thể vào đoạn nguy hiểm.
       => Lãng phí CPU




# Chương 3
## Lọai 1 điểm
### 1.13. Thế nào là địa chỉ logic và địa chỉ vật lý?
**ĐỊa chỉ logic:**
- Gán cho các lệnh và dữ liệu không phụ thuộc vào vị trí cụ thể tiến trình trong bộ nhớ.
- Chương trình ứng dụng chỉ nhìn thấy và làm việc với địa chỉ logic này.
- Là địa chỉ tương đối, tức là mỗi phần tử của chương trình được gán một địa chỉ tương đối đối với một vị trí nào đó.

**Địa chỉ vật lý:**
- Là địa chỉ chính xác trong bộ nhớ máy tính.
- Các mạch nhớ sử dụng để truy nhập tới chương trình và dữ liệu.

### 1.14. Trình bày kỹ thuật phân chương cố định bộ nhớ.
- Bộ nhớ được chia thành các chương với kích thước vị trí, số lượng không đổi.
- Có 2 phương án: các chương to bằng nhau và các chương không to bằng nhau.
  - Các chương kích thước to bằng nhau đơn giản nhưng phân mảnh trong, do đó ít được dùng trong thực tế.
  - Các chương có kích thước khác nhau: có 2 kiểu
    - Mỗi chương có một hàng đợi và tiến trình chỉ được xếp vào hàng đợi phù hợp nhất.
    - Dùng chung một hàng đợi: Chương có săn nhỏ nhất sẽ được cấp phát. Khi một chương được giải phóng chọn tiến trình gần đầu hàng đó nhất và có kích thước phù hợp.
- Phân trường cố định không mềm dẻo do hạn chế số lượng tiến trình tối đa có thể tải và ô nhớ. Do vậy hiện nay hầu như không được sử dụng.

### 1.15. Trình bày cơ chế ánh xạ địa chỉ khi sử dụng kỹ thuật phân chương bộ nhớ.
- Với phương pháp phân chương, các chương có thể nằm ở các địa chỉ khác nhau trong bộ nhớ, thậm chí có thể bị di chuyển. Do vậy, cần cơ chế biến đổi địa chỉ logic thành địa chỉ vật lý. Ngoài ra cần ngăn không cho tiến trình này truy cập trái phép chương nhớ của tiến trình khác.

![1 15](https://github.com/user-attachments/assets/12fb555c-d261-404d-9797-316170aa795a)


- Khi tiến trình được tải vào MEM, CPU dành 2 thanh ghi:
  - Thanh ghi cơ sở chứa địa chỉ bắt đầu của tiến trình.
  - Thanh ghi giới hạn chứa độ dài chương.

- Địa chỉ logic được so sánh với nội dung của thanh ghi giới hạn
  - Nếu ">" : lỗi truy cập
  - Nếu "<" : Được đưa tới bộ cận với thanh ghi cơ sở để thành địa chỉ vật lý.
- Nếu chương bị di chuyển thì nội dung của thanh ghi cơ sở bị thay đổi, chứa địa chỉ vị trí mới. 

### 1.16. Trình bày khái niệm phân đoạn bộ nhớ và ưu nhược điểm.
- Phân đoạn là phân chia tiến trình thành các phần (đoạn, tùy theo ý nghĩa của phần đó). 
  - Việc phân chia có thể do người lập trình thực hiện. 
  - Mỗi đoạn sẽ được phân vào một vùng nhớ riêng có kích thước bằng đoạn đó (Tương tự như phân chương rỗng). 
  - Mỗi một đoạn tương ứng với không gian, địa chỉ riêng được xác định bởi tên hay số thứ tự và bởi độ dài của đoạn.
- ***Ưu điểm***:
  - Dễ dàng chia sẻ các đoạn giữa các tiến trình với nhau.
  - Mỗi đoạn có thể thay đổi kích thước mà không ảnh hưởng tới các đoạn khác.
- ***Nhược điểm***: phân mảnh ngoài

### 1.17. Trình bày cơ chế ánh xạ địa chỉ khi sử dụng kỹ thuật phân đoạn bộ nhớ.
- Mỗi một tiến trình có 1 bảng đoạn, mỗi ô của bảng tương ứng với một đoạn và chứa 2 đơn vị:
  - Địa chỉ cơ sở: Vị trí bắt đầu của đoạn đó trong bộ nhớ.
  - Giới hạn: Độ dài đoạn
- Địa chỉ logic gồm:
  - **S:** stt/tên đoạn
  - **O:** độ dịch trong đoạn

![1 17](https://github.com/user-attachments/assets/8fa7aa09-3528-49ce-bf54-a6fddc73c169)

- Giải thích:
  - Từ chỉ số đoạn S, vào bảng đoạn, tìm địa chỉ vật lí bắt đầu của đoạn
  - So sánh độ dịch O với chiều dài đoạn, nếu lớn hơn => *địa chỉ sai*
  - Địa chỉ vật lý mong muốn là tổng của địa chỉ vật lý bắt đầu đoạn và địa chỉ lệch.
  
## Loại 2 điểm
### 2.13. Trình bày kỹ thuật giúp tăng tốc độ truy cập bảng trang và bảng trang nhiều mức.
- Mỗi thao tác truy nhập bộ nhớ đều yêu cầu truy nhập bảngg trang để ánh xạ địa chỉ. Do vậy, tốc độ truy nhập bảng trang ảnh hưởng lớn tới tốc độ chung của toàn bộ hệ thống.
- Do vậy, mong muốn đặt bảng trang trong loại bộ nhớ tốc độ cao. Tuy nhiên, do bộ nhớ thanh ghi và bộ nhớ cache không đủ lớn nên bảng trang thường được chứa trong RAM và tăng tốc độ truy nhập bằng 2 kỹ thuật sau:
  - Vị trí mỗi bản được chọn bởi thanh ghi cơ sở bảng trang.
  - kết hợp bộ nhớ cache để chứa 1 phần bảng trang

### 2.14. Trình bày lý do phải đổi trang và các bước tiến hành khi đổi trang.
- Đỏi trang do bộ nhớ ảo. Nếu bộ nhớ ảo lớn hơn bộ nhớ thực thì đến một lúc nào đó sẽ không còn khung trống để nạp thêm các trang mới. Khi đó có 3 giải pháp: Kết thúc tiến trình, tạm trao đổi ra đĩa, đổi trang.
- Quá trình đổi trang:
  1. Xác định trang cần nạp trên đĩa.
  2. Nếu có khung trống thì chuyển sang bước 4.
  3.   
        - Lựa chọn một khung để giải phóng theo một thuật toán nào đó.
        - Ghi nội dung khung bị đổi ra đĩa.(Nếu cần)
  4. Đọc trang cần nạp vào khung vừa giải phóng. Cập nhật bảng trang và bảng khung.
  5. Thực hiện tiếp tiến trình từ điểm bị dừng trước khi đổi trang.

### 2.15. Trình bày kỹ thuật đổi trang tối ưu và đổi trang vào trước ra trước.
**Kỹ thuật đổi trang tối ưu:**
- Chọn trang sẽ không được dùng tới trong thời gian lâu nhất để đổi. Cách này sinh ra số lần lỗi trang ít nhất, do vậy nó tối ưu theo số lần lỗi trang.
- Tuy nhiên, trên thực tế, HĐH không biết trước trang nào sẽ được sử dụng vào lúc nào, do vậy thuật toán này không dùng được mà chỉ được dùng làm tiêu chuẩn để đánh giá cái khác.

**Kỹ thuật đổi trang vào trước ra trước:**
- Trang nào vào trước sẽ bị đẩy ra trước
- Ưu điểm chính của chiến lược này là dễ dàng cài đặt. Tuy nhiên, phương pháp này có số trang lỗi rất cao.

### 2.16. Trình bày phương pháp xác định số lượng khung trang tối đa cấp cho mỗi tiến trình và xác định phạm vi cấp phát.
**Giới hạn số lượng khung cấp cho mỗi tiến trình:**
- Vấn đề là HĐH cần cấp cho mỗi tiến trình bao nhiêu khung
- Nếu cấp quá ít khung thì sẽ dân tới đổi trang thường xuyên, làm giảm hiệu quả của tiến trình.Tuy nhiên, cấp quá nhiều khung sẽ ảnh hưởng tới tiến trình khác và làm lãng phí.

**Trên thực tế có 2 chiến lược cấp phát số khung:**
- ***Cấp phát cố định:*** Mỗi tiến trình được cấp một khung số lượng cố định trong suốt quá trình.
- ***Cấp phát động:*** Tùy theo nhu cầu của tiến trình mà số lượng cung cấp cho tiến trình có thể thay đổi. Cách này cho phép dùng bộ nhớ hiệu quả hơn cách 1 nhưng HĐH phức tạp hơn, phải theo dõi và xử lý tần suất đổi trang của các tiến trình.

### 2.17. Trình bày phương pháp kết hợp phân trang và phân đoạn. Vẽ sơ đồ và giải thích cơ chế ánh xạ địa chỉ.
- Phân đoạn tiến trình, sau đó mỗi đoạn sẽ được phân trang để xếp vào ô nhớ. Mỗi tiến trình có 1 bảng đoạn và mỗi đoạn có 1 bảng trang riêng. Địa chỉ gồm 3 phần: stt đoạn, stt trang và độ dịch trong trang
- Tiến trình có 1 bảng phân đoạn, mỗi đoạn có 1 bảng phân trang.

![2 17](https://github.com/user-attachments/assets/16cd788a-db54-45a2-936b-2431c821b693)


### 2.18*. Trình bày về tình trạng trì trệ (Thrashing)
- là tình trạng đổ trang liên tục do không đủ bộ nhớ.
- Thời gian đổi trang của tiến trình lớn hơn thời gian thực hiện.
- Xảy ra khi:
  - Kích thước bộ nhớ hạn chế.
  - Tiến trình đòi hỏi truy cập, đồng thời nhiều trang nhớ.
  - Hệ thống có mức độ đa chương trình cao.
- Khi tiến trình rơi vào tình trạng trì trệ, tần suất thiếu trang tăng đáng kể.

**=> Sử dụng để phát hiện và giải quyết vấn đề trì trệ.**
- Theo dõi và ghi lại tần suất thiếu trang.
- Có thể đặt ra giới hạn trên và giới hạn dưới cho tần suất thiếu trang của tiến trình.
  - Tần suất vượt giới hạn trên:
    - Cấp thêm cho tiến trình khung mới.
    - Nếu không thể tìm khung để cấp thêm, tiến trình sẽ bị treo hoặc kết thúc.
  - Tần suất thấp hơn giới hạn dưới: Thu hồi một số khung của tiến trình.
 
### 2.19. Trình bày kỹ thuật sử dụng đệm trang. Ưu điểm.
- HĐH dành ra một số trang trống được kết nối thành các danh sách liên kết gọi là các trang đệm.
- Trang bị đổi như bình thường nhưng nội dung trang này không bị xóa ngay khỏi bộ nhớ.
- Khung chứa trang được đánh dấu là khung trống và thêm vào cuối danh sách trang đệm.
- Trang mới sẽ được nạp vào khung đứng đầu trong danh sách trang đệm.
- Tới thời điểm thích hợp, hệ thống sẽ ghi nội dung các trang trong danh sách đệm ra đĩa.
- **Ưu điểm:**
  - HĐH có thể lùi được ghi các trang ra đĩa đệm một thời điểm thuận lợi hơn và ghi đồng thời nhiều trang nhớ đánh dấu trống.
  - Nếu thuật toán đổi trang chọn nhầm trang thì vẫn có cơ hội sửa sai do trang bị đổi vẫn nằm trong đệm trang thêm 1 thời gian nữa.

## Loại 3 điểm
### 3.7. Trình bày kỹ thuật tải trong quá trình thực hiện. Trình bày kỹ thuật liên kết động và thư viện dùng chung. Phân tích rõ ưu điểm từng phương pháp mang lại.
- **Tải trong quá trình thực hiện:**
  - Thực tế không phải chương trình nào cũng cần tới tất cả các phần của mình trong một phiên làm việc.
  - Từ nhận xét này, thay vì tải toàn bộ chương trình bộ nhớ, ta chỉ tải chương trình chính.,
  Chương trình sẽ kiểm tra hàm đó được tải vào chưa. Nếu chưa, chương trình sẽ tiến hành tải, sau đó ánh xạ địa chỉ hàm vào không gian chung của chương trình và thay đổi bảng địa chỉ để ghi lại các ánh xạ đó.
- **Liên kết động và thương hiệu dùng chung**
  - Theo các liên kết tĩnh, các hàm thư viện được liên kết ngay vào chương trình, do vậy các hàm không dùng thường xuất hiện nhiều lần trong các chương trình khác nhau, gây ra dư thừa và tốn không gian lưu trữ.
  - Để tiết kiệm không gian nhớ trong giai đoạn liên kết, không liên kết các hàm vào chương trình mà chỉ chèn một đoạn thông tin về hàm đó.
  - Các module thư viện được liên kết trong quá trình thực hiện sử dụng các thông tin chứa trong stub*.

### 3.8. Trình bày kỹ thuật phân chương động bộ nhớ. Phân tích ưu nhược điểm của phương pháp này so với phân chương cố định. Lấy ví dụ minh họa cho các chiến lược cấp chương đồng mà HĐH thường sử dụng: first fit, best fit, worst fit. Khi di chuyển trường sang vị trí khác cần thay đổi thông tin gì trong khối ánh xạ địa chỉ?
**Phần chương động:**
- Kích thước, số lượng và vị trí của chương có thể thay đổi.
- Mỗi một tiến trình được cấp một trước nhớ có kích thước đúng bằng chương đó, khi tiến trình kết thúc, chương nhớ được giải phóng tạo thành một vùng trống. Các vùng trống nằm liền nhau gộp thành vùng trống lớn hơn. Các chương nhớ và các vùng trống được liên kết với nhau thành danh sách kết nối.

![3 8](https://github.com/user-attachments/assets/fd3b95ee-fc4b-4da6-b0b1-ae5da25a78f6)

- Do các trường được tạo ra đúng bằng kích thước tiến trình nên không có phân mảnh trong, tuy nhiên có phân mảnh ngoài.
- Ảnh hưởng của phân mảnh ngoài có thể khá lớn, gây lãng phí bộ nhớ.
- Có 2 cách giải quyết:
  - Chuyển các tiến trình về một đầu bộ nhớ, khi đó các vùng trống sẽ được chuyển về đầu còn lại và nhập thành vùng trồng lớn hơn. Tuy nhiên, việc chuyển như vậy sẽ làm hệ thống phải dừng lại, ảnh hưởng đến tốc độ.
  - Hạn chế phân mảnh ngoài= cách sử dụng chiến lược các chương sử dụng. Có 3 chiến lược cấp chương:
    - ***First Fit:*** Trong số các vùng trống chọn vùng nhớ đầu tiên có thể chứa tiến trình để cấp phát.
    - ***Best Fit:*** Trong số các vùng trống chọn vùng nhỏ nhất có thể chưa tiến trình để tạm chương nhớ. Chiến lược này có xu hướng tạo ra vùng trống kích thước nhỏ.
    - Worst Fit: Chọn vùng trống có kích thước lớn nhất để tạo, chưa nhớ và cấp phát.
- Ưu điểm: Tránh phân mảnh trong (nhược điểm phân chương cố định)
- Nhược điểm: Phân mảnh ngoài.
- VD: Trong bộ nhớ có 4 vùng trống có kích thước lần lượt là 3 MB, 8 MB, 7 MB, 10 MB, Yêu cầu cấp phát vùng nhớ kích thước 6 MB:
  - Chiến lược FF sẽ chọn khối 8 MB để chia và cấp phát
  - Chiến lược BF sẽ chọn vùng trống 7 MB
  - Chiến lược WF sẽ chọn 10 MB
- Nếu chương bị di chuyển thì nội dung của thanh ghi cơ sở bị thay đổi chứa địa chỉ vị trí mới.

### 3.9. Trình bày kỹ thuật phân đoạn bộ nhớ, bao gồm cả cấu trúc và các ánh xạ địa chỉ. So sánh ưu nhược điểm của phân đoạn với phân trang.

(go to 1.16 and 1.17)
**So sánh:**
- Phân trang và phân đoạn đều có ưu điểm riêng. Fontchanger đơn giản hơn do các cha có kích thước bằng nhau. Trong khi đó, phân đoạn cho phép tiến tới cấu trúc của tiến trình.
- Phân đoạn đã khắc phục được phân mảnh trong của phân trang. Tuy nhiên, nhược điểm của phân đoạn là phân mảnh ngoài.

### 3.10. Trình bày kỹ thuật nạp trang theo nhu cầu dùng cho bộ nhớ ảo, bao gồm: khái niệm, ví dụ minh họa, quá trình thực hiện ngắt thiếu trang. Nạp trang hoàn toàn theo nhu cầu khác với nạp trang trước như thế nào? Phân tích rõ cùng một lệnh có thể xảy ra nhiều sự kiện lỗi trang không.
- **Nạp trang theo nhu cầu:**
  - ***Khái niệm:*** Tiến trình được phân trang và chứa trên đĩa. Khi tiến trình thực hiện cần đến trang nào thì trang đó sẽ được nạp vào bộ nhớ. Như vậy, tại một thời điểm, mỗi tiến trình sẽ gồm một số trang đã được nạp vào bộ nhớ. Những trang còn lại vẫn nằm trên đĩa. Để phân biệt 2 loại này, người ta đã thêm vào khoảng một trang, một bit ký hiệu là p (p = 1: trang đã nằm trong bộ nhớ, p = 0: trang đã nằm trên đĩa)

![3 10](https://github.com/user-attachments/assets/0657d9af-b6df-479e-b1b8-0de196354a6c)

- **Quá trình thực hiện ngắt thiếu trang:**
  - Đọc trang bị thiếu và không trang vừa tìm được.
  - Sửa lại khoản mục tương ứng trong bảng trang: đổi bit p = 1 và số khung trang đã cấp cho trang
  - Khôi phục lại trạng thái tiến trình và thực hiện tiếp lệnh bị ngắt.
- **Nạp trang trước và nạp trang theo nhu cầu:**
  - Nạp trang trước là cách truyền thống, tức là nạp tất cả các trang và bộ nhớ.
  - Nạp trang hoàn toàn theo nhu cầu: Tiến trình khởi đầu mà chưa có trang nào trong bộ nhớ, tức là ngay lệnh đầu tiên sẽ gây ra lỗi trang. Trên thực tế thường dùng giải pháp trung gian, tức là nạp sẵn 1 số lượng trang nhất định vào trong ô nhớ.
- **Cùng một lệnh có thể gây ra sự kiện lỗi trang**. Khi tiến trình truy cập bộ nhớ để thực hiện một lệnh sẽ xảy ra 2 tình huống:
  - Trang cần truy cập đã ở trong bộ nhớ *(p = 1)*, truy cập bình thường.
  - Trang đó chưa nằm trong bộ nhớ *(p = 1)*. Khi đó sẽ xảy ra sự kiện lỗi trang hoặc thiếu trang, hệ thống sẽ sinh ra bộ ngắt và chuyển cho HĐH xử lý.


# Chương 4
## Loại 1 điểm
### 1.18. Việc định nghĩa và sử dụng khái niệm file đem lại những ưu điểm gì? Khi đặt tên cho file, cần quan tâm tới những quy định gì?
- Nhờ có khái niệm file, người dùng có thể quyết định cấu trúc, ý nghĩa, cách sử dụng cho thông tin cần lưu trữ và đặt tên cho tập các thông tin này. Người dùng có thể không quan tâm tới việc file được lưu trữ cụ thể ở đâu, ra sao.

![1 18](https://github.com/user-attachments/assets/a806d016-67f6-421d-9ccc-dee79ef751c2)


### 1.19. Trình bày khái niệm thư mục. Thông tin trong các khoản mục có nhất thiết phải lưu trữ gần nhau không.
- Để quản lý các file, thông tin về file được lưu tập trung trong thư mục. Như vậy, thư mục là các khoản mục, mỗi khoản mục chứa thông tin về một file.
- Thông tin trong các khoản mục không nhất thiết phải lưu trữ gần nhau vì khoản mục có thể chứa con trỏ trỏ tới các thông tin của file hoặc chứa các thông tin của file.

### 1.20. HĐH có cần biết và hỗ trợ các kiểu cấu trúc file hay không?
- Nếu HĐH hỗ trợ cấu trúc file thì ta có 2 ưu điểm:
  - Thao tác truy cập file sẽ dễ dàng hơn với người lập trình.
  - HĐH có thể kiểm soát được các thao tác với file bằng cách kiểm tra xem thao tác đó có phù hợp với cấu trúc của file hay không.
- Nhược:
  - Kích thước HĐH tăng nhanh do có nhiều kiểu cấu trúc file, và mỗi kiểu lại phải có modul riêng để quản lý và hỗ trợ.
  - Tính mềm dẻo hạn chế. Đôi khi ta cần xử lý file theo các cách khác nhau.

## Loại 2 điểm
### 2.20. Trình bày các cấu trúc dữ liệu dùng cho tổ chức bên trong của thư mục



### 2.21. Trình bày cách kiểm soát truy cập file sử dụng mật khẩu và sử dụng danh sách quản lý truy cập
- **Sử dụng mật khẩu:** Mỗi một file cũng được gắn với mật khẩu để truy cập file người dùng hoặc chương trình cung cấp mật khẩu đó.
  - Nhược điểm:
    - Người dùng phải nhớ mật khẩu.
    - Mỗi lần truy cập đều yêu cầu mật khẩu dẫn đến mất thời gian.
- **Sử dụng danh sách quản lý truy cập:**
  - Mõi người dùng khi đăng ký trong hệ thống người dùng cần đăng nhập, sau khi đăng nhập xong UID (số định danh người dùng) sẽ được sử dụng trong suốt thời gian làm việc. 
  - Mỗi file được gắn một danh sách đi kèm gọi là danh sách quản lý truy cập ACL. Danh sách này chứa UID và các quyền mà người đó được thực hiện 
  - Khi người dùng yêu cầu truy cập file, hệ thống sẽ so sánh ID của người dùng với ACL của file để quyết định có cho truy cập hay không.

### 2.22. Trình bày các thao tác cơ bản với file. Phân tích rõ một hệ thống file có nhất thiết phải có thao tác mở file hay không.
- Tạo file: Tạo file trống chưa có data; được dành một chỗ trong thư mục.
- Xóa file: Giải phóng không gian mà dữ liệu của  chiếm; Giải phóng chỗ của file trong thư mục.
- Mở file: Thực hiện trước khi ghi và đọc file. Đọc các thuộc tính của file và MEM để tăng tốc độ.
- Đóng file: Xoá các thông tin về file ra khỏi bảng trong MEM
- Đọc file: Thông tin ở vị trí hiện thời sẽ được đọc. Lệnh đặt file cần cung cấp thông tin về số lượng byte hoặc bản ghi cần đọc và nơi chứa dữ liệu được đọc từ file.
- Ghi vào file: Ghi vào file tại vị trí được cung cấp. 
- Định vị(seek): Đối với file truy cập trực tiếp, thao tác định vị cho phép xác định vị trí hiện thời để tiến hành đọc/ghi.
- Đọc thuộc tính của file
- Thay đổi thuộc tính của file

### 2.23. Trình bày về cấu trúc hệ thống thư mục một mức và hai mức
- Thư muc 1 mức: Toàn bộ đĩa chỉ có một thư mục chứa các file của hệ thống đó => Chỉ thích hợp với hệ thống đơn giản, ít file, 1 người dùng.
- Thư mục 2 mức:
  - Thơm một gốc trời ơi, cắt thêm 1 con thư mục con chứa các file.
  - Nhược điểm: Cô lập người dùng. Các file mà nhiều người dùng truy cập tới phải chép và từng thu mục của từng người dùng => lãng phí.


### 2.24. Trình bày phương pháp cấp phát không gian cho file bằng các khối liên tiếp. Cho ví dụ minh họa. Ưu nhược điểm của phương pháp này là gì?


### 2.25. Trình bày về các phương pháp quản lý không gian trống trên đĩa: bảng bit, danh sách kết nối và danh sách vùng trống.



## Loại 3 điểm
### 3.11. Trình bày cấu trúc thư mục dạng cây và dạng đồ thị không có chu trình. Cấu trúc thư mục dạng không chu trình có ưu điểm gì so với dạng cây ? Thế nào là đường dẫn tuyệt đối và đường dẫn tương đối.


### 3.12. Trình bày phương pháp cấp phát không gian cho file sử dụng danh sách kết nối và sử dụng khối chỉ số (I-node) (có ví dụ minh họa). Hai phương pháp này có điểm gì giống và khác nhau.



### 3.13. Trình bày về yêu cầu phải đảm bảo tính toàn vẹn của hệ thống file và các phương pháp đảm bảo tính toàn vẹn.


### 3.14. Trình bày hai phương pháp cấp phát không gian cho file : sử dụng danh sách kết nối và sử dụng danh sách kết nối trên bảng chỉ số (có ví dụ minh họa). So sánh sự giống nhau và khác nhau của hai phương pháp này

# Bài toán Triết gia ăn cơm
```cpp
bool chopstick[5] = {false, false, false, false, false};
void philosopher(int i) {
    for (;;) {

        while (Test_and_Set(chopstick[i]));
        while (Test_and_Set(chopstick[(i + 1) % 5]));

        <ăn cơm>

        chopstick[i] = false;
        chopstick[(i + 1) % 5] = false;

        <suy nghĩ>
    }
}

void main() 
{
    Start process(philosopher[1]);
    Start process(philosopher[2]);
    Start process(philosopher[3]);
    Start process(philosopher[4]);
    Start process(philosopher[5]);
}
```

# Bài toán Người sản xuất, người tiêu dùng với bộ đệm hạn chế
```cpp
const int N; //kích thước bộ ñệm
semaphore lock = 1;
semaphore empty = 0;
semaphore full = N;

void producer () {                        //tiến trình người sản xuất
    for (;;) {
        <sản xuất>

        wait (full);
        wait (lock);

        <thêm một sản phẩm vào bộ đệm>

        signal (lock);
        signal (empty);
    }
}

void consumer () {                        //tiến trình người tiêu dùng
    for (;;) {
        wait (empty);
        wait (lock);

        <lấy một sản phẩm từ bộ đệm>
        
        signal (lock);
        signal (full);
        
        <tiêu dùng>
    }
}

void main()
{
    StartProcess(producer); 
    StartProcess(consumer);
}

```
