<!--
Meta Description: # HTMLInputElement: Đối Tượng Quan Trọng Trong JavaScript ## Tóm tắt HTMLInputElement là một đối tượng trong JavaScript đại diện cho phần tử `<input>`...
Meta Keywords: liệu, nhập, trường, các, checkbox
-->

# HTMLInputElement: Đối Tượng Quan Trọng Trong JavaScript

## Tóm tắt
HTMLInputElement là một đối tượng trong JavaScript đại diện cho phần tử `<input>` trong HTML, cho phép lập trình viên tương tác và quản lý các trường nhập liệu trên trang web.

## Tài liệu
HTMLInputElement là một interface trong DOM (Document Object Model) đại diện cho các phần tử `<input>` trong tài liệu HTML. Đối tượng này cung cấp nhiều thuộc tính và phương thức để thao tác với các trường nhập liệu như text, checkbox, radio, và nhiều loại khác nữa. Việc sử dụng HTMLInputElement giúp lập trình viên có thể dễ dàng kiểm soát giá trị, kiểu dữ liệu và các trạng thái của các phần tử nhập liệu trên giao diện người dùng.

### Mục đích
Mục đích chính của HTMLInputElement là cung cấp một cách tiếp cận dễ dàng để quản lý và tương tác với các trường nhập liệu trong một trang web.

### Cách sử dụng
Để sử dụng HTMLInputElement, trước tiên bạn cần chọn phần tử `<input>` từ DOM. Có thể sử dụng các phương thức như `document.getElementById`, `document.querySelector`, hoặc `document.getElementsByClassName`. Sau khi đã chọn được phần tử, bạn có thể truy cập và thay đổi các thuộc tính của nó.

### Các thuộc tính chính
- `value`: Trả về hoặc đặt giá trị của trường nhập liệu.
- `type`: Xác định loại trường nhập liệu (ví dụ: text, password, checkbox).
- `checked`: Chỉ áp dụng cho checkbox và radio, cho phép kiểm tra xem phần tử có được chọn hay không.
- `disabled`: Cho phép vô hiệu hóa trường nhập liệu.
- `placeholder`: Văn bản hiển thị khi trường nhập liệu trống.

## Ví dụ
### Ví dụ 1: Lấy giá trị từ trường nhập liệu
```javascript
const inputField = document.getElementById('myInput');
console.log(inputField.value); // In ra giá trị của trường nhập liệu
```

### Ví dụ 2: Thay đổi giá trị của trường nhập liệu
```javascript
const inputField = document.getElementById('myInput');
inputField.value = 'Giá trị mới'; // Đặt giá trị mới cho trường nhập liệu
```

### Ví dụ 3: Kiểm tra xem checkbox có được chọn hay không
```javascript
const checkbox = document.getElementById('myCheckbox');
if (checkbox.checked) {
    console.log('Checkbox đã được chọn');
} else {
    console.log('Checkbox chưa được chọn');
}
```

## Giải thích
Khi làm việc với HTMLInputElement, một số vấn đề thường gặp bao gồm:
- Không lấy được giá trị đúng từ trường nhập liệu do không sử dụng đúng ID hoặc selector.
- Quên kiểm tra trạng thái của checkbox hoặc radio, dẫn đến lỗi logic trong mã.
- Không đặt thuộc tính `disabled` dẫn đến việc người dùng có thể nhập liệu khi không mong muốn.

## Tóm tắt một câu
HTMLInputElement là một đối tượng quan trọng trong JavaScript giúp quản lý và tương tác với các trường nhập liệu trên trang web.