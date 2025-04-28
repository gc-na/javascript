<!--
Meta Description: # Fetch trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt Fetch là một API trong JavaScript cho phép thực hiện các truy vấn mạng (network reque...
Meta Keywords: một, error, fetch, các, response
-->

# Fetch trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
Fetch là một API trong JavaScript cho phép thực hiện các truy vấn mạng (network requests) tới các tài nguyên từ xa, hỗ trợ việc lấy dữ liệu từ máy chủ một cách đơn giản và hiệu quả.

## Tài liệu
Fetch API được giới thiệu trong ECMAScript 6 (ES6) và cung cấp một cách dễ dàng để thực hiện các yêu cầu HTTP. Nó thay thế XMLHttpRequest, mang lại một cú pháp dễ sử dụng hơn và hỗ trợ Promise, giúp xử lý bất đồng bộ một cách tự nhiên hơn.

### Mục đích
Fetch được sử dụng để thực hiện các yêu cầu HTTP, cho phép bạn lấy dữ liệu từ các API, tải tệp, hoặc gửi dữ liệu đến máy chủ.

### Cách sử dụng
Cú pháp cơ bản của Fetch là:

```javascript
fetch(url, options)
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json(); // hoặc response.text() tùy thuộc vào loại dữ liệu
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('There was a problem with the fetch operation:', error);
  });
```

- **url**: Địa chỉ của tài nguyên mà bạn muốn lấy.
- **options**: Một đối tượng tùy chọn cho phép bạn cấu hình các thông số như phương thức HTTP (GET, POST, PUT, DELETE), tiêu đề (headers), và dữ liệu (body).

## Ví dụ
### Lấy dữ liệu từ một API
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

### Gửi dữ liệu đến một API
```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ name: 'John', age: 30 })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

## Giải thích
### Những cạm bẫy phổ biến
- **CORS (Cross-Origin Resource Sharing)**: Khi bạn cố gắng gửi yêu cầu đến một miền khác, bạn có thể gặp phải các vấn đề với CORS. Đảm bảo rằng máy chủ mà bạn đang yêu cầu cho phép các yêu cầu từ miền của bạn.
- **Xử lý lỗi**: Không phải tất cả các yêu cầu đều thành công. Hãy luôn kiểm tra `response.ok` để đảm bảo rằng yêu cầu đã được thực hiện thành công.
- **Thời gian chờ**: Fetch không có cơ chế thời gian chờ tự động. Nếu bạn cần thiết lập thời gian chờ, bạn sẽ cần phải xây dựng một giải pháp riêng.

## Tóm tắt một dòng
Fetch trong JavaScript là một API mạnh mẽ cho phép thực hiện các yêu cầu mạng một cách dễ dàng và hiệu quả.