<!--
Meta Description: # HTMLTableCaptionElement: Đối tượng trong JavaScript cho phần chú thích của bảng HTML ## Tóm tắt `HTMLTableCaptionElement` là một đối tượng đại diện ...
Meta Keywords: caption, bảng, của, một, phần
-->

# HTMLTableCaptionElement: Đối tượng trong JavaScript cho phần chú thích của bảng HTML

## Tóm tắt
`HTMLTableCaptionElement` là một đối tượng đại diện cho phần chú thích (caption) của bảng trong HTML, cho phép lập trình viên JavaScript dễ dàng truy cập và thao tác với thông tin này.

## Tài liệu
`HTMLTableCaptionElement` là một phần của Document Object Model (DOM) trong JavaScript, cho phép bạn tương tác với các phần tử HTML trên trang web. Đối tượng này được sử dụng để đại diện cho thẻ `<caption>` trong bảng, giúp cung cấp thông tin mô tả về nội dung của bảng.

### Cách sử dụng
Khi bạn tạo một bảng trong HTML, bạn có thể thêm một thẻ `<caption>` để mô tả nội dung của bảng. Đối tượng `HTMLTableCaptionElement` cho phép bạn truy cập và thay đổi nội dung của thẻ này thông qua JavaScript.

#### Ví dụ cơ bản
```html
<table id="myTable">
  <caption>Danh sách sinh viên</caption>
  <tr>
    <th>Tên</th>
    <th>Tuổi</th>
  </tr>
  <tr>
    <td>Nguyễn Văn A</td>
    <td>20</td>
  </tr>
  <tr>
    <td>Trần Thị B</td>
    <td>22</td>
  </tr>
</table>

<script>
  // Lấy phần tử caption
  const caption = document.querySelector('#myTable caption');
  
  // Thay đổi nội dung của caption
  caption.textContent = 'Cập nhật Danh sách sinh viên';
</script>
```

## Giải thích
Khi làm việc với `HTMLTableCaptionElement`, có một số điều cần lưu ý:

- **Truy cập đúng phần tử**: Đảm bảo rằng bạn đang truy cập đúng phần tử `<caption>` thông qua phương thức như `document.querySelector()`.
- **Chỉ có một caption trong bảng**: Mỗi bảng HTML chỉ có thể có một thẻ `<caption>`. Nếu bạn cố gắng thêm nhiều hơn một thẻ caption, chỉ thẻ đầu tiên sẽ được hiển thị.
- **Tương thích trình duyệt**: `HTMLTableCaptionElement` được hỗ trợ bởi hầu hết các trình duyệt hiện đại, nhưng luôn kiểm tra tính tương thích nếu dự án của bạn cần hỗ trợ các trình duyệt cũ.

## Tóm tắt một câu
`HTMLTableCaptionElement` là đối tượng JavaScript cho phép truy cập và thao tác với phần chú thích của bảng HTML, giúp cải thiện trải nghiệm người dùng và cung cấp thông tin rõ ràng về nội dung bảng.