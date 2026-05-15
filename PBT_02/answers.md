### Câu A1
1. type="email": Ô nhập văn bản, tự động kiểm tra có @ và định dạng email, sử dụng biểu mẫu đăng ký/đăng nhập
2. type="password": Ô nhập văn bản, ẩn ký tự nhập vào, dùng cho biểu mẫu đăng nhập, đặt lại mật khẩu
3. type="tel": Nhập văn bản, hiển thị bàn phím số trên thiết bị di động, sử dụng cho số điện thoại liên hệ
4. type="number": Ô nhập số, có nút tăng/giảm, dùng cho số lượng sản phẩm, giá tiền
5. type="date": Hiển thị bộ chọn ngày, dùng cho ngày sinh, ngày đặt hàng, ngày giao hàng
6. type="color": Hiển thị bộ chọn màu, sử dụng tùy chọn màu sắc sản phẩm
7. type="range": Thanh trượt, dùng cho bộ lọc giá, mức độ hài lòng
8. type="file": Nút chọn file, dùng để upload ảnh đại diện, tài liệu đính kèm
9. type="url": Nhập văn bản, tự động kiểm tra http:// hoặc https:// , dùng cho liên kết trang web, mạng xã hội
10. type="search": Ô tìm kiếm có nút X để xóa, dùng cho ô tìm kiếm sản phẩm

### Câu A2
Trường hợp 1: `<input type="text" required value="">` user để trống → THẤT BẠI vì bắt buộc nhưng giá trị trống.
Trường hợp 2: `<input type="email" value="abc">` người dùng nhập "abc" → THẤT BẠI vì "abc" không hợp lệ email (thiếu @ và tên miền).
Trường hợp 3: `<input type="number" min="1" max="10" value="15">` người dùng nhập 15 → THẤT BẠI vì giá trị 15 > max (10).
Trường hợp 4: `<input type="text" pattern="[0-9]{10}" value="abc123">` người dùng nhập "abc123" → THẤT BẠI vì mẫu yêu cầu 10 chữ số, nhưng "abc123" có chữ cái.
Trường hợp 5: `<input type="password" minlength="8" value="123">` người dùng nhập "123" → THẤT BẠI vì chỉ có 3 ký tự, nhỏ hơn độ dài tối thiểu (8).

### Câu A3
1. Tại sao `<label for="email">` quan trọng cho trình đọc màn hình người dùng?
- Khi người dùng sử dụng trình đọc màn hình (NVDA, VoiceOver), hãy chọn ô nhập để biết mục đích sử dụng để làm gì. Không có nhãn, trình đọc màn hình chỉ đọc "trường văn bản" mà không biết đó là email hay mật khẩu. Thuộc tính fornhãn kết nối với id đầu vào tương ứng.
2. Khi nào dùng `<fieldset>` + `<legend>`? Cho ví dụ cụ thể.
  - Sử dụng khi có các nhóm đầu vào liên kết với nhau. Ví dụ:
    ```
    <fieldset>
      <legend>Phương thức thanh toán</legend>
      <input type="radio" id="cod" name="payment"><label for="cod">COD</label>
      <input type="radio" id="bank" name="payment"><label for="bank">Chuyển khoản</label>
    </fieldset>
3. Thuộc tính `aria-label` dùng để cung cấp một nhãn văn bản ẩn cho các phần tử không có chữ hiển thị trên màn hình (ví dụ một nút bấm chỉ có icon cái kính lúp). KHÔNG nên dùng `aria-label` chung với thẻ `<label>` vì chúng sẽ gây xung đột cấu trúc cây Accessibility Tree, Screen Reader có thể bỏ qua thẻ `<label>` hiển thị thông thường và đọc đè nội dung `aria-label`, gây rối rắm hoặc mất thông tin trực quan của người dùng phổ thông.
### Câu A4
1. Thuộc tính `loading="lazy"` giúp trì hoãn việc tải hình ảnh cho đến khi người dùng cuộn trang tới gần vị trí của tấm ảnh đó. Nó giúp cải thiện đáng kể tốc độ tải trang ban đầu (TTI), tiết kiệm băng thông cho người dùng. KHÔNG dùng thuộc tính này cho các ảnh nằm ở phần nới đầu trang (Above-the-fold) như Banner chính, Logo vì nó sẽ làm chậm thời gian hiển thị nội dung lớn nhất (LCP).
2. Nên cung cấp nhiều thẻ `<source>` vì mỗi trình duyệt (Chrome, Safari, Firefox) hỗ trợ các bộ giải mã mã hóa (Codec) video khác nhau. Việc cung cấp nhiều source giúp đảm bảo video chạy được trên mọi thiết bị. Ba định dạng video web phổ biến là: `MP4 (H.264)`, `WebM`, và `Ogg`.
3. Thuộc tính `alt` (Alternative text) dùng để mô tả bằng chữ nội dung của bức ảnh trong trường hợp ảnh bị lỗi không tải được hoặc phục vụ cho Screen Reader đọc.
- Ảnh iPhone 16: `alt="Điện thoại iPhone 16 màu hồng bản 128GB mặt trước và mặt sau"`
- Ảnh trang trí: `alt=""` (để rỗng để Screen Reader chủ động bỏ qua)
- Ảnh biểu đồ Q1/2026: `alt="Biểu đồ cột thể hiện doanh thu Quý 1 năm 2026 tăng trưởng 15% so với cùng kỳ năm ngoái"`

### Câu A5
- Cách 1 (`<img>` đứng độc lập): Dùng khi hình ảnh mang tính chất minh họa bổ trợ, nội dung văn bản xung quanh không phụ thuộc hoàn toàn vào nó, hoặc ảnh dạng icon, banner quảng cáo đơn giản.
  + Ví dụ 1: Logo công ty nằm ở thanh điều hướng Header.
  + Ví dụ 2: Icon mạng xã hội Facebook dưới chân trang Footer.
- Cách 2 (`<figure>` + `<figcaption>`): Dùng khi hình ảnh là một khối nội dung độc lập, quan trọng, cần đi kèm ghi chú, chú thích rõ ràng bên dưới (như biểu đồ, ảnh tư liệu báo chí, ảnh chi tiết sản phẩm). Khối này có thể di chuyển đi vị trí khác trong bài mà không làm mất ý nghĩa luồng đọc.
  + Ví dụ 1: Ảnh chụp chi tiết cụm camera của điện thoại trong một bài viết đánh giá công nghệ.
  + Ví dụ 2: Sơ đồ luồng đi của hệ thống thanh toán trong tài liệu hướng dẫn sử dụng.
