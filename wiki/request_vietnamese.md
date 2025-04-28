<!--
Meta Description: # Yêu cầu (Request) trong JavaScript: Hướng dẫn đầy đủ ## Tóm tắt Trong JavaScript, "Request" thường đề cập đến việc gửi và nhận dữ liệu từ một máy ch...
Meta Keywords: xhr, api, error, yêu, cầu
-->

# Yêu cầu (Request) trong JavaScript: Hướng dẫn đầy đủ

## Tóm tắt
Trong JavaScript, "Request" thường đề cập đến việc gửi và nhận dữ liệu từ một máy chủ sử dụng API, đặc biệt là khi làm việc với Fetch API hoặc XMLHttpRequest. Bài viết này sẽ cung cấp cái nhìn tổng quan và hướng dẫn chi tiết về cách thực hiện yêu cầu HTTP trong JavaScript.

## Tài liệu
### Mục đích
"Request" trong JavaScript chủ yếu được sử dụng để giao tiếp với các API web. Việc gửi yêu cầu HTTP cho phép bạn lấy dữ liệu từ máy chủ hoặc gửi dữ liệu đến máy chủ.

### Cách sử dụng
Có nhiều cách để thực hiện yêu cầu HTTP trong JavaScript, nhưng hai phương pháp phổ biến nhất là Fetch API và XMLHttpRequest.

#### Fetch API
Fetch API là một giao diện JavaScript hiện đại hơn giúp bạn thực hiện yêu cầu HTTP một cách đơn giản và dễ đọc.

Cú pháp cơ bản:
```javascript
fetch(url, options)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

- **url**: Địa chỉ của API hoặc tài nguyên mà bạn muốn gửi yêu cầu.
- **options**: Một đối tượng tùy chọn dùng để cấu hình yêu cầu (phương thức, tiêu đề, thân yêu cầu, v.v.)

#### XMLHttpRequest
Đây là phương pháp truyền thống hơn để thực hiện yêu cầu HTTP.

Cú pháp cơ bản:
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', url, true);
xhr.onload = function() {
  if (xhr.status >= 200 && xhr.status < 300) {
    console.log(JSON.parse(xhr.responseText));
  } else {
    console.error('Request failed:', xhr.statusText);
  }
};
xhr.onerror = function() {
  console.error('Network error');
};
xhr.send();
```

### Chi tiết
- **Fetch API** hỗ trợ Promise, điều này giúp xử lý bất đồng bộ một cách dễ dàng hơn.
- **XMLHttpRequest** là phương pháp cũ hơn và có thể phức tạp hơn khi xử lý các yêu cầu bất đồng bộ.

## Ví dụ
### Ví dụ sử dụng Fetch API
```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('Fetch error:', error));
```

### Ví dụ sử dụng XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onload = function() {
  if (xhr.status === 200) {
    console.log(JSON.parse(xhr.responseText));
  } else {
    console.error('Error:', xhr.status);
  }
};
xhr.send();
```

## Giải thích
- **Lỗi phổ biến**: Một số lập trình viên mới có thể quên kiểm tra trạng thái của phản hồi khi sử dụng Fetch API. Điều này có thể dẫn đến việc không xử lý được lỗi.
- **CORS**: Khi thực hiện yêu cầu đến một nguồn khác (cross-origin), bạn có thể gặp vấn đề với CORS (Cross-Origin Resource Sharing). Đảm bảo rằng máy chủ hỗ trợ CORS để yêu cầu thành công.
- **Chưa hỗ trợ Internet Explorer**: Fetch API không được hỗ trợ trên Internet Explorer. Nếu bạn cần hỗ trợ trình duyệt này, hãy sử dụng XMLHttpRequest hoặc thư viện như Axios.

## Tóm tắt một dòng
"Request" trong JavaScript cho phép giao tiếp với máy chủ thông qua các yêu cầu HTTP, chủ yếu sử dụng Fetch API hoặc XMLHttpRequest.