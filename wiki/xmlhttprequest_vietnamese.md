<!--
Meta Description: # XMLHttpRequest trong JavaScript: Gửi và Nhận Dữ Liệu Từ Server ## Tóm tắt `XMLHttpRequest` là một đối tượng trong JavaScript cho phép người dùng gửi...
Meta Keywords: xhr, yêu, cầu, xmlhttprequest, gửi
-->

# XMLHttpRequest trong JavaScript: Gửi và Nhận Dữ Liệu Từ Server

## Tóm tắt
`XMLHttpRequest` là một đối tượng trong JavaScript cho phép người dùng gửi và nhận dữ liệu từ máy chủ mà không cần tải lại trang, giúp cải thiện trải nghiệm người dùng trong các ứng dụng web.

## Tài liệu
### Mục đích
`XMLHttpRequest` được sử dụng để tương tác với các dịch vụ web bằng cách gửi yêu cầu HTTP và nhận phản hồi từ máy chủ. Nó hỗ trợ cả yêu cầu đồng bộ và không đồng bộ, cho phép thực hiện các thao tác trên dữ liệu mà không làm gián đoạn trải nghiệm người dùng.

### Cách sử dụng
Để sử dụng `XMLHttpRequest`, bạn cần tạo một thể hiện của đối tượng này và sử dụng các phương thức của nó để gửi yêu cầu. Cách tiếp cận cơ bản là:

1. Tạo một thể hiện của `XMLHttpRequest`.
2. Thiết lập yêu cầu với phương thức HTTP (GET, POST, v.v.) và URL.
3. Định nghĩa một hàm xử lý sự kiện cho phản hồi.
4. Gửi yêu cầu.

### Cú pháp
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onload = function () {
    if (xhr.status >= 200 && xhr.status < 300) {
        console.log(xhr.responseText);
    } else {
        console.error('Request failed with status: ' + xhr.status);
    }
};
xhr.onerror = function () {
    console.error('Request failed');
};
xhr.send();
```

## Ví dụ
### Ví dụ 1: Gửi yêu cầu GET
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onload = function () {
    console.log(xhr.responseText);
};
xhr.send();
```

### Ví dụ 2: Gửi yêu cầu POST
```javascript
var xhr = new XMLHttpRequest();
xhr.open('POST', 'https://api.example.com/data', true);
xhr.setRequestHeader('Content-Type', 'application/json;charset=UTF-8');
xhr.onload = function () {
    console.log(xhr.responseText);
};
xhr.send(JSON.stringify({ key: 'value' }));
```

## Giải thích
- **Cảnh giác với trạng thái yêu cầu**: Đảm bảo kiểm tra `xhr.status` để xác định xem yêu cầu có thành công hay không. Các mã trạng thái HTTP từ 200 đến 299 được coi là thành công.
- **Sự kiện onload**: Được gọi khi yêu cầu hoàn tất thành công. Nếu có lỗi xảy ra, bạn nên xử lý trong `onerror`.
- **Yêu cầu đồng bộ**: Sử dụng yêu cầu đồng bộ (đặt tham số thứ ba của `open` thành `false`) không được khuyến nghị, vì nó có thể làm treo giao diện người dùng.

## Tóm tắt một dòng
`XMLHttpRequest` là một đối tượng trong JavaScript cho phép gửi và nhận dữ liệu từ máy chủ mà không làm tải lại trang, cải thiện trải nghiệm người dùng trong các ứng dụng web.