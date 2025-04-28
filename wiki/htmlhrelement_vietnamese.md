<!--
Meta Description: # HTMLHRElement trong JavaScript: Cách Sử Dụng và Tính Năng ## Tóm tắt HTMLHRElement là một đối tượng trong JavaScript đại diện cho thẻ `<hr>` trong H...
Meta Keywords: dụng, một, tính, thẻ, các
-->

# HTMLHRElement trong JavaScript: Cách Sử Dụng và Tính Năng

## Tóm tắt
HTMLHRElement là một đối tượng trong JavaScript đại diện cho thẻ `<hr>` trong HTML, thường được sử dụng để tạo ra một đường kẻ ngang phân cách nội dung trên trang web.

## Tài liệu
### Mục đích
HTMLHRElement cho phép lập trình viên tương tác với các yếu tố `<hr>` trong tài liệu HTML thông qua JavaScript. Điều này có thể hữu ích khi bạn cần thay đổi kiểu dáng, thêm các thuộc tính, hoặc xóa đường kẻ khi người dùng thực hiện một hành động nhất định.

### Cách sử dụng
Để sử dụng HTMLHRElement trong JavaScript, bạn có thể truy cập các đối tượng này thông qua DOM (Document Object Model). Bạn có thể tạo, sửa đổi hoặc xóa các thẻ `<hr>` bằng cách sử dụng các phương thức và thuộc tính của đối tượng này.

### Chi tiết
- **Tạo đối tượng HR**: Bạn có thể tạo một đối tượng HR mới bằng cách sử dụng `document.createElement('hr')`.
- **Thay đổi thuộc tính**: Bạn có thể thay đổi các thuộc tính như `size`, `width`, `color`, và nhiều thuộc tính CSS khác để điều chỉnh hiển thị của đường kẻ.
- **Thêm vào DOM**: Để thêm đường kẻ vào trang, bạn có thể sử dụng `appendChild()` hoặc `insertBefore()`.

## Ví dụ
### 1. Tạo và thêm một HR mới
```javascript
// Tạo một thẻ HR mới
const hr = document.createElement('hr');

// Thay đổi các thuộc tính
hr.style.width = '50%';
hr.style.color = 'blue';

// Thêm thẻ HR vào body
document.body.appendChild(hr);
```

### 2. Thay đổi thuộc tính của HR hiện có
```javascript
// Lấy thẻ HR đầu tiên trong tài liệu
const hr = document.querySelector('hr');

// Thay đổi màu sắc
hr.style.color = 'red';
```

### 3. Xóa một HR
```javascript
// Lấy thẻ HR đầu tiên trong tài liệu
const hr = document.querySelector('hr');

// Xóa thẻ HR
hr.remove();
```

## Giải thích
- **Cảnh giác với sự tương thích**: Một số thuộc tính CSS có thể không được hỗ trợ trên tất cả các trình duyệt. Hãy kiểm tra sự tương thích trước khi sử dụng.
- **Sử dụng đúng phương thức**: Khi thêm thẻ HR vào DOM, đảm bảo rằng bạn đang sử dụng phương thức đúng như `appendChild()` để tránh lỗi.
- **Chú ý đến khả năng truy cập**: Đường kẻ ngang có thể không đủ để truyền đạt thông tin cho người dùng sử dụng công nghệ hỗ trợ. Hãy đảm bảo rằng nội dung được phân chia rõ ràng và dễ hiểu.

## Tóm tắt một dòng
HTMLHRElement trong JavaScript cho phép lập trình viên tạo và thao tác với các thẻ `<hr>` để phân chia nội dung trên trang web một cách hiệu quả.