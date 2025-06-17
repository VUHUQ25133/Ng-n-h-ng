# Trích lớp thực thể
Sử dụng kỹ thuật trích danh từ

## 1. mô tả modul trong 1 đoạn văn (xét toàn bộ kịch bản chuẩn + ngoại lệ của modul)
## 2. Trích tất cả các danh từ xuất hiện trong 1 đoạn văn (kết hợp với các đối tượng trong câu hỏi 4 của BM)
## 3. Đánh giá các danh từ:
* Bị loại: trừu tượng, chung chung, ngoài phạm vi
* Chỉ để làm thuộc tính
* Đề xuất thành các lớp thực thể
## 4. Xét quan hệ số lượng giữa các danh từ (xem lại câu hỏi số 5 của BM)
* 1-1: Giữ nguyên/gộp lại
* 1-n: giữ nguyên
* n-n: phải tách thành >= 2 quan hệ 1-n

## 5. Xét quan hệ đói tượng giữa các lớp
* Kế thừa
* Thành phần:
    * lỏng (aggregation)
    * chặt (composition)
* Liên kết (association)

## Kết quả: Biểu đồ lớp thực thể của modul

# Thiết kế biểu đồ lớp chi tiết
## 1. copy các lớp thực thể liên quan của modul từ biểu đồ lớp thực thể của pha thiết kế
## 2. Với mỗi giao diện:
* Đề xuất lớp GD tương ứng
* Thiết kế các thuộc tính tường minh (tương tác với user)
* Thiết kế các thuộc tính ẩn (dùng lưu trữ/đựng DL từ form trước đấy gửi sang). Nếu có thuộc tính ẩn, hàm khởi tạo phải nhận tham số vào tương ứng với các thuộc tính ẩn (nếu không so tham số này thì sẽ không tạo được form)
* Thiết kế các phương thức xử lí sự kiện trên Giao diện
## 3. Nếu lớp Giao diện cần thao tác vào ra với dữ liệu hệ thống, ĐỀ XUẤT CÁC LỚP DAO (Controller) tương ứng
Với mỗi thao tác:
* Thiết kế phương thức tương ứng
* Thiết kế tham số vào & tham số ra của phương thức
* Gán phương thức cho lớp DAO liên quan đến tham số ra, tham số vào

## 4. Lặp lại bước 2 & 3 đến khi hết các Giao diện chức năng


# I. Phần mềm quản lí thư viện
Khách hàng yêu cầu chúng ta phát triển một phần mềm **quản lí thư viện**,:

* Mỗi đầu sách (Mã, tên, tác giả, năm xuất bản, giá bìa, số lượng, mã vạch, mô tả) có thể được mượn nhiều lần khác nhau bởi nhiều bạn đọc khác nhau
* Mỗi bạn đọc có một thẻ bạn đọc chứa mã, tên, ngày sinh, địa chỉ, số điện thoại, mã vạch của bạn đọc đó
* Mỗi lần mượn được mượn tối đa 5 quyển sách, và tổng số sách đang mượn bởi một người cũng không được quá 5 quyển
* Thời gian tối đa mượn 1 quyển sách là 1 tháng kể từ ngày mượn quyển đó, nếu trả sau thời hạn này thì sẽ bị phạt 20% giá trị bìa sách.
* Mỗi lần trả sách có thể trả một phần hoặc toàn bộ số lượng sách đang mượn
* Khi mượn sách mới, thủ thư vẫn xem được danh sách các sách mà một độc giả đã mượn và trả rồi hoặc chưa trả trước đấy.

## 1. Modul "Quản lí việc mượn sách": 
* Nhân viên chọn menu cho mượn sách  
* →  quét thẻ độc giả để lấy thông tin độc giả 
* →  thông tin chi tiết độc giả hiện lên + danh sách các sách mượn chưa trả + danh sách sách mượn đã trả 
* →  nhân viên quét lần lượt các sách được chọn mượn 
* →  danh sách sách mượn được bổ sung thêm cho đến khi hết sách chọn mượn (hoặc tối đa 5 quyển) thì submit 
* →  in ra phiếu mượn chứa mã, tên, mã vạch độc giả, mã vạch phiếu mượn, và danh sách sách còn mượn, mỗi đầu sách trên một dòng: mã, tên sách, tác giả, mã vạch, ngày mượn, ngày phải trả và dòng cuối cùng ghi tổng số sách đang mượn.
## 2. Modul "Quản lí việc trả sách": 
* Nhân viên chọn menu trả sách  
* →  quét thẻ độc giả để lấy thông tin độc giả 
* →  thông tin chi tiết độc giả hiện lên + danh sách các sách mượn chưa trả + danh sách sách mượn đã trả 
* →  nhân viên quét lần lượt các sách được trả 
* →  danh sách sách đang mượn được rút ngắn cho đến khi hết sách mượn (hoặc hết số sách độc giả đem đến trả) thì submit 
* →  in ra phiếu mượn (nếu còn sách mượn) chứa mã, tên, mã vạch độc giả, mã vạch phiếu mượn, và danh sách sách còn mượn, mỗi đầu sách trên một dòng: 
       * mã, tên sách, tác giả, mã vạch, ngày mượn, ngày phải trả 
       * và dòng cuối cùng ghi tổng số sách đang mượn + phiếu phạt (nếu bị phạt) chứa mã, tên, mã vạch độc giả, mã vạch phiếu mượn, và danh sách sách trả muộn bị phạt, 
       * mỗi đầu sách trên một dòng: mã, tên sách, tác giả, mã vạch, ngày mượn, ngày phải trả, ngày trả, số tiền phạt và dòng cuối cùng ghi tổng số tiền phạt
## 3. Modul "Thống kê sách mượn nhiều": 
* Nhân viên chọn menu thống kê  
* →  chọn thống kê sách mượn nhiều 
* →  nhập khoảng thời gian (bắt đầu - kết thúc) 
* →  danh sách sách mượn nhiều nhất được hiển thị theo thứ tự số lượt mượn từ nhiều đến ít, mỗi dòng chứa: mã, tên sách, tác giả, mã vạch, tổng số lượt mượn. NV click vào 1 dòng của 1 sách thì hiện lên danh sách chi tiết những lần độc giả nào mượn quyển sách đấy
## 4. Modul "Thống kê độc giả mượn nhiều": 
* Nhân viên chọn menu thống kê  
* →  chọn thống kê độc giả mượn nhiều 
* →  nhập khoảng thời gian (bắt đầu - kết thúc) 
* →  danh sách độc giả đã mượn nhiều nhất được hiển thị theo thứ tự số lượng sách mượn từ nhiều đến ít, mỗi dòng chứa: mã, tên, ngày sinh, địa chỉ độc giả, tổng số lượng sách đã mượn. NV click vào 1 dòng của 1 độc giả thì hiện lên chi tiết các phiếu mượn với thông tin ngày mượn, tổng số sách của từng lần mượn.

# II. Phần mềm quản lí kết quả học tập của sinh viên theo tín chỉ
Khách hàng yêu cầu chúng ta phát triển một phần mềm **quản lí kết quả học tập của sinh viên theo tín chỉ**,:

* Mỗi sinh viên (Mã SV, mật khẩu, tên, ngày sinh, khóa, quê quán, địa chỉ) được phép đăng kí tối thiểu 10 tín chỉ/học kì và tối đa 15 tín chỉ/học kì
* Mỗi sinh viên được đăng kí nhiều môn học (mã môn, tên môn, số tín chỉ)
* Mỗi môn học có thể có nhiều môn học yêu cầu sinh viên phải hoàn thành trước đó thì mới được đăng kí
* Mỗi môn học có thể có nhiều lớp học phần 
    (mã lớp, tên lớp, số sv tối đa, phòng học, khung giờ học cố định trong tuần)
* Sinh viên không được phép đăng kí học hai lớp có trùng buổi học
* Với mỗi môn học, một sinh viên chỉ được đăng kí vào 1 lớp xác định
* Kết quả của sinh viên (điểm thành phần số 1, số 2, số 3, điểm thi, 
    điểm cuối cùng= x % số1 + y % số2 + z % số3 + w % điểm thi) được lưu theo từng môn học 
* Điểm trung bình của sinh viên trong học kì được tính bằng trung bình có trọng số là số tín chỉ từng môn học

## 1. Modul "Lên lịch học cho lớp học phần": 
* QL chọn menu lên lịch học cho lớp học phần 
* →  giao diện lên lịch học hiện ra với các ô sổ chọn môn học, lớp học phần, phòng học, khung giờ, nút xác nhận 
* →  QL click chọn môn học từ danh sách sổ xuống 
* →  Danh sách lớp học phần của môn học học được cập nhật 
* →  QL click chọn thêm 1 lớp học phần của môn học 
* →  click chọn phòng học từ danh sách phòng học sổ xuống + click chọn khung giờ trong tuần từ danh sách khung giờ sổ xuống + click xác nhận 
* →  Hệ thống lưu lịch học vào CSDL và thông báo thành công.

## 2. Modul "Nhập điểm theo lớp học phần": 
* GV chọn chức năng nhập điểm 
* →  giao diện hiện ra danh sách các môn học do GV dạy 
* →  GV click chọn 1 môn học 
* →  giao diện hiện ra danh sách các lớp học phần của môn học đã chọn do GV dạy 
* →  GV click chọn 1 lớp học phần 
* →  Giao diện hiện lên danh sách các sinh viên trong lớp học phần, mỗi SV trên 1 dòng với các cột điểm thành phần và cột điểm thi 
* →  GV nhập đầy đủ các đầu điểm của các SV + click xác nhận 
* →  Hệ thống lưu vào CSDL và thông báo thành công.

## 3. Modul "Đăng kí học": 
* SV đăng nhập 
* →  chọn menu đăng kí tín chỉ cho học kì mới 
* →  trang đăng kí hiện ra 
* →  sinh viên chọn môn học trong danh sách môn học + chọn lớp trong danh sách các lớp (và giảng viên đi kèm) tương ứng với môn học 
* →  nếu thỏa mãn các ràng buộc nêu trên thì thông báo thành công + in ra phiếu đăng kí cho sinh viên: 
       mã SV, tên SV, khóa học, học kì + danh sách các môn học đã đăng kí, 
       mỗi môn có: mã MH, tên MH, số tín chỉ, giờ học, giảng viên

## 4. Modul "Xem TKB của sinh viên": 
* SV chọn menu xem TKB 
* →  Giao diện xem TKB hiện lên với phía trên là ô chọn các cách xem TKB theo: tuần, học kỳ 
* →  SV chọn xem theo tuần 
* →  Phía dưới cập nhật hiển thị thời khóa biểu theo tuần hiện tại của SV: 
      1 bảng có 7 cột tương ứng 7 ngày, 6 hàng tương ứng 6 kíp học cho mỗi ngày. 
    Trong mỗi ô của bảng hiển thị tên môn học, nhóm môn học, và tên phòng học tương ứng với khung giờ đó

## 5. Modul "Thống kê sinh viên khá giỏi": 
* quản lí đăng nhập 
* →  chọn menu thống kê 
* →  chọn thống kê sinh viên giỏi 
* →  trang kết quả hiện ra danh sách SV: 
    mã SV, tên SV, khóa học, học kì, tổng số tín chỉ đã học trong học kì, 
    điểm trung bình môn cuối học kì, sắp xếp theo điểm trung bình cả học kì, từ cao đến thấp. 
    NV click vào 1 dòng của 1 SV thì hiện lên chi tiết bảng điểm từng môn học mà SV đã học trong học kì.

## 6. Modul "Thống kê môn học theo tỉ lệ sinh viên qua": 
* quản lí đăng nhập 
* →  chọn menu thống kê  
* →  chọn thống kê môn học của từng giáo viên dạy theo tỉ lệ SV qua môn 
* →  trang kết quả hiện ra danh sách môn học: 
    mã MH, tên MH, số tín chỉ, điểm trung bình của các SV trong môn học, tỉ lệ SV qua môn trong các nhóm (tính %). 
    Kết quả được sắp xếp theo tỉ lệ SV qua môn học đó từ cao đến thấp. 
    NV click vào 1 dòng của 1 MH thì hiện lên chi tiết bảng điểm của tất cả các SV đã học MH

# III. Phần mềm quản lí đặt tour du lịch
Khách hàng yêu cầu chúng ta phát triển một phần mềm **quản lí đặt tour du lịch**,:

* Mỗi tour (Mã tour, tên, nơi xuất phát, nơi đến, mô tả) có thể xuất phát vào nhiều ngày khác nhau, tùy vào ngày xuất phát và số lượng người mua tour cho mỗi đoàn sẽ có giá khác nhau. 
* Mỗi khách hàng (Mã, tên, số ID, loại thẻ ID, số ĐT, email, địa chỉ) có thể mua vé nhiều tour khác nhau. Mỗi tour có thể mua số lượng vé khác nhau. Mỗi lần mua có xuất hóa đơn ghi rõ thông tin tour, ngày xuất phát, giá tour, số lượng khách, tên khách hàng đại diện, tổng số tiền thanh toán.
* Cùng một khách hàng có thể đi cùng một tour nhiều lần, chỉ khác nhau ở ngày xuất phát và giá vé.
* Khách hàng có thể trả vé, nếu trả trước giờ xuất phát trước 7 ngày thì phạt 10%, trước 5 ngày phạt 20%, trước 3 ngày phạt 50%, trước ít hơn 3 ngày phạt 100% giá ghi trên vé.

## 1. Modul "Mua vé": 
* Nhân viên chọn chức năng mua vé theo yêu cầu của khách 
* →  giao diện tìm tour (theo tên nơi đến) 
* →  NV nhập tên nơi đến và bấm tìm 
* →  kết quả hiện ra gồm danh sách các tour còn chỗ trống tương ứng với tiêu chí đã chọn, mỗi tour hiển thị đấy đủ thông tin + ngày xuất phát + giá tương ứng tại thời điểm tìm 
* →  NV chọn 1 tour theo lựa chọn của KH 
* →  hóa đơn (vé) hiện ra chi tiết: tên tour, nơi đi, nơi đến, ngày đi, tên khách đại diện đoàn, số ID, kiểu ID, địa chỉ khách, số điện thoại, email, số lượng khách, giá vé 
* →  NV chọn thanh toán 
* →  khách hàng thanh toán 
* →  hệ thống lưu kết quả vào và in vé cho khách hàng.

## 2. Modul "Khách hàng hủy bỏ đặt tour": 
* Nhân viên chọn chức năng trả vé theo yêu cầu của khách 
* →  giao diện nhập mã vé hiện ra 
* →  NV nhập mã 
* →  kết quả hiện ra vé chi tiết: tên tour, nơi đi, nơi đến, ngày đi, tên khách đại diện đoàn, số ID, kiểu ID, địa chỉ khách, số điện thoại, email, số lượng khách, giá vé 
* →  NV chọn hủy vé 
* →  hệ thống hiện hóa đơn phạt bao gồm thông tin như trên vé + tiền phạt theo khung quy định 
* →  NV nhấn Ok 
* →  hệ thống lưu kết quả vào hệ thống, và nhân viên gửi lại phần tiền thừa cho khách hàng.

## 3. Modul "Thống kê tour theo doanh thu": 
* Quản lí chọn chức năng thống kê các tour theo doanh thu  
* →  giao diện chọn thời gian thống kê (ngày bắt đầu - kết thúc) hiện ra 
* →  quản lí chọn xong bấm thống kê 
* →  kết quả hiện ra gồm danh sách các tour chi tiết: mã, tên, tên, nơi xuất phát, nơi đến, trung bình số khách/tour, tổng doanh thu. 
        Sắp xếp theo tổng doanh thu, xếp từ cao đến thấp. 
    NV click vào một dòng của một tour, hệ thống hiện ra danh sách chi tiết các hóa đơn của khách đã đặt mua tour đó, mỗi hóa đơn trên 1 dòng: 
        id, tên khách, ngày giờ xuất phát, tổng số khách, tổng số tiền

## 4. Modul "Thống kê doanh thu theo địa điểm": 
* Quản lí chọn chức năng thống kê doanh thu theo địa điểm du lịch 
* →  giao diện chọn thời gian thống kê (ngày bắt đầu - kết thúc) hiện ra 
* →  quản lí chọn xong bấm thống kê 
* →  kết quả hiện ra gồm danh sách các địa điểm chi tiết: tên, số lượng tour đến địa điểm đấy, tổng số lượng khách đến địa điểm đấy, tổng doanh thu. 
        Sắp xếp theo tổng doanh thu, xếp từ cao đến thấp.
    NV click vào một dòng của một địa điểm, hệ thống hiện ra danh sách chi tiết các hóa đơn của khách đã đặt mua tour qua địa điểm đó, mỗi hóa đơn trên 1 dòng: 
        id, tên khách, ngày giờ xuất phát, tên tour, tổng số khách, tổng số tiền

# IV. Phần mềm quản lí việc gọi món trong một nhà hàng
Khách hàng yêu cầu chúng ta phát triển một phần mềm **quản lí việc gọi món trong một nhà hàng**,:

* Nhà hàng có nhiều bàn (Mã bàn, tên, số lượng khách tối đa, mô tả). Nhiều bàn nhỏ có thể gộp lại thành một bàn lớn khi có yêu cầu từ đoàn khách có số lượng lớn.
* Mỗi bàn, có thể bị đặt nhiều lần khác nhau trong ngày, hoặc khác ngày.
* Mỗi khách hàng (Mã, tên, số ĐT, email, địa chỉ) có thể đặt bàn nhiều lần, mỗi lần có thể đặt nhiều bàn (trường hợp này sẽ bị gộp thành đặt 1 bàn)
* Nhà hàng có thể lên combo dạng kết hợp sẵn một số món ăn đủ cho 1 bữa ăn cho một người ăn. Khách hàng có thể gọi combo có sẵn như thế này.
* Khách hàng ở mỗi bàn có thể gọi nhiều món ăn (Mã, loại, tên, mô tả, giá hiện tại) hoặc combo. Mỗi món ăn (combo) có có thể bị gọi với số lượng khác nhau. 
* Khi thanh toán, hóa đơn ghi đầy đủ thông tin: mã bàn, tên và mã nhân viên thanh toán, tên khách hàng nếu có, sau đó là một bảng, mỗi dòng chứa thông tin một món (combo) đã dùng: id, tên, đơn giá, sơ lượng, thành tiền. Dòng cuối cùng ghi tổng số tiền của hóa đơn.

## 1. Modul "Gọi món": 
* Nhân viên chọn chức năng gọi món     
* →  giao diện bàn hiện ra với danh sách bàn và số hiệu sổ xuống 
* →  NV chọn bàn đúng với KH đang gọi món 
* →  Giao diện nhập món được gọi hiện ra 
* →  NV hỏi KH và nhập vào tên món ăn + chọn tìm 
* →  kết quả hiện ra gồm danh sách các món ăn chi tiết: mã, loại, tên, giá. 
* →  NV chọn 1 món ăn đúng như KH gọi và NV click chọn 
* →  Yêu cầu nhập số lượng 
* →  NV nhập số lượng và click OK 
* →  Tên món ăn + số lượng + số tiền tạm tính được thêm vào danh sách các món ăn đã chọn phía dưới. 
        NV lặp lại các bước chọn món ăn này cho đến khi nhập vào được hết các món mà khách hàng trong bàn đã gọi. 
        NV đọc lại để xác nhận với KH 
* →  NV click xác nhận 
* →  hệ thống lưu lại.

## 2. Modul "Đặt bàn": 
* Nhân viên chọn chức năng đặt bàn khi khách hàng gọi đến  
* →  giao diện tìm bàn trống hiện ra 
* →  NV nhập ngày + giờ đặt + số lượng khách và bấm tìm 
* →  kết quả hiện ra gồm danh sách các bàn còn trống vào ngày giờ đấy: mã, tên, số lượng khách tối đa, mô tả 
* →  NV chọn 1 bàn theo yêu cầu của KH
* →  Giao diện nhập thông tin KH hiện ra 
* →  NV hỏi khách hàng và nhập mã, tên, số ĐT, email, địa chỉ và click tìm 
* →  Hệ thống hiện danh sách các khách hàng có cùng tên vừa nhập, mỗi khách hàng trên 1 dòng: mã, tên, số ĐT, email, địa chỉ 
* →  NV click vào dòng đúng với KH đnag đặt (nếu không có thì lick thêm KH mới) 
* →  Hệ thống hiện lên giao diện xác nhận có đầy đủ thông tin bàn + thông tin KH + ngày giờ đặt 
* →  NV xác nhận với KH và click xác nhận
* →  Hệ thống lưu thông tin vào CSDL.

## 3. Modul "Lên menu sẵn dạng combo" cho phép quản lí (QL) thực hiện thêm, sửa, xóa thông tin combo sẵn các món ăn: 
* QL chọn menu quản lí combo 
* →  trang quản lí hiện ra 
* →  QL chọn chức năng thêm combo 
* →  giao diện thêm combo hiện ra với các ô nhập tên combo và nút thêm món ăn vào combo 
* →  QL click thêm món ăn vào combo 
* →  giao diện tìm món ăn theo tên hiện ra 
* →  QL nhập tên món ăn và click tìm kiếm 
* →  danh sách các món ăn có tên chứa từ khóa hiện ra 
* →  QL chọn một món ăn 
* →  hệ thống quay về giao diện thêm combo với món ăn vừa chọn được thêm vào combo 
* →  QL lặp lại cho đến khi thêm xong các món ăn cần cho vào combo và sau đó QL click cập nhật 
* →  hệ thống lưu thông tin vào CSDL và thông báo thành công.

## 4. Modul "Thanh toán": 
* KH yêu cầu VN thanh toán 
* →  Nhân viên chọn chức năng thanh toán 
* →  giao diện chọn bàn hiện ra với danh sách bàn và số hiệu sổ xuống 
* →  NV chọn bàn đúng với bàn của KH 
* →  Giao diện hóa đơn chi tiết của bàn hiện ra như mô tả ở trên 
* →  NV hỏi KH có phiếu giảm giá không 
* →  nếu có thì click thêm phiếu giảm giá + nhập mã 
* →  giao diện hóa đơn thêm dòng phiếu giảm giá và cập nhật lại tổng tiền phải thanh toán 
* →  NV báo KH số tiền 
* →  Sau khi thanh toán, NV click xác nhận 
* →  hệ thống lưu lại và in hóa đơn chi tiết cho KH

## 5. Modul "Thống kê lượng khách theo khung giờ": 
* Quản lí chọn chức năng thống kê lượng khách theo khung giờ  
* →  giao diện chọn thời gian thống kê (ngày bắt đầu - kết thúc) hiện ra 
* →  quản lí chọn xong bấm thống kê 
* →  kết quả hiện ra gồm danh sách các khung giờ chi tiết: 
        khung giờ từ mấy giờ đến mấy giờ trong ngày, trung bình số lượng khách, 
            trung bình doanh thu/đầu khách, tổng doanh thu của khung giờ. 
        Sắp xếp theo tổng doanh thu, xếp từ cao đến thấp. 
        NV click vào một khung giờ, hệ thống hiện lên chi tiết các hóa đơn của khác đã dùng trong khong giờ đấy, 
            mỗi hóa đơn trên 1 dòng: mã, tên khách, ngày, tổng số món gọi, tổng số tiền thanh toán

## 6. Modul "Thống kê doanh thu theo tháng": 
* QL chọn menu thống kê 
* →  chọn thống kê doanh thu theo món ăn 
* →  nhập thời gian bắt đầu và kết thúc thống kê 
* →  danh sách các món ăn có doanh thu lớn nhất được hiện ra, mỗi dòng cho 1 món ăn: 
        Mã, tên, tổng số lượng khách đã dùng, tổng doanh thu thu được, sắp xếp theo chiều giảm dần tổng doanh thu. 
        NV click vào 1 dòng của 1 tháng, hệ thống hiện lên chi tiết các hóa đơn của khách trong tháng, 
            mỗi hóa đơn trên dòng: id, tên khách, ngày giờ, tổng số món gọi, tổng số tiền thanh toán.

## 7. Modul "Thống kê món ăn bán chạy": 
* Quản lí chọn chức năng thống kê món ăn bán chạy  
* →  giao diện chọn thời gian thống kê (ngày bắt đầu - kết thúc) hiện ra 
* →  quản lí chọn xong bấm thống kê 
* →  kết quả hiện ra gồm danh sách các món ăn chi tiết: mã, loại, tên, tổng số lượt bán, tổng doanh thu. 
        Sắp xếp theo tổng doanh thu, xếp từ cao đến thấp. 
        NV click vào 1 dòng của 1 món ăn, hệ thống hiện lên chi tiết danh sách các lần món ăn được gọi: 
            id, tên khách, ngày giờ, số lượng, thành tiền

# V. Phần mềm hỗ trợ quản lí kho vật tư
Khách hàng yêu cầu chúng ta phát triển một phần mềm **hỗ trợ quản lí kho vật tư**,:

* Mỗi hàng hóa (Mã hàng, tên, mô tả) có thể được nhập nhiều lần khác nhau, mỗi lần nhập có số lượng khác nhau và giá nhập khác nhau, đến từ một nhà cung cấp (mã NCC, tên NCC, địa chỉ, số ĐT) khác nhau
* Mỗi lần nhập hàng có thể nhập nhiều hàng hóa khác nhau
* Mỗi lần nhập có một phiếu nhập ghi thông tin nhà cung cấp, tiếp theo là danh sách các mặt hàng nhập vào, mỗi mặt hàng có đầy đủ thông tin: mã hàng, tên hàng, số lượng, đơn giá, thành tiền (tự động tính) và dòng cuối cùng là tổng tiền của hóa đơn nhập
* Tương tự, mỗi hàng hóa có thể xuất đi nhiều lần khác nhau, mỗi lần cho các đại lí con (mã ĐL, tên ĐL, địa chỉ, số ĐT) khác nhau, với số lượng khác nhau và giá xuất khác nhau
* Mỗi lần xuất có thể xuất nhiều hàng khác nhau, miễn sao số lượng xuất không vượt quá số lượng hàng còn trong kho
* Mỗi lần xuất có một phiếu xuất ghi thông tin đại lí con, tiếp theo là danh sách các mặt hàng xuất đi, mỗi mặt hàng có đầy đủ thông tin: mã hàng, tên hàng, số lượng, đơn giá, thành tiền (tự động tính) và dòng cuối cùng là tổng tiền của hóa đơn xuất

## 1. Modul "lập phiếu xuất hàng": 
* Nhân viên chọn menu xuất hàng 
* →  trang xuất hàng hiện ra với ô tìm kiếm đại lí con (ĐLC)
* →  NV nhập tên ĐL và click tìm
* →  hệ thống hiện lên danh sách các ĐL có tên chứa tên vừa nhập
* →  NV click chọn dòng của ĐL đúng với ĐL nhập (trường hợp ĐL mới thì phải thêm mới vào)
* →  hệ thống hiện lên giao diện tìm hàng xuất
* →  NV nhập tên hàng và click tìm
* →  hệ thống hiện lên danh sách các MH có tên chứa từ khóa vừa nhập
* →  nhân viên chọn tên hàng trong danh sách hàng hóa có sẵn + nhập số lượng + đơn giá
* →  MH xuất hiện vào danh sách MH xuất trong hóa đơn
* →  lặp đến khi hết các hàng cần xuất vào thì submit
* →  báo xuất thành công và in ra hóa đơn xuất như đã mô tả

## 2. Modul "Lập phiếu nhập hàng": 
* Nhân viên chọn menu nhập hàng 
* →  trang nhập hàng hiện ra với ô tìm NCC theo tên
* →  NV nhập tên + click tìm
* →  hệ thống hiện lên danh sách các NCC chứa tên vừa nhập vào
* →  NV click vào NCC đang nhập (nếu NCC mới thì thêm mới)
* →  Lặp các bước sau cho hết hàng nhập: NV click chọn tìm MH theo tên
* →  nhập tên + click tìm
* →  hệ thống hiện lên danh sách các MH chứa tên vừa nhập
* →  nhân viên chọn tên hàng trong danh sách hàng hóa có sẵn (nếu hàng mới thì chọn nhập mới) + nhập số lượng
* →  MH đó sẽ được thêm vào danh sách các MH nhập của hóa đơn
* →  lặp đến khi hết các hàng nhập vào thì submit
* →  báo nhập thành công và in ra hóa đơn nhập như đã mô tả

## 3.  Modul "Thống kê sản phẩm bán chạy": 
* Nhân viên chọn menu thống kê 
* →  chọn chức năng thống kê sản phẩm bán chạy
* →  nhập khoảng thời thời gian thống kê (bắt đầu - kết thúc)
* →  kết quả hiện ra danh sách các sản phẩm theo thứ tự bán được tổng số lượng nhiều nhất đến ít dần trong khoảng thời gian đã chọn, 
    mỗi dòng có các thông tin: mã hàng, tên hàng, số lượng đã bán được, tổng số tiền đã thu được từ sản phẩm ấy trong khoảng thời gian đã chọn. 
    NV click vào một dòng của 1 sản phẩm thì hiện lên thống kê chi tiết các hóa đơn của các đại lí con đã mua sản phẩm đấy

## 4.  Modul "Thống kê đại lí tiêu thụ mạnh": 
* Nhân viên chọn menu thống kê 
* →  chọn chức năng thống kê đại lí tiêu thụ hàng đầu
* →  nhập khoảng thời thời gian thống kê (bắt đầu - kết thúc)
* →  kết quả hiện ra danh sách các đại lí tiêu thụ theo thứ tự bán được tổng doanh thu nhiều nhất đến ít dần trong khoảng thời gian đã chọn, 
    mỗi dòng có các thông tin: mã đại lí, tên đại lí, tổng số tiền đã thu được từ đại lí ấy trong khoảng thời gian đã chọn. 
    NV click vào 1 dòng của đại lí thì hiện lên chi tiết danh sách các hóa đơn (ngày, tổng số hàng, tổng số tiền) của mỗi lần đại lí con đấy đã nhập hàng

# VI. Phần mềm quản lí Giải đấu vô địch thế giới
Liên đoàn cờ vua thế giới (FIDE) yêu cầu anh/chị phát triển một phần mềm **quản lí Giải đấu vô địch thế giới** với mô tả như sau:

* Mỗi giải đấu (Mã, tên, năm, lần tổ chức, địa điểm, mô tả) cho phép nhiều cờ thủ (mã, tên, năm sinh, quốc tịch, hệ số Elo, ghi chú) tham gia.
* Có thể có hàng trăm cờ thủ tham gia, nhưng mỗi cờ thủ phải thi đấu 11 trận theo hệ Thụy Sỹ
* Ở ván thứ nhất, các cờ thủ được xếp hạng theo thứ tự hệ số Elo từ cao đến thấp. Sau đó đi từ trên xuống dưới bảng sắp xếp, hai cờ thủ đứng kề nhau sẽ tạo thành một cặp đấu cho vòng 1.
* Ở mỗi vòng đấu, thắng được 1 điểm, hòa được 0.5 điểm, thua được 0 điểm. Sau mỗi vòng đấu, kết quả từng trận được cập nhật theo các cặp đấu đã lên lịch trước đó. Đồng thời hệ số Elo tăng hay giảm sau mỗi vòng đấu cũng được cập nhật (Tính theo công thức của FIDE, chỉ cần nhập kết quả vào).
* Bắt đầu từ ván thứ 2, bảng xếp hạng tạm thời sau vòng đấu trước đó được xếp theo thứ tự các tiêu chí: tổng điểm (giảm dần), tổng điểm của các đối thủ đã gặp (giảm dần), hệ số Elo (giảm dần). Và cặp đấu được xác định như sau, đi từ đầu đến cuối bảng xếp hạng tạm thời, với mỗi cờ thủ chưa có cặp, đối thủ cả cờ thủ đó là cờ thủ đầu tiên gặp phải và thỏa mãn: chưa có căp , và chưa gặp cờ thủ đang xem xét.
* Sau 11 vòng đấu như vậy, cờ thủ đứng đầu bảng xếp hạng sẽ là nhà vô địch.

## 1. Modul "Cập nhật kết quả": 
* Ban tổ chức (BTC) chọn menu cập nhật kết quả 
* →  trang cập nhật kết quả hiện ra
* →  BTC chọn vòng đấu từ danh sách sổ ra + chọn cặp đấu từ danh sách sổ ra theo vòng đấu + nhập số điểm và điểm Elo cho 2 cờ thủ của trận đấu + click Cập nhật
* →  Hệ thống thông báo lưu thành công kết quả trận đấu và quay về trang chọn vòng đấu + trận đấu

## 2. Modul "Xem bảng xếp hạng": 
* Ban tổ chức (BTC) chọn menu thống kê 
* →  chọn chức năng xem bảng xếp hạng sau từng vòng đấu
* →  chọn vòng đấu trong danh sách sổ ra
* →  kết quả hiện ra danh sách các cờ thủ, mỗi người có đầy đủ thông tin: id, tên, năm sinh, quốc tịch, tổng điểm, tổng điểm đối thủ đã gặp, hệ số Elo tức thời. Sắp xếp theo thứ tự đã mô tả ở trên

## 3. Modul "Xếp cặp thi đấu": 
* Ban tổ chức (BTC) chọn menu xếp cặp thi đấu 
* →  trang xếp cặp thi đấu hiện ra
* →  BTC chọn vòng đấu trước đó trong danh sách sổ xuống
* →  hệ thống hiện bảng xếp hạng hiện tại sau vòng đấu trước đó + nút Xếp lịch
* →  BTC click nút Xếp lịch
* →  Hệ thống  tự động xếp cặp cho các cờ thủ theo luật mô tả ở trên, và hiện danh sách các bàn đấu theo đúng thứ tự các cặp đấu
* →  BTC click Lưu
* →  Hệ thống lưu lịch thi đấu của vòng mới vào CSDL

## 4. Modul "Thống kê thay đổi Elo": 
* Ban tổ chức (BTC) chọn menu thống kê 
* →  chọn chức năng thống kê thay đổi Elo của các cờ thủ sau giải
* →  kết quả hiện ra danh sách các cờ thủ, mỗi cờ thủ được hiện đầy đủ thông tin: 
    mã, tên, năm sinh, quốc tịch, hệ số Elo cũ, hệ số Elo mới, hệ số Elo đã tăng/giảm. 
    Sắp xếp theo thứ tự giảm dần của mức tăng giảm hệ số Elo của các kì thù, tiếp đến là giảm dần của hệ số Elo mới, sau giải. 
    Click vào 1 dòng của một cờ thủ
* →  hệ thống hiện lên chi tiết các trận cờ thủ đấy đã đấu, mỗi trận trên 1 dòng: id, tên đối thủ, mức tăng giảm Elo.

# VII. Phần mềm quản lí kết quả giải đua
Ban tổ chức đưa xe công thức 1 (F1) đặt hàng anh/chị phát triển một phần mềm **quản lí kết quả giải đua** với mô tả như sau:

* Mỗi năm có một giải. Một giải bao gồm nhiều chặng đua diễn ra trên khắp thế giới (Mã chặng, tên, số vòng đua, địa điểm, thời gian, mô tả). 
* Mỗi giải có nhiều đội đua tham gia (Mã, tên, hãng, mô tả).
* Mỗi đội đua có nhiều tay đua (mã, tên, ngày sinh, quốc tịch, tiểu sử). Nhưng ở mỗi chặng đua, mỗi đội chỉ được phép cho tối đa 2 tay đua tham dự.
* Mỗi chặng đua, kết quả xếp theo thứ tự về đích (thời gian) và điểm số chỉ được tính cho top 10 người về đích sớm nhất, lần lượt theo các thứ tự về đích là 25, 18, 15, 12, 10, 8, 6, 4, 2, 1.
* Nếu tay đua nằm trong top 10 nhưng không về đích do bỏ cuộc hoặc tai nạn thì 0 điểm.
* Điểm số và thời gian của từng tay đua sẽ được cộng dồn giữa các chặng để quyết định giải cá nhân và giải đồng đội của mùa giải

## 1. Modul "Đăng kí thi đấu": 
* Ban tổ chức (BTC) chọn chức năng đăng kí tay đua
* →  giao diện đăng kí tay đua cho mỗi chặng đấu hiện ra
* →  BTC chọn chặng đua từ danh sách sổ xuống + chọn đội đua từ danh sách sổ xuống
* →  danh sách các tay đua của đội đua đã chọn hiện ra, xếp theo abc của họ tên
* →  BTC tích chọn đúng 2 tay đua theo yêu cầu của đội + click Đăng kí
* →  Hệ thống lưu thông tin và thông báo thành công.

## 2.  Modul "Cập nhật kết quả": 
* Ban tổ chức (BTC) chọn chức năng nhập kết quả chặng đua 
* →  giao diện nhập kết quả hiện ra
* →  BTC chọn tên chặng đua từ danh sách sổ xuống
* →  Danh sách các tay đua đã đăng kí thi đấu cho chặng đua hiện ra dưới dạng bảng, mỗi dòng chứa các ô trống nhập thời gian về đích, số vòng đua hoàn thành
* →  BTC nhập đầy đủ kết quả tất cả các tay đua và click Lưu
* →  Hệ thống  lưu kết quả vào CSDL và thông báo thành công

## 3.  Modul "Xem BXH các tay đua": 
* Ban tổ chức (BTC) chọn chức năng thống kê
* →  Chọn xem bảng xếp hạng các tay đua hiện tại
* →  Hệ thống hiện lên danh sách các tay đua theo dạng bảng, mỗi dòng chứa: 
    Tên tay đua, quốc tịch, tên đội đua, tổng điểm sau các chặng, tổng thời gian sau các chặng. 
    Kết quả sắp xếp theo thứ tự giảm dần của tổng điểm, sau đó là thứ tự tăng dần tổng thời gian. 
    NV click vào 1 dòng của 1 tay đua
* →  hệ thống hiện lên chi tiết kết quả từng chặng đưa của tay đua đó, mỗi chặng trên 1 dòng: 
    tên chặng, thứ hạng về đích, số điểm, thời gian về đích

## 4.  Modul "Xem BXH các đội đua": 
* Ban tổ chức (BTC) chọn chức năng thống kê
* →  Chọn xem bảng xếp hạng các đội đua hiện tại
* →  Hệ thống hiện lên danh sách các đội đua theo dạng bảng, mỗi dòng chứa: 
    Tên đội đua, hãng, tổng điểm các tay đua của đội sau các chặng, tổng thời gian sau các chặng. 
    Kết quả sắp xếp theo thứ tự giảm dần của tổng điểm, sau đó là thứ tự tăng dần tổng thời gian.  
    NV click vào 1 dòng của 1 đội đua
* →  hệ thống hiện lên kết qả chi tiết cho từng chặng của đội đua đó, mỗi chặng trên 1 dòng: 
    tên chặng, tổng số điểm, tổng thời gian của 2 tay đua trong đội

# VIII. phần mềm quản lí cho thuê truyện
Khách hàng yêu cầu anh/chị phát triển một phần mềm **quản lí cho thuê truyện ở một cửa hàng chuyên cho thuê truyện** với mô tả như sau:

* Cửa hàng có nhiều đầu truyện khác nhau. Mỗi đầu truyện có số lượng khác nhau và giá thuê khác nhau (giá thuê theo ngày).
* Mỗi đầu truyện có thể được mượn bởi nhiều khách hàng khác nhau. Mỗi khách hàng mỗi lần mượn được mượn nhiều đầu truyện khác nhau.
* Mỗi lần mượn, khách hàng được nhận một phiếu mượn. Trong đó, dòng đầu ghi tên khách hàng và ngày mượn. Thông tin mỗi đầu truyện mượn được ghi trên một dòng: tên, tác giả, nhà xuất bản, năm xuất bản, giá thuê. Dòng cuối cùng ghi số lượng đầu truyện mượn.
* Khi trả truyện, khách hàng được nhận hóa đơn trả. Trong đó, dòng đầu ghi tên khách hàng và ngày thanh toán. Thông tin mỗi đầu truyện trả được ghi trên một dòng: tên, tác giả, nhà xuất bản, năm xuất bản, ngày mượn, ngày trả, giá thuê, thành tiền. Nếu bị phạt thì có thêm cột số tiền phạt. Dòng cuối cùng ghi tổng số tiền thanh toán

## 1.  Modul "Cho thuê truyện": Sau khi chọn được các truyện để thuê mượn, khách hàng (KH) cầm đến quầy nhân viên (NV) thu ngân làm phiếu mượn. 
* NV nhập tên KH và tìm kiếm
* →  Hệ thống trả về danh sách các KH có tên vừa nhập
* →  NV click chọn tên KH trong danh sách (nếu KH mượn lần đầu thì nhập mới)
* →  Hệ thống hiện giao diện thêm truyện mượn vào phiếu: Với mỗi đầu truyện, NV click chọn tìm truyện theo tên
* →  nhập tên truyện + click tìm
* →  hệ thống hiện lên danh sách các đầu truyện có tên vừa nhập
* →  NV click chọn dòng đúng với quyển truyện do KH chọn thuê
* →  Hệ thống thêm 1 dòng tương ứng với đầu truyện đó vào phiếu thuê mượn như mô tả. 
    Khi hết các đầu truyện do KH chọn thuê, NV click tạo phiếu mượn
* →  Hệ thống lưu vào CSDL và hiển thị phiếu mượn lên màn hình
* →  NV click in ra
* →  Hệ thống in phiếu mượn ra cho KH.

## 2. Modul "Khách hàng trả truyện và thanh toán":
* Khi KH đem truyện đến trả, NV chọn menu tìm danh sách truyện mượn theo tên KH
* →  nhập tên KH+click tìm kiếm
* →  hệ thống hiển thị danh sách các KH có tên vừa nhập
* →  NV chọn tên KH đúng với thông tin KH hiện tại
* →  hệ thống hiện lên danh sách các đầu truyện mà KH đó đang mượn, mỗi đầu truyện trên một dòng 
    với đầy đủ thông tin về đầu truyện, ngày mượn, giá mượn, và số tiền thuê tính đến ngày đang trả, cột cuối cùng là ô tích chọn trả
* →  NV click vào nút chọn trả cho các đầu truyện mà KH đem trả (có thể không trả hết 1 lần), nhập tình trạng sách và tiền phạt 
nếu có, cuối cùng click nút thanh toán
* →  hệ thống hiện hóa đơn đầy đủ thông tin khách hàng + 1 bảng danh sách các đầu truyện trả như mô tả trên + dòng cuối là tổng số tiền trả
* →  NV click xác nhận
* →  hệ thống cập nhật vào CSDL

## 3.  Modul "Thống kê truyện được mượn nhiều": 
* QL chọn menu thống kê đầu truyện được mượn nhiều
* →  Nhập khoảng thời gian (ngày bắt đầu – kết thúc) thống kê
* →  Hệ thống hiển thị danh sách các đầu truyện được mượn nhiều theo dạng bảng, mỗi dòng tương ứng với một đầu truyện 
    với đầy đủ thông tin: mã, tên, tác giả, NXB, năm XB, cột tổng số lượt được mượn, cột tổng số tiền thu được. 
    Xếp theo thứ tự giảm dần của cột tổng số lượt mượn, tiếp theo là giảm dần của cột tổng số tiền thu được. 
    NV click vào 1 dòng của 1 truyện
* →  hệ thống hiện lên chi tiết hóa đơn có truyện đó đã mượn, mỗi hóa đơn trên 1 dòng: 
    id, tên khách mượn, ngày giờ mượn, ngày giờ trả, tổng số tiền.

## 4. Modul "Thống kê khách hàng mượn nhiều": 
* QL chọn menu thống kê khách hàng mượn nhiều
* →  Nhập khoảng thời gian (ngày bắt đầu – kết thúc) thống 
kê
* →  hệ thống hiển thị danh sách KH mượn nhiều theo dạng bảng, mỗi dòng tương ứng với một 
KH với đầy đủ thông tin: mã, tên, số CMT, số đt, địa chỉ, tiếp theo là cột tổng số lượt mượn, cột 
tổng số tiền đã trả. Xếp theo chiều giảm dần của tổng số lượt mượn, tiếp theo là chiều giảm dần của 
tổng số tiền trả. NV click vào 1 dòng của 1 khách hàng
* →  hệ thống hiện lên chi tiết các hóa đơn 
khách hàng đấy đã mượn, mỗi hóa đơn trên 1 dòng: ngày mượn, tổng số sách mượn, tổng số tiền 
thanh toán

## 5. Modul "Thống kê doanh thu": 
* QL chọn menu thống kê doanh thu theo thời gian (tháng, quý, năm)
* →  hệ thống hiện ô chọn thống kê theo tháng, quý, hoặc năm
* →  QL click chọn theo tháng
* →  hệ thống hiện lên thống kê doanh thu theo tháng dưới dạng bảng, mỗi dòng tương ứng với 1 tháng (tương ứng là quý, năm): tên tháng, tổng doanh thu. Sắp xếp theo chiều thời gian tháng (tương ứng là quý, năm) gần nhất đến tháng (tương ứng là quý, năm) cũ 
nhất. NV click vào 1 dòng
* →  hệ thống hiện lên chi tiết các hóa đơn trong khoảng thời gian của dòng đấy, mỗi hóa đơn trên 1 dòng: id, tên khách hàng, ngày mượn, tổng số truyện mượn, tổng số tiền của hóa đơn

# IX. Phần mềm quản lí phân công và chấm công nhân viên part time
Chuỗi nhà hàng đồ ăn nhanh Lotteria đặt hàng anh chị phát triển một phần mềm giúp họ **quản lí phân công và chấm công nhân viên làm thêm theo giờ** (parttime) tại chuỗi cửa hàng của họ với mô tả như sau:

* Chuỗi nhà hàng có nhiều nhà hàng. Mỗi nhà hàng có nhiều nhân viên làm theo giờ. Mỗi ngày làm việc có 2 ca, ca 1 từ 8-16h, ca 2 từ 16-24h. Mức tiền công theo giờ là giống nhau cho tất cả nhân viên làm theo giờ.
* Mỗi nhân viên, sau khi kí hợp đồng, được đăng kí những buổi nào rảnh để có thể đến làm việc. Số buổi có thể làm việc trong mỗi tuần mà mỗi nhân viên đăng kí phải đạt ngưỡng tối thiểu theo quy định. Thông tin này có thể thay đổi hàng tuần, trước khi lên lịch làm việc cho tuần tiếp theo.
* Quản lí sẽ dựa trên lịch đăng kí của từng nhân viên để lên lịch cho tuần tiếp theo. Đảm bảo mỗi ca có đủ N nhân viên làm việc. Nếu có ca nào đó mà số nhân viên đăng kí lớn hơn N, thì ưu tiên những nhân viên đang có số giờ làm ít hơn xếp trước. Lịch tuần tiếp theo sẽ được thông báo cho toàn bộ nhân viên để tiện chuẩn bị.
* Khi đến làm việc, nhân viên quét thẻ checkin giờ vào làm, khi về, nhân viên quét thẻ checkout để về. 
* Tiền lương nhân viên tính theo số giờ thực làm của nhân viên và được trả theo tuần. Ca nào nhân viên làm quá 8h thì mức tiền công cho phần thời gian đội thêm được tính thêm 20%. ca nào nhân viên đến muộn hoặc về sớm thì thời gian vắng mặt sẽ bị trừ tiền đội thêm 50%

## 1. Modul "Đăng kí ca làm tuần tới": 
* QL chọn chức năng đăng kí ca làm tuần tới cho NV
* →  Giao diện tìm NV hiện lên
* →  QL nhập tên NV hoặc một phần tên NV và click tìm
* →  Giao diện hiện lên danh sách các NV có tên chứa từ khóa vừa nhập
* →  Giao diện đăng kí ca làm tuần tới cho NV hiện lên, chứa thông tin NV và 1 bảng có 7 dòng tương ứng 7 ngày của tuần tới, mỗi dòng có 2 ô chọn tương ứng với ca 
* →  QL click vào các ô tương ứng với các ca mà NV đăng kí làm và click lưu
* →  Hệ thống lưu lại và báo thành công

## 2. Modul "Lên lịch làm việc tuần tới": 
* QL chọn chức năng lên lịch làm việc tuần tới cho nhân viên 1 nhà hàng
* →  Giao diện lên lịch hiện lên gồm một bảng có 7 dòng tương ứng 7 ngày của tuần tới, mỗi dòng có 2 cột tương ứng 2 ca của ngày.
    Mỗi cột chứa tên các NV đã chọn cho ca đó
* →  QL click chọn vào 1 ca
* →  Giao diện hiện lên danh sách các NV đã đăng kí làm việc cho ca đó và chưa được xếp làm cho ca đó, 
    mỗi NV trên 1 dòng: tên, số điện thoại, tổng giờ đã lên lịch cho tuần tới, sắp xếp theo chiều tăng dần của tổng giờ đã lên lịch cho tuần tới
* →  QL click chọn một số NV và click nút chọn
* →  Giao diện quay về trang lên lịch với thông tin các NV được chọn được thêm vào cột của ca tương ứng
* →  QL lặp lại các bước chọn trên cho đến hết số ca của tuần tới và click lưu
* →  Hệ thống lưu lại và thông báo thành công, đồng thời in lịch ra để QL phát cho từng NV

## 3. Modul "Checkin/Checkout": Checkin và checkout có thể do NV quét thẻ, hoặc do QL trực tiếp cập nhật trên máy tính: 
* QL chọn chức năng checkin (hoặc checkout)
* →  Giao diện nhập mã NV hiện lên
* →  QL nhập mã NV và click submit
* →  Hệ thống lưu và báo thời điểm checkin (checkout) của NV là thời điểm hiện tại

## 4. Modul "Tính công tuần này": 
* QL chọn chức năng tính tiền công cho NV trong tuần
* →  Giao diện tính công hiện lên với ô nhập khoảng thời gian tính công 
* →  QL nhập ngày bắt đầu, ngày kết thúc của tuần vừa rồi
* →  Giao diện hiện lên danh sách bảng tiền công cho tất cả các NV trong tuần đó, 
    mỗi NV trên 1 dòng, xếp theo thứ tự tên: mã, tên, số đt, tổng số giờ làm trong ca, tổng tiền trong ca, tổng số giờ thừa ca, tổng tiền thừa ca, tổng số giờ đi chậm về sớm, tổng số tiền bị phạt, tổng tiền thực nhận cuối cùng
* →  QL click chọn vào 1 dòng để xem chi tiết
* →  Giao diện hiện lên bảng thống kê chi tiết giờ làm của NV được chọn trong tuần đó, mỗi dòng tương ứng 1 ca làm việc, xếp theo thứ tự thời gian: thứ, ngày, ca, giờ checkin, giờ checkout, số giờ trong ca, số tiền trong ca, số giờ thừa ca, số tiền thừa ca, số giờ đi chậm về sớm, số tiền bị phạt, tổng tiền thực nhận của ca

## 5. Modul "Thống kê nhân viên làm nhiều": 
* QL chọn chức năng thống kê NV làm nhiều
* →  Giao diện thống kê hiện lên với ô nhập khoảng thời gian thống kê
* →  QL nhập ngày bắt đầu, ngày kết thúc của thời gian thống kê
* →  Giao diện hiện lên danh sách bảng thống kê cho tất cả các NV trong khoảng thời gian đó, mỗi NV trên 1 dòng, xếp theo thứ 
tự tổng số giờ làm giảm dần: mã, tên, số đt, tổng số giờ làm trong ca, tổng số giờ thừa ca, tổng số giờ đi chậm về sớm, tổng số giờ thực làm cuối cùng, tổng số tiền thực nhận cuối cùng
* →  QL click chọn vào 1 dòng để xem chi tiết
* →  Giao diện hiện lên bảng thống kê chi tiết giờ làm của NV được chọn trong khoảng thời gian đó, mỗi dòng tương ứng 1 ca làm việc, xếp theo thứ tự thời gian: thứ, ngày, ca, giờ checkin, giờ checkout, số giờ trong ca, số giờ thừa ca, số giờ đi chậm về sớm, tổng thời gian thực làm, tổng tiền thực nhận của ca.

## 6. Modul "Thống kê nhân viên đúng giờ": 
* QL chọn chức năng thống kê NV đúng giờ
* →  Giao diện thống kê hiện lên với ô nhập khoảng thời gian thống kê 
* →  QL nhập ngày bắt đầu, ngày kết thúc của thời gian thống kê
* →  Giao diện hiện lên danh sách bảng thống kê cho tất cả các NV trong khoảng thời gian đó, mỗi NV trên 1 dòng, xếp theo thứ tự 
tăng dần của tổng số giờ đi muộn về sớm: mã, tên, số đt, tổng số giờ thực làm, tổng tiền thực nhận, tổng số giờ đi chậm về sớm, tổng số tiền phạt 
* →  QL click chọn vào 1 dòng để xem chi tiết
* →  Giao diện hiện lên bảng thống kê chi tiết giờ làm của NV được chọn trong khoảng thời gian đó, mỗi dòng tương ứng 1 ca làm việc, xếp theo thứ tự thời gian: thứ, ngày, ca, giờ checkin, giờ checkout, số giờ thực làm, số tiền thực nhận, số giờ đi chậm về sớm, số tiền phạt

# X. Phần mềm quản lí chuỗi rạp chiếu phim
Khách hàng yêu cầu anh/chị phát triển một phần mềm **quản lí chuỗi rạp chiếu phim** với mô tả như sau:

* Hãng có một chuỗi rạp chiếu phim (Mã rạp, tên rạp, địa chỉ, giới thiệu).
* Mỗi rạp chiếu phim có nhiều phòng chiếu khác nhau (Mã phòng chiếu, số lượng ghế, đặc điểm phòng chiếu)
* Mỗi phim (Mã phim, tên phim, loại phim, năm sản xuất, mô tả) có thể được chiếu tại nhiều phòng chiếu khác nhau vào nhiều thời điểm khác nhau
* Mỗi phòng chiếu có thể chiếu nhiều phim khác nhau tại nhiều thời điểm khác nhau
* Mỗi một thời điểm nhất định, trong một phòng chiếu chỉ có duy nhất một phim được chiếu, và bán với một giá vé xác định.
* Cùng một phim, chiếu tại cùng 1 phòng chiếu nhưng nếu ở các khung giờ và ngày khác nhau có thể có giá vé khác nhau.
* Cùng một suất chiếu, ghế ngồi chỗ khác nhau có thể có giá vé khác nhau.
* Nhân viên chỉ bán vé cho khách hàng khi phòng chiếu tại giờ chiếu mà khách hàng yêu cầu vẫn còn đủ số lượng ghế trống cho khách hàng.
* Khi mua vé, khách hàng được xuất hóa đơn ghi rõ các vé đã mua. Mỗi vé trên một dòng: tên phim, phòng chiếu, giờ chiếu, số ghế, ưu đãi, giá tiền. Bên dưới là tổng tiền.
* Rạp chiếu có bán kèm các dịch vụ ăn uống nhẹ (như bỏng ngô, nước uống...). Khách hàng có thể mua kèm với vé xem phim (khi đó, hóa đơn sẽ bao gồm các dịch vụ này), hoặc mua riêng lẻ. Nếu mua riêng lẻ thì xuất hóa đơn riêng, mỗi dòng là một mặt hàng: mã, tên, đơn giá, số lượng, ưu đãi, thành tiền. Dưới cùng là tổng tiền.

## 1. Modul "Bán vé xem phim" cho phép nhân viên (NV) rạp thêm thông tin bán vé cho khách hàng: 
* NV chọn menu bán vé
* →  trang bán vé hiện ra
* →  NV chọn phòng chiếu 
hoặc tên phim trong danh sách sổ ra (theo yêu cầu của khách) + chọn khung giờ chiếu
* →  NV cho 
khách hàng chọn các ghế còn trống trong phòng chiếu
* →  in ra vé và hóa đơn cho khách hàng: Tên 
rạp, số hiệu phòng chiếu, ngày giờ chiếu, tên phim, số lượng vé, giá tiền cho mỗi vé+tổng số tiền 
của hóa đơn.

## 2.  Modul “Lên lịch chiếu”  cho phép quản lí (QL) thực hiện lên lịch chiếu cho phim (phòng chiếu):
*  QL chọn menu quản lí lịch chiếu
* →  chọn lên lịch chiếu mới
* →  giao diện lên lịch chiếu hiện ra
* →  QL chọn lên phim từ danh sách sổ xuống + chọn phòng chiếu từ danh sách sổ xuống + khung giờ chiếu và chọn giá vé từ danh sách sổ xuống + click thêm lịch chiếu (danh sách phòng chiếu hay khung giờ thay đổi theo số phòng còn trống của khung giờ hay khung giờ còn trống của phòng chiếu được chọn)
* →  Giao diện định giá vé hiện lên với giá vé mặc định cho tất cả các ghế của suất chiếu -> QL có thể chọn một số ghế vào một mức giá và có thể có nhiều mức giá khác nhau và xác nhận -> Hệ thống lưu vào CSDL và thông báo thêm thành công.

## 3. Modul "Bán vé dịch vụ ăn uống" cho phép nhân viên (NV) rạp thêm thông tin bán đồ ăn uống cho khách hàng: 
* NV chọn menu bán dịch vụ đi kèm
* →  trang bán hàng hiện ra
* →  NV lặp các bước sau cho đến khi hết các mặt hàng mà KH yêu cầu: nhập tên mặt hàng và click tìm kiếm
* →  giao diện danh sách các mặt hàng chứa từ khóa vừa nhập hiện ra
* →  NV click chọn một mặt hàng
* →  giao diện chọn kích cỡ, số lượng hiện ra
* →  NV chọn kích cỡ đồ ăn uống, nhập số lượng và click OK
* →  giao diện các mặt hàng đã chọn hện lên như hóa đơn chứa bẳng các mặt hàng, mỗi dòng chứa: mã, tên, kích cỡ, đơn giá, số lượng, thành tiền. Dòng cuối là tổng tiền.
* →  Hết mặt hàng, NV click chọn thanh toán. Hệ thống in hóa đơn ra cho KH

## 4.  Modul "Thống kê doanh thu" cho phép nhân viên (NV) rạp thống kê doanh thu bán vé theo phim (hoặc theo rạp): 
* NV chọn menu thống kê
* →  chọn thống kê doanh thu theo phim (hoặc theo rạp)
* →  nhập thời gian bắt đầu và kết thúc thống kê
* →  danh sách các phim (rạp) có hiện ra, mỗi dòng cho 1 phim: Mã, tên phim, tổng số lượng vé bán ra, tổng doanh thu thu được, được sắp xếp theo chiều giảm dần tổng doanh thu 
    -> NV click vào một dòng của phim (rạp) thì hiện lên chi tiết tổng số tiền thu được cho từng suất chiếu của phim, mỗi dòng tương ứng: suất chiếu, số lượng vé bán ra, tổng tiền thu được, được sắp xếp theo thứ tự thời gian của suất chiếu từ cũ đến mới
    -> NV click vào một suất chiếu thì hiện lên danh sách các hóa đơn đã bán cho suất chiếu đó, mỗi hóa đơn trên 1 dòng sắp sếp theo thời gian thanh toán: mã, tên KH nếu có, tổng số vé, tổng tiền của hóa đơn (chỉ tính những vé liên quan đến suất chiếu đó trong hóa đơn).

## 5.  Modul "Thống kê các mặt hàng bán kèm theo doanh thu" cho phép nhân viên (NV) rạp thống kê doanh thu bán các mặt hàng đi kèm theo doanh thu: 
* NV chọn menu thống kê
* →  chọn thống kê các mặt hàng bán kèm theo doanh thu
* →  nhập thời gian bắt đầu và kết thúc thống kê
* →  danh sách các mặt hàng bán kèm hiện ra, mỗi dòng cho 1 mặt hàng: Mã, tên, tổng số lượng bán ra, tổng doanh thu thu được, sắp xếp theo chiều giảm dần tổng doanh thu. NV click vào một dòng của một mặt hàng thì hiện lên chi tiết các lần bán mặt hàng đấy, mỗi dòng tương ứng các thông tin: ngày bán, đơn giá, số lượng, tổng tiền được sắp xếp theo thứ tự thời gian bán hàng từ cũ đến mới. Đối với mặt hàng được đổi điểm thì khi thống kê vẫn quy ra tiền như thông thường để thống kê

# XI. Phần mềm quản lí cho thuê sân bóng mini
Khách hàng yêu cầu anh/chị phát triển một phần mềm **quản lí cho thuê sân bóng mini** của một chủ sân bóng với mô tả như sau:

* Sân bóng có nhiều sân con mini cho thuê. Tùy yêu cầu khách hàng mà có thể ghép 2 hay 4 sân bé liền nhau thành 1 sân lớn cho thuê.
* Mỗi sân có thể cho nhiều khách hàng (KH) thuê tại nhiều khung giờ khác nhau. Mỗi khách hàng có thể thuê nhiều sân khác nhau.
* Khách hàng có thể thuê sân theo buổi trong tuần hoặc thuê theo tháng (vào một hoặc một số buổi cố định trong tuần, trong vòng mấy tháng cụ thể).
* Khi làm hợp đồng thuê sân, khách hàng nhận được phiếu thuê sân. Trong đó, dòng đầu ghi ngày làm hợp đồng, thông tin chủ sân, thông tin của khách hàng. Các dòng tiếp theo, mỗi dòng ghi một sân mini với đầy đủ thông tin về sân, giá thuê một buổi, khung giờ thuê trong tuần, ngày bắt đầu, ngày kết thúc đợt thuê, tổng tiền thuê dự kiến. Dòng cuối cùng ghi tỏng 
số tiền thuê sân dự kiến
* Khi đặt sân, khách hàng phải đặt cọc trước cho chủ sân ít nhất 10% tổng tiền thuê dự kiến. Và thông tin số tiền đặt cọc này cũng được ghi rõ trong phiếu đặt sân là đã thanh toán bao nhiêu tiền, vào ngày nào.
* Khi khách hàng đến đá bóng tại sân, chủ sân có thể phục vụ nước uống giải khát và đồ ăn nhẹ. Mỗi buổi khách hàng dùng các loại mặt hàng nào, mỗi loại bao nhiêu chai (gói), hết tổng tiền bao nhiêu đều được cập nhật vào hệ thống. Khách hàng sẽ thanh toán luôn khoản chi phí phát sinh này vào cuối đợt thuê sân.
* Khi thanh toán tiền thuê sân, khách hàng nhận được một hóa đơn ghi chi tiết thông tin thuê sân và chi phí thuê sân giống như phiếu đặt sân. Có thể có thêm một số buổi phát sinh hoặc phải đổi lịch theo yêu cầu khách hàng. Ngoài ra, phần dưới hóa đơn ghi rõ đồ ăn uống phát sinh theo từng buổi, mỗi buổi được liệt kê thành một bảng, trong đó mỗi dòng của bảng mô tả một mặt hàng: mã, tên, giá, số lượng dùng, thành tiền. Tổng số tiền từng buổi và tổng số tiền cho cả đợt đặt sân.
* Quản lí sân (QL) phải nhập các mặt hàng (MH) bán kèm từ nhiều nhà cung cấp (mã, tên, địa chỉ, email, điện thoại, mô tả) khác nhau. Mỗi lần nhập hàng có hóa đơn nhập ghi rõ thông tin nhà cung cấp và danh sách các mặt hàng, mỗi dòng: id, tên, đơn giá, số lượng, thành tiền. Dòng cuối là tổng tiền.

## 1. Modul "Đặt sân" : 
* Khách hàng (KH) đến yêu cầu đặt sân
* →  Nhân viên (NV) chọn chức năng đặt sân
* →  hệ thống hiện giao diện tìm sân trống theo khung giờ
* →  NV nhập khung giờ + chọn loại sân theo yêu cầu KH + click tìm
* →  hệ thống hiện lên danh sách sân còn trống theo khung giờ đã chọn
* →  NV click chọn 1 sân
* →  hệ thống hiện giao diện điền thông tin KH 
* →  NV nhập tên và tìm
* →  hệ thống hiện lên danh sách các KH có tên vừa nhập
* →  NV click chọn tên KH đúng với KH hiện tại (nếu KH lần đầu đến đặt sân thì phải thêm mới)
* →  hệ thống hiện giao diện nhập khoảng thời gian ngày bắt đầu, ngày kết thúc đợt đặt sân (ưu tiên đặt theo quý)
* →  NV click chọn và click xác nhận
* →  hệ thống hiện phiếu đặt sân với đầy đủ thông tin KH, thông tin sân đặt, giá sân đặt, khung giờ đặt, tổng số buổi theo thoài gian đã chọn, tổng số tiền ước tính và số tiền phải đặt cọc (10%)
* →  NV click xác nhận
* →  hệ thống in phiếu đặt sân và cập nhật vào CSDL.

## 2. Modul "Quản lí nhập hàng": 
* NV chọn menu nhập hàng 
* →  trang nhập hàng hiện ra với ô tìm NCC theo tên
* →  NV nhập tên + click tìm
* →  hệ thống hiện lên danh sách các NCC chứa tên vừa nhập vào
* →  NV click vào NCC đang nhập (nếu NCC mới thì thêm mới)
* →  Lặp các bước sau cho hết hàng nhập: NV click chọn tìm MH theo tên
* →  nhập tên + click tìm
* →  hệ thống hiện lên danh sách các MH chứa tên vừa nhập
* →  nhân viên chọn tên hàng trong danh sách hàng hóa có sẵn (nếu hàng mới thì chọn thêm mới) + nhập đơn giá và số lượng
* →  MH đó sẽ được thêm vào danh sách các MH nhập của hóa đơn
* →  lặp đến khi hết các hàng nhập vào thì submit
* →  báo nhập thành công và in ra hóa đơn nhập như đã mô tả

## 3.  Modul "Cập nhật các mặt hàng đã dùng của buổi thuê": 
* Khi KH đến nhận sân đá xong và trả sân của buổi đó, NV chọn menu tìm phiếu đặt sân theo tên KH
* →  nhập tên KH, click tìm kiếm
* →  hệ thống hiển thị danh sách các KH có tên vừa nhập
* →  NV chọn tên KH đúng với thông tin KH hiện tại
* →  hệ thống hiện lên danh sách các phiếu đặt mà KH đó đang đặt
* →  NV click vào nút chọn checkout buổi thuê 1 phiếu đặt sân
* →  hệ thống hiện giao diện nhập giờ nhận sân, giờ trả sân, tiền thuê sân (trả sớm thì không được giảm tiền, nhưng trả muộn thì bị tính thêm tiền) + lặp các bước sau cho đến khi hết danh sách các sản phẩm ăn uống mà KH đã sử dụng trong suốt các buổi thuê sân: click thêm mặt hàng dùng
* →  giao diện tìm MH theo tên hiện ra
* →  NV nhập tên MH và tìm
* →  giao diện danh sách các MH có tên chứ từ khóa vừa nhập hiện lên
* →  NV click chọn 1 MH
* →  giao diện nhập đơn giá và số lượng hiện ra
* →  NV nhập và xác nhận
* →  thông tin MH sử dụng được thêm vào danh sách các MH đã dùng của buổi + dòng cuối là tổng số tiền các MH
* →  NV click xác nhận
* →  hệ thống cập nhật vào CSDL (chưa cần thanh toán)

## 4. Modul "Khách hàng thanh toán": 
* Khi KH đến yêu cầu thanh toán, NV chọn menu tìm phiếu đặt sân theo tên KH
* →  nhập tên KH+click tìm kiếm
* →  hệ thống hiển thị danh sách các KH có tên vừa nhập
* →  NV chọn tên KH đúng với thông tin KH hiện tại
* →  hệ thống hiện lên danh sách các phiếu đặt mà KH đó đang đặt
* →  NV click vào nút chọn thanh toán cho 1 phiếu đặt sân
* →  hệ thống hiện hóa đơn đầy đủ thông tin khách hàng + 1 bảng danh sách các sản phẩm ăn uống mà KH đã sử dụng trong suốt các buổi thuê sân như mô tả trên + dòng cuối là tổng số tiền trả 
    (nếu KH khiếu nại thay đổi số lượng hay thông tin mặt hàng sử dụng thì NV phải thay đổi, cập nhật lại dnah sách chi tiết trong hóa đơn tương ứng)
* →  NV click xác nhận
* →  hệ thống cập nhật vào CSDL

## 5. Modul "Thống kê doanh thu": 
* QL chọn menu thống kê doanh thu theo thời gian (tháng, quý, năm)
* →  hệ thống hiện ô chọn thống kê theo tháng, quý, hoặc năm
* →  QL click chọn theo tháng
* →  hệ thống hiện lên thống kê doanh thu trong 12 tháng gần nhất dưới dạng bảng, mỗi dòng tương ứng với 1 tháng (tương ứng là quý, năm): tên tháng, tổng doanh thu, được sắp xếp theo chiều thời gian tháng (tương ứng là quý, năm) gần nhất đến tháng (tương ứng là quý, năm) cũ nhất. QL click vào 1 dòng của kết quả
* →  hệ thống hiện lên chi tiết các hóa đơn của khách hàng trong thờ gian của dòng click, mỗi hóa đơn trên 1 dòng: id, tên khách hàng, tên sân, ngày giờ, tổng tiền thanh toán

## 6. Modul "Thống kê khung giờ được thuê nhiều": 
* QL chọn menu thống kê khung giờ được thuê nhiều
* →  Nhập khoảng thời gian (ngày bắt đầu – kết thúc) thống kê
* →  Hệ thống hiển thị danh sách các khung giờ được thuê nhiều theo dạng bảng, mỗi dòng tương ứng với một khung giờ 
    với đầy đủ thông tin: khung giờ, ngày, cột tổng số lượt được thuê, cột tổng số tiền thu được, 
    được sắp xếp theo thứ tự giảm dần của cột tổng số lượt thuê, 
    tiếp theo là giảm dần của cột tổng số tiền thu được. 
    QL click vào 1 dòng của 1 khung giờ
* →  hệ thống hiện lên chi tiết danh sách các lần có khách đặt sân trong khung giờ đó, mỗi lần trên một dòng: id, tên khách, tên sân, ngày giờ, giá, tổng tiền

# XII. Phần mềm quản lí khách hàng vay trả góp
Hãng cho vay trả góp Saison đặt hàng anh chị phát triển một phần mềm giúp họ **quản lí khách hàng vay trả góp** tại chuỗi cửa hàng của họ với mô tả như sau:

* Hãng hợp tác với nhiều đối tác - ĐT, là các công ty bán lẻ các mặt hàng - MH với nhiều chủng loại từ điện thoại, máy tính, đồ điện tử, điện lạnh, gia dụng, ô tô, bất động sản...
* Khi khách hàng - KH mua một hay một số MH của ĐT mà có nhu cầu sử dụng dịch vụ trả góp, nhân viên sẽ làm thủ tục kí hợp đồng - HĐ vay trả góp cho KH đó. HĐ chứa thông tin địa diện công ty, thông tin KH, thông tin ĐT, ngày kí, và danh sách các mặt hàng, mỗi mặt hàng trên 1 dòng: mã, tên, đơn vị tính, đơn giá, số lượng, thành tiền. Dòng cuối là tổng tiền và thời hạn vay. Tiếp theo là danh sách các thời điểm thanh toán, mỗi đợt trên 1 dòng: ngày phải thanh toán, tổng tiền thanh toán, tổng dư nợ còn lại.
* Mỗi MH có giá niêm yết của ĐT riêng, công ty thanh toán cho ĐT sẽ được chiết khấu giảm giá mức 1-5%, công ty thu lại của khách hàng theo lãi suất 1-20%/năm dựa trên giá niêm yết của MH.
* KH có thể thanh toán tiền trả góp cho mỗi HĐ mỗi tháng một lần, trong thời gian tùy chọn của hợp đồng.
* KH có thể thanh toán trước hạn từng tháng nhưng giá trị thanh toán không đổi (không được giảm lãi)
* Nếu KH thanh toán muộn so với thời hạn hàng tháng, thì khoản dư nợ trễ hạn được hình vào nợ gốc và tính lãi theo nợ gốc.
* Công ty có thể thanh toán tiền MH cho ĐT theo từng MH hoặc theo từng đợt trong khoảng thời gian 1 tuần, 1 tháng... Mỗi lần thanh toán đều lưu hóa đơn đầy đủ thông tin người đại diện công ty, đại diện đối tác, ngày thanh toán, tổng tiền thanh toán và danh sách các MH được thanh toán, mỗi MH của một KH trên 1 dòng: mã, tên MH, tên KH, ngày mua, đơn vị tính, số lượng, đơn giá, thành tiền.

## 1. Modul “Kí hợp đồng”: 
* QL chọn menu thống NV chọn chức năng kí HĐ mới với KH
* →  Giao diện tìm KH hiện lên
* →  NV nhập tên KH hoặc một phần tên KH và click tìm
* →  Giao diện hiện lên danh sách các KH có tên chứa từ khóa vừa nhập -> NV chọn đúng KH 
    (nếu không có thì snag giao diện nhập thông tin KH mới để nhập rồi tiếp tục)
* →  Giao diện tìm ĐT hiện lên
* →  NV nhập tên ĐT hoặc một phần tên ĐT và click tìm
* →  Giao diện hiện lên danh sách các ĐT có tên chứa từ khóa vừa nhập 
    -> Chọn đúng ĐT 
    -> Lặp lại các bước sau cho hết các MH do KH mua: Giao diện tìm MH hiện lên 
* →  NV nhập tên MH hoặc một phần tên MH và click tìm
* →  Giao diện hiện lên danh sách các H có tên chứa từ khóa vừa nhập -> Chọn đúng MH và nhập số lượng, đơn giá -> Sau khi xong hết các mặt hàng, NV chọn tiếp tục -> Giao diện nhập thời hạn vay và lãi suất vay -> Hệ thống tự động tính ra các thời điểm phải thanh toán hàng tháng và số tiền thanh toán dưới dạng bảng, mỗi dòng tương ứng: thời điểm phải thanh toán, tổng tiền phải thanh toán, dư nợ còn lại
* →  NV xác nhận lại với KH và click lưu
* →  Hệ thống lưu lại và báo thành công, in HĐ ra cho KH.

## 2. Modul “Cho khách thanh toán theo hạn”: 
* NV chọn chức năng nhận thanh toán từ KH (KH có thể thanh toán trực tiếp tại quầy, chuyển khoản hoặc online - đây là mô tả cho 
thanh toán trực tiếp) 
* →  Hiện giao diện tìm thông tin HĐ 
    -> NV nhập mã HĐ 
    -> Hiện thông tin chi tiết HĐ, lịch sử các lần đã thanh toán, tổng dư nợ còn lại và số tiền phải thanh toán 
    -> NV báo KH số tiền phải thanh toán và tổng dư nợ, hỏi KH muốn thanh toán cho mấy đợt hoặc tổng tiền bao nhiêu 
    (KH có thể thanh toán trước các đợt sau, hoặc thanh toán chưa đủ cho đợt này)
* →  NV chọn các mốc thanh toán KH muốn thanh toán, nhập số tiền
* →  GD kiện hóa đơn thanh toán chứa thông tin KH, đại diện công ty, danh sách các MH như trong HĐ gốc, tổng tiền thanh toán, tổng dư nợ còn lại, và danh sách các đợt thanh toán còn lại 
    -> NV xác nhận với KH và click lưu 
    -> Hệ thống lưu lại và thông báo thành công, đồng thời in hóa đơn ra để NV giao cho KH

## 3.  Modul “Thanh toán cho đối tác”: 
* NV chọn chức năng thanh toán cho ĐT
* →  Giao diện tìm ĐT hiện lên
* →  NV nhập tên ĐT hoặc một phần tên ĐT và click tìm
* →  Giao diện hiện lên danh sách các ĐT có tên chứa từ khóa vừa nhập -> Chọn đúng ĐT
* →  Giao diện hiện lên danh sách các Hợp đồng của KH mua hàng của ĐT đó mà công ty chưa thanh toán hết cho ĐT hiện lên, mỗi hợp đồng trên 1 dòng: id, tên KH, tổng mặt hàng, tổng tiền của KH, số tiền phải thanh toán cho ĐT 
    -> NV tích chọn một số hợp đồng để thanh toán cho ĐT và click next 
    -> Hiện giao diện hóa đơn thanh toán đối tác với đầy đủ thông tin như mô tả ở trên 
    -> NV xác nhận với ĐT và click lưu 
* →  Hệ thống lưu và in hóa đơn cho ĐT kí để NV lưu

## 4.  Modul “Thống kê khách hàng theo dư nợ”: 
* QL chọn chức năng thống kê KH theo dư nợ
* →  Giao diện hiện lên danh sách bảng thống kê cho tất cả các KH,  mỗi KH trên 1 dòng, xếp theo thứ tự tổng dư nợ giảm dần: mã, tên, số đt, tổng dư nợ còn, tổng dư nợ quá hạn
* →  QL click chọn vào 1 dòng để xem chi tiết
* →  Giao diện hiện lên bảng danh sách các HĐ của KH đó, mỗi dòng tương ứng 1 hợp đồng, xếp theo thứ tự thời gian: mã, ngày kí, tổng tiền vay, tổng số lần trả, tổng dư nợ, tổng dư nợ quá hạn 
    -> click vào 1 dòng 
    -> hiện lên chi tiết hợp đồng tương ứng: thông tin KH, ĐT, danh sách các mặt hàng, số lượng, đơn giá, tổng tiền; danh sách các đợt thanh toán, trạng thái đã hoàn thành thanh toán hay chưa

## 5.  Modul “Thống kê đối tác theo doanh số”: 
* QL chọn chức năng thống kê ĐT theo doanh số
* →  Giao diện thống kê hiện lên với ô nhập khoảng thời gian thống kê
* →  QL nhập 
ngày bắt đầu, ngày kết thúc của thời gian thống kê
* →  Giao diện hiện lên danh sách các ĐT,  mỗi 
ĐT trên 1 dòng, xếp theo thứ tự tổng doanh thu giảm dần: mã, tên, địa chỉ/chi nhánh, tổng số hóa 
đơn có, tổng doanh thu, tổng dư nợ chưa trả
* →  QL click chọn vào 1 dòng để xem chi tiết
* →  Giao 
diện hiện lên bảng danh sách các HĐ liên quan ĐT đó, mỗi dòng tương ứng 1 hợp đồng, xếp theo 
thứ tự thời gian: mã, tên KH, ngày kí, tổng tiền vay, tổng số lần trả, tổng dư nợ, tổng dư nợ quá hạn -> click vào 1 dòng -> hiện lên chi tiết hợp đồng tương ứng: thông tin KH, ĐT, danh sách các mặt 
hàng, số lượng, đơn giá, tổng tiền; danh sách các đợt thanh toán, trạng thái đã hoàn thành thanh toán 
hay chưa.

## 6. Modul “Thống kê dòng mặt hàng theo doanh thu”: 
* QL chọn chức năng thống kê dòng mặt hàng theo doanh thu
* →  Giao diện thống kê hiện lên với ô nhập khoảng thời gian thống kê
* →  QL nhập ngày bắt đầu, ngày kết thúc của thời gian thống kê
* →  Giao diện hiện lên danh sách bảng thống kê cho tất cả các dòng/thể loại MH trong khoảng thời gian đó, mỗi dòng MH trên 1 
dòng, xếp theo thứ tự giảm dần của tổng doanh thu từ lãi suất: dòng MH, tổng số hóa đơn, tổng doanh thu lãi (chỉ tính phần lãi suất thu được)
* →  QL click chọn vào 1 dòng để xem chi tiết
* →  Giao diện hiện lên bảng thống kê chi tiết các Mh của dòng MH được chọn trong khoảng thời gian đó, mỗi dòng tương ứng 1 MH, xếp theo thứ tự tổng doanh thu lãi giảm dần: mã, tên MH, tổng hóa đơn, tổng doanh thu lãi 
    -> Click vào 1 dòng, hiện lên danh sách các hợp đồng của MH đấy trong khoảng thời gian thống kê, sắp xếp theo thứ tự thời gian: mã, tên KH, tổng giá trị vay, tổng tiền lãi thu được 
    -> click vào 1 dòng 
    -> hiện lên chi tiết hợp đồng tương ứng: thông tin KH, ĐT, danh sách các mặt hàng, số lượng, đơn giá, tổng tiền; danh sách các đợt thanh toán, trạng thái đã hoàn thành thanh toán hay chưa

# XIII. Phần mềm quản lí hoạt động cho thuê trang phục
Cửa hàng cho thuê trang phục dạ hội, biểu diễn đặt hàng anh chị phát triển một phần mềm giúp họ quản lí hoạt động cho thuê trang phục của họ với mô tả như sau:

* Cửa hàng có nhiều trang phục -TP, thuộc nhiều chủng loại khác nhau, một TP có thể có số lượng khác nhau.
* TP được đặt hàng hoặc nhập sẵn từ các nhà cung cấp - NCC. Mỗi NCC có thể cung cấp nhiều loại TP khác nhau. Mỗi lần nhập có thể nhập nhiều loại TP từ cùng NCC, mỗi TP có số lượng khác nhau.
* Khách hàng - KH có thể thuê nhiều lần, mỗi lần thuê nhiều TP khác nhau, mỗi TP có số lượng khác nhau. Nếu thuê lần đầu thì phải đặt cọc bằng tổng giá trị gốc của các TP thuê, nếu thuê nhiều lần (khách quen) thì tiền cọc do NV làm hóa đơn quyết định.
* Khi trả, KH có thể trả một phần hoặc trả hết các TP đang thuê trong một lần, mỗi lần trả đều có phiếu trả tương ứng với các TP trả. Tiền cọc chỉ được trả lại cho KH khi đã trả hết các TP thuê. Trường hợp KH trả một phần TP, sau khi trả xong mà tiền cọc còn lại nhiều hơn giá trị gốc các TP thuê thì KH được nhận lại phần dư ra, chỉ giữ lại cọc tối đa bằng giá trị gốc các TP đang thuê.
* Khi trả, nếu TP bị lỗi hỏng hóc, vấy bẩn thì KH phải trả tiền phạt. Một TP có thể dính nhiều lỗi đồng thời. Tiền phạt cho mỗi lỗi được ước tính bởi NV thanh toán trả đồ.

## 1. Modul "Nhập trang phục": 
* NV chọn chức năng nhập TP từ một NCC 
* →  Giao diện tìm NCC theo tên hiện lên 
    -> NV nhập tên NCC và tìm 
    -> Hiện danh sách các NCC chứa tên vừa nhập 
    -> Click chọn NCC đúng 
    (nếu không có trong danh sách kết quả thì chuyển sang giao diện nhập thông tin NCC mới và tiếp tục)
* →  Lặp cho đến khi hết các TP cần mua từ NCC đấy: 
    chọn tìm TP theo tên 
    -> chọn và nhập số lượng, đơn giá
* →  NV xác nhận hóa đơn nhập với NCC và thanh toán cho NCC, nhận hàng
* →  Hệ thống lưu lại và thông báo thành công, đồng thời in hóa đơn ra đề nghị NCC kí để lưu

## 2. Modul "Cho thuê trang phục": Sau khi chọn được các trang phục để thuê mượn, khách hàng (KH) cầm đến quầy nhân viên (NV) thu ngân làm phiếu mượn. 
* NV nhập tên KH và tìm kiếm
* →  Hệ thống trả về danh sách các KH có tên vừa nhập
* →  NV click chọn tên KH trong danh sách (nếu KH mượn lần đầu thì nhập mới)
* →  Hệ thống hiện giao diện thêm trang phục mượn vào phiếu: Với mỗi trang phục, NV click chọn tìm trang phục theo tên
* →  nhập tên trang phục + click tìm
* →  hệ thống hiện lên danh sách các trang phục có tên vừa nhập
* →  NV click chọn dòng đúng với trang phục do KH chọn thuê + nhập số lượng
* →  Hệ thống thêm 1 dòng tương ứng với trang phục đó vào phiếu thuê mượn như mô tả. 
    Tổng tiền đặt cọc bằng tổng tiền giá gốc của các trang phục và tự động tính vào cuối hóa đơn. 
    Khi hết các trang phục do KH chọn thuê, NV click tạo phiếu mượn
* →  Hệ thống lưu vào CSDL và hiển thị phiếu mượn lên màn hình
* →  NV click in ra
* →  Hệ thống in phiếu mượn ra cho KH và nhận tiền cọc

## 3.  Modul "Khách hàng trả đồ và thanh toán": 
* Khi KH đem trang phục đến trả, NV chọn menu tìm danh sách trang phục mượn theo tên KH
* →  nhập tên KH+click tìm kiếm
* →  hệ thống hiển thị danh sách các KH có tên vừa nhập
* →  NV chọn tên KH đúng với thông tin KH hiện tại
* →  hệ thống hiện lên danh sách các trang phục mà KH đó đang mượn, mỗi trang phục trên một dòng với đầy đủ thông tin về trang phục, ngày mượn, giá mượn theo ngày, số ngày đã mượn, và số tiền thuê tính đến ngày đang trả, cột cuối cùng là ô tích chọn trả
* →  NV click vào nút chọn trả cho các trang phục mà KH đem trả (có thể không trả hết 1 lần), nhập tình trạng trang phục và tiền phạt nếu có, cuối cùng click nút thanh toán
* →  hệ thống hiện hóa đơn đầy đủ thông tin khách hàng + 1 bảng danh sách các trang phục trả như mô tả trên + dòng cuối là tổng số tiền trả , số tiền đã đặt cọc, số tiền khách phải trả hoặc trả lại khách
* →  NV click xác nhận
* →  hệ thống cập nhật vào CSDL

## 4. Modul "Thống kê trang phục được mượn nhiều":
* QL chọn menu thống kê trang phục được mượn nhiều
* →  Nhập khoảng thời gian (ngày bắt đầu – kết thúc) thống kê 
* →  Hệ thống hiển thị danh sách các trang phục được mượn nhiều theo dạng bảng, mỗi dòng tương ứng với một trang phục 
    với đầy đủ thông tin: mã, tên, kiểu, thể loại, cột tổng số lượt được mượn, cột tổng số tiền thu được. 
    Xếp theo thứ tự giảm dần của cột tổng số lượt mượn, tiếp theo là giảm dần của cột tổng số tiền thu được. 
    QL click vào 1 dòng của 1 trang phục
* →  hệ thống hiện lên chi tiết hóa đơn có trang phục đó đã mượn, mỗi hóa đơn trên 1 dòng: 
    id, tên khách mượn, ngày giờ mượn, ngày giờ trả, tổng số tiền

## 5. Modul "Thống kê doanh thu": 
* QL chọn menu thống kê doanh thu theo thời gian (tháng, quý, năm) 
* →  hệ thống hiện ô chọn thống kê theo tháng, quý, hoặc năm
* →  QL click chọn theo tháng
* →  hệ thống hiện lên thống kê doanh thu theo tháng dưới dạng bảng, mỗi dòng tương ứng với 1 tháng (tương ứng là quý, năm): tên tháng, tổng doanh thu. Sắp xếp theo chiều thời gian tháng (tương ứng là quý, năm) gần nhất đến tháng (tương ứng là quý, năm) cũ nhất. QL click vào 1 dòng
* →  hệ thống hiện lên chi tiết các hóa đơn trong khoảng thời gian của dòng đấy, mỗi hóa đơn trên 1 dòng: 
    id, tên khách hàng, ngày mượn, tổng số trang phục mượn, tổng số tiền của hóa đơn
