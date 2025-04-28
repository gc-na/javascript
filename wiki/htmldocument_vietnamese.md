<!--
Meta Description: # HTMLDocument trong JavaScript: Khám Phá và Sử Dụng Hiệu Quả ## Tóm tắt HTMLDocument là một đối tượng trong JavaScript đại diện cho tài liệu HTML hiệ...
Meta Keywords: phần, với, của, document, htmldocument
-->

# HTMLDocument trong JavaScript: Khám Phá và Sử Dụng Hiệu Quả

## Tóm tắt
HTMLDocument là một đối tượng trong JavaScript đại diện cho tài liệu HTML hiện tại. Đối tượng này cho phép lập trình viên tương tác và thao tác với nội dung của trang web.

## Tài liệu
HTMLDocument là một phần của DOM (Document Object Model) và cho phép bạn truy cập và thao tác với các phần tử HTML của trang. Đối tượng này cung cấp nhiều phương thức và thuộc tính hữu ích để tương tác với nội dung, như `getElementById`, `getElementsByClassName`, và `querySelector`.

### Mục đích
HTMLDocument được sử dụng để:
- Truy cập các phần tử HTML.
- Thay đổi nội dung và thuộc tính của phần tử.
- Thêm hoặc xóa các phần tử trong tài liệu.

### Cách sử dụng
Để sử dụng HTMLDocument, bạn có thể truy cập nó thông qua đối tượng `document`. Dưới đây là một số phương thức và thuộc tính phổ biến của đối tượng này:

- `document.getElementById(id)`: Trả về phần tử đầu tiên có id tương ứng.
- `document.getElementsByClassName(className)`: Trả về danh sách tất cả các phần tử có class tương ứng.
- `document.querySelector(selector)`: Trả về phần tử đầu tiên phù hợp với bộ chọn CSS được cung cấp.
- `document.querySelectorAll(selector)`: Trả về danh sách tất cả các phần tử phù hợp với bộ chọn CSS.

## Ví dụ
Dưới đây là một số ví dụ cơ bản về cách sử dụng HTMLDocument trong JavaScript:

### Ví dụ 1: Truy cập phần tử bằng ID
```javascript
let element = document.getElementById('myElement');
element.innerText = 'Nội dung mới';
```

### Ví dụ 2: Thay đổi màu nền của tất cả phần tử có class
```javascript
let elements = document.getElementsByClassName('myClass');
for (let i = 0; i < elements.length; i++) {
    elements[i].style.backgroundColor = 'blue';
}
```

### Ví dụ 3: Sử dụng querySelector
```javascript
let firstParagraph = document.querySelector('p');
firstParagraph.style.color = 'red';
```

## Giải thích
Khi làm việc với HTMLDocument, có một số điểm cần lưu ý:
- Đảm bảo rằng JavaScript của bạn chỉ chạy sau khi tài liệu HTML đã được tải hoàn toàn. Bạn có thể sử dụng sự kiện `DOMContentLoaded` để đảm bảo điều này.
- Khi thay đổi nội dung của phần tử, hãy cẩn thận với việc ghi đè nội dung hiện có, vì điều này có thể dẫn đến mất dữ liệu.
- Sử dụng `querySelector` và `querySelectorAll` cho phép bạn truy cập các phần tử một cách linh hoạt hơn, nhưng có thể chậm hơn so với các phương thức như `getElementById` hoặc `getElementsByClassName`.

## Tóm tắt một dòng
HTMLDocument trong JavaScript cho phép lập trình viên tương tác và thao tác với cấu trúc và nội dung của tài liệu HTML một cách linh hoạt và hiệu quả.