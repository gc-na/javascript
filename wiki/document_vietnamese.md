<!--
Meta Description: # Tài liệu về Đối tượng "document" trong JavaScript ## Tóm tắt Đối tượng `document` trong JavaScript là một phần quan trọng của API DOM (Document Obje...
Meta Keywords: phần, document, của, tài, liệu
-->

# Tài liệu về Đối tượng "document" trong JavaScript

## Tóm tắt
Đối tượng `document` trong JavaScript là một phần quan trọng của API DOM (Document Object Model), cho phép lập trình viên truy cập và thao tác với cấu trúc HTML của trang web. Nó là điểm khởi đầu để làm việc với nội dung và cấu trúc của tài liệu.

## Tài liệu
Đối tượng `document` đại diện cho toàn bộ tài liệu HTML của trang web. Nó cung cấp nhiều phương thức và thuộc tính để truy cập, thay đổi, và thao tác với các phần tử trong tài liệu. 

### Mục đích
Mục đích chính của đối tượng `document` là cung cấp một cách để lập trình viên có thể tương tác với nội dung của trang web, từ việc lấy thông tin của các phần tử, đến việc thay đổi nội dung và cấu trúc của các phần tử đó.

### Cách sử dụng
Đối tượng `document` thường được sử dụng trong các tình huống sau:
- Lấy các phần tử bằng cách sử dụng `getElementById`, `getElementsByClassName`, hoặc `querySelector`.
- Thay đổi nội dung của các phần tử bằng thuộc tính `innerHTML`, `textContent`, hoặc `value`.
- Tạo mới các phần tử HTML và thêm chúng vào tài liệu với `createElement` và `appendChild`.

### Chi tiết
- **`document.getElementById(id)`**: Trả về phần tử đầu tiên có thuộc tính id tương ứng.
- **`document.getElementsByClassName(className)`**: Trả về danh sách các phần tử có thuộc tính class tương ứng.
- **`document.querySelector(selector)`**: Trả về phần tử đầu tiên khớp với bộ chọn CSS.
- **`document.createElement(tagName)`**: Tạo một phần tử mới với tên thẻ được chỉ định.
- **`document.body`**: Trả về phần tử `<body>` của tài liệu.

## Ví dụ
### Lấy phần tử theo ID
```javascript
let element = document.getElementById('myElement');
console.log(element);
```

### Thay đổi nội dung của phần tử
```javascript
let element = document.getElementById('myElement');
element.innerHTML = 'Nội dung mới';
```

### Tạo và thêm phần tử mới
```javascript
let newElement = document.createElement('div');
newElement.innerHTML = 'Phần tử mới';
document.body.appendChild(newElement);
```

## Giải thích
Một số vấn đề thường gặp khi làm việc với đối tượng `document` bao gồm:
- **Lỗi khi tìm phần tử**: Đảm bảo rằng phần tử tồn tại trong DOM trước khi truy cập. Nếu không, sẽ nhận được giá trị `null`.
- **Thay đổi DOM trong quá trình tải trang**: Nếu bạn cố gắng thay đổi nội dung của tài liệu trước khi nó được tải hoàn toàn, bạn có thể gặp phải vấn đề không tìm thấy phần tử.
- **Chọn phần tử không chính xác**: Sử dụng đúng bộ chọn CSS khi sử dụng `querySelector` để đảm bảo bạn đang chọn đúng phần tử.

## Tóm tắt một dòng
Đối tượng `document` trong JavaScript cho phép lập trình viên truy cập và thao tác với nội dung và cấu trúc của tài liệu HTML trên trang web.