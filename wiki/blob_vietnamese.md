<!--
Meta Description: # Blob trong JavaScript: Tìm Hiểu và Sử Dụng ## Tóm Tắt Blob (Binary Large Object) trong JavaScript là một đối tượng dùng để lưu trữ dữ liệu nhị phân ...
Meta Keywords: blob, liệu, trong, các, url
-->

# Blob trong JavaScript: Tìm Hiểu và Sử Dụng

## Tóm Tắt
Blob (Binary Large Object) trong JavaScript là một đối tượng dùng để lưu trữ dữ liệu nhị phân lớn, chẳng hạn như hình ảnh, âm thanh, và video. Blob cho phép bạn xử lý và quản lý dữ liệu nhị phân một cách dễ dàng trong các ứng dụng web.

## Tài Liệu
### Mục Đích
Blob được sử dụng để đại diện cho các dữ liệu nhị phân không cấu trúc. Nó là một phần quan trọng trong việc xử lý các tệp và dữ liệu nhị phân trong JavaScript, thường được dùng trong các ứng dụng web như tải lên tệp, tạo hình ảnh từ dữ liệu nhị phân, và nhiều hơn nữa.

### Cách Sử Dụng
Đối tượng Blob được khởi tạo thông qua constructor `Blob()` và có thể nhận vào một mảng các dữ liệu nhị phân và các tùy chọn về loại MIME (Media Type).

#### Cú pháp:
```javascript
let myBlob = new Blob([data], { type: 'image/png' });
```

- **data**: Mảng chứa dữ liệu nhị phân (có thể là một chuỗi hoặc một mảng các đối tượng).
- **type**: Tùy chọn chỉ định loại MIME của Blob.

### Thông tin chi tiết
- Blob có thể chứa dữ liệu từ nhiều nguồn khác nhau, bao gồm các tệp từ người dùng, dữ liệu tạo ra từ mã JavaScript, v.v.
- Bạn có thể sử dụng các phương thức như `URL.createObjectURL()` để tạo URL tạm thời cho Blob, giúp dễ dàng truy cập và hiển thị dữ liệu trong trình duyệt.

## Ví Dụ
### Ví dụ 1: Tạo một Blob từ chuỗi
```javascript
const data = new Blob(["Hello, World!"], { type: 'text/plain' });
const url = URL.createObjectURL(data);
console.log(url); // Hiển thị URL Blob
```

### Ví dụ 2: Tạo một Blob từ hình ảnh
```javascript
const imgData = new Uint8Array([/* dữ liệu nhị phân hình ảnh */]);
const imageBlob = new Blob([imgData], { type: 'image/jpeg' });
const imageUrl = URL.createObjectURL(imageBlob);
document.getElementById('myImage').src = imageUrl; // Gán URL vào thẻ img
```

## Giải Thích
- **Lưu ý về kích thước Blob**: Kích thước tối đa của Blob phụ thuộc vào trình duyệt và thiết bị, vì vậy cần thận trọng khi làm việc với các tệp lớn.
- **Thời gian tồn tại của URL**: URL tạo từ Blob chỉ tồn tại trong phiên làm việc hiện tại; hãy sử dụng `URL.revokeObjectURL()` để giải phóng bộ nhớ khi không cần nữa.
- **Không hỗ trợ mọi loại MIME**: Một số loại MIME có thể không được hỗ trợ trong tất cả các trình duyệt, hãy kiểm tra khả năng tương thích trước khi sử dụng.

## Tóm Tắt Một Dòng
Blob trong JavaScript là đối tượng cho phép lưu trữ và quản lý dữ liệu nhị phân lớn, hỗ trợ trong việc xử lý tệp và dữ liệu trong các ứng dụng web.