<!--
Meta Description: # Phản Hồi (Response) trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt Phản hồi (Response) trong JavaScript là một đối tượng quan trọng trong các ứng d...
Meta Keywords: response, liệu, thức, phản, hồi
-->

# Phản Hồi (Response) trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
Phản hồi (Response) trong JavaScript là một đối tượng quan trọng trong các ứng dụng web, đặc biệt khi làm việc với API và giao thức HTTP. Đối tượng này chứa thông tin về phản hồi từ máy chủ, bao gồm dữ liệu trả về, mã trạng thái và tiêu đề.

## Tài Liệu
### Mục Đích
Đối tượng `Response` được sử dụng để đại diện cho phản hồi từ một yêu cầu HTTP. Nó cung cấp các phương thức và thuộc tính giúp bạn truy cập dữ liệu trả về từ máy chủ.

### Cách Sử Dụng
`Response` thường được tạo ra khi bạn sử dụng phương thức `fetch()` để thực hiện yêu cầu HTTP. Dưới đây là cú pháp cơ bản của phương thức `fetch()`:

```javascript
fetch(url)
  .then(response => {
    // Xử lý phản hồi tại đây
  })
  .catch(error => {
    // Xử lý lỗi tại đây
  });
```

### Các Thuộc Tính và Phương Thức
- **status**: Mã trạng thái HTTP của phản hồi (ví dụ: 200, 404).
- **statusText**: Mô tả ngắn gọn về mã trạng thái.
- **headers**: Đối tượng `Headers` chứa các tiêu đề của phản hồi.
- **json()**: Phương thức trả về một Promise với dữ liệu JSON.
- **text()**: Phương thức trả về một Promise với dữ liệu dưới dạng văn bản.
- **blob()**: Phương thức trả về một Promise với dữ liệu dưới dạng Blob.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Mạng lưới lỗi: ' + response.statusText);
    }
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Có lỗi xảy ra:', error);
  });
```

### Ví Dụ Với Phản Hồi Văn Bản
```javascript
fetch('https://api.example.com/text')
  .then(response => response.text())
  .then(data => {
    console.log(data);
  });
```

## Giải Thích
### Cạm Bẫy Thường Gặp
- **Kiểm Tra Mã Trạng Thái**: Luôn kiểm tra thuộc tính `ok` hoặc mã trạng thái để đảm bảo yêu cầu thành công trước khi xử lý dữ liệu.
- **Xử Lý Lỗi**: Đảm bảo có xử lý lỗi trong chuỗi Promise để tránh ứng dụng bị treo khi gặp sự cố.

### Ghi Chú Bổ Sung
- Đối tượng `Response` không chỉ chứa dữ liệu mà còn nhiều thông tin quan trọng khác. Hãy tận dụng các thuộc tính và phương thức để lấy dữ liệu một cách hiệu quả.
- Khi làm việc với dữ liệu lớn, hãy cân nhắc sử dụng `blob()` hoặc `arrayBuffer()` để xử lý dữ liệu.

## Tóm Tắt Một Câu
Đối tượng `Response` trong JavaScript là một phần thiết yếu của việc xử lý phản hồi từ yêu cầu HTTP, cung cấp thông tin và phương thức để truy cập dữ liệu trả về từ máy chủ.