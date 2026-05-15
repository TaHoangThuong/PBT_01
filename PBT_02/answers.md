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
      <legend>Thông tin cá nhân</legend>
      <label for="fullname">Họ tên:</label>
      <input type="text" id="fullname">
      <label for="email">Email:</label>
      <input type="email" id="email">
      <label for="phone">SĐT:</label>
      <input type="tel" id="phone">
  </fieldset>
  
