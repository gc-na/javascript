<!--
Meta Description: # HTMLBRElement: Hiểu Biết Về Phần Tử HTML <br> Trong JavaScript ## Tóm tắt HTMLBRElement là một phần tử trong DOM (Document Object Model) đại diện ch...
Meta Keywords: phần, thẻ, trong, tạo, cách
-->

# HTMLBRElement: Hiểu Biết Về Phần Tử HTML <br> Trong JavaScript

## Tóm tắt
HTMLBRElement là một phần tử trong DOM (Document Object Model) đại diện cho thẻ `<br>`, được sử dụng để tạo khoảng cách dòng trong văn bản. Trong JavaScript, bạn có thể tương tác với phần tử này để thay đổi nội dung và cấu trúc của trang web.

## Tài liệu
### Mục đích
HTMLBRElement cho phép lập trình viên kiểm soát cách hiển thị văn bản trong trình duyệt. Thẻ `<br>` thường được dùng để tạo dòng mới mà không cần bắt đầu một đoạn văn mới.

### Cách sử dụng
Trong JavaScript, bạn có thể tạo và thao tác với phần tử HTMLBRElement bằng cách sử dụng phương thức `document.createElement()` và các thuộc tính như `innerHTML` hoặc `appendChild()`.

### Chi tiết
- **Tạo phần tử**: Bạn có thể tạo một thẻ `<br>` mới bằng cách gọi `document.createElement('br')`.
- **Thêm vào DOM**: Sử dụng `appendChild()` để thêm thẻ `<br>` vào một phần tử khác trong trang.
- **Xóa phần tử**: Để xóa thẻ `<br>`, bạn có thể sử dụng phương thức `remove()`.

## Ví dụ
### Tạo và thêm thẻ `<br>` vào trang
```javascript
// Tạo một thẻ <br>
let brElement = document.createElement('br');

// Thêm nó vào một phần tử có id là 'content'
document.getElementById('content').appendChild(brElement);
```

### Xóa thẻ `<br>`
```javascript
// Tìm thẻ <br> đầu tiên trong phần tử 'content' và xóa nó
let brToRemove = document.querySelector('#content br');
if (brToRemove) {
    brToRemove.remove();
}
```

## Giải thích
- **Điểm cần lưu ý**: Mặc dù thẻ `<br>` rất hữu ích để tạo khoảng cách dòng, việc lạm dụng nó có thể dẫn đến mã HTML không rõ ràng và khó bảo trì. Tốt hơn là sử dụng CSS để kiểm soát khoảng cách giữa các phần tử.
- **Thao tác DOM**: Khi thao tác với phần tử DOM, hãy chắc chắn rằng bạn thực hiện các thay đổi trên các phần tử đã được tải hoàn toàn để tránh lỗi không tìm thấy phần tử.
  
## Tóm tắt một dòng
HTMLBRElement là phần tử đại diện cho thẻ `<br>` trong JavaScript, cho phép bạn tạo và quản lý khoảng cách dòng trong văn bản.