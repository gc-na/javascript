<!--
Meta Description: # HTMLBaseElement trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng ## Tóm tắt HTMLBaseElement là một phần của DOM (Document Object Model) trong HTML, ch...
Meta Keywords: html, trong, tài, cho, các
-->

# HTMLBaseElement trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng

## Tóm tắt
HTMLBaseElement là một phần của DOM (Document Object Model) trong HTML, cho phép lập trình viên JavaScript quản lý và tương tác với các thẻ `<base>` trong tài liệu HTML, từ đó xác định URL cơ sở cho các liên kết và tài nguyên tương đối.

## Tài liệu
HTMLBaseElement đại diện cho phần tử `<base>` trong HTML, cho phép chỉ định URL cơ sở cho các liên kết trong tài liệu. Phần tử này thường được đặt trong phần `<head>` của tài liệu HTML. URL cơ sở giúp trình duyệt hiểu các liên kết tương đối mà không cần phải chỉ định đường dẫn đầy đủ.

### Cấu trúc
```html
<base href="https://example.com/">
```

### Thuộc tính
- **href**: Thuộc tính này chứa URL cơ sở. Nó có thể được định nghĩa bằng đường dẫn tuyệt đối hoặc tương đối.
  
### Phương thức
- **getAttribute(name)**: Lấy giá trị của thuộc tính được chỉ định.
- **setAttribute(name, value)**: Đặt giá trị cho thuộc tính được chỉ định.

### Ví dụ sử dụng
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <base href="https://example.com/">
    <title>Ví dụ về HTMLBaseElement</title>
</head>
<body>
    <a href="page1.html">Liên kết đến Page 1</a>
    <a href="page2.html">Liên kết đến Page 2</a>
</body>
</html>
```
Trong ví dụ trên, nếu người dùng nhấp vào các liên kết, trình duyệt sẽ điều hướng đến `https://example.com/page1.html` và `https://example.com/page2.html`.

## Giải thích
Một số điểm cần lưu ý khi làm việc với HTMLBaseElement:
- Nếu không có thẻ `<base>`, các liên kết tương đối sẽ được tính từ URL của tài liệu hiện tại.
- Chỉ có một thẻ `<base>` có thể tồn tại trong một tài liệu. Nhiều thẻ sẽ dẫn đến hành vi không xác định.
- Thẻ `<base>` phải được khai báo trước bất kỳ thẻ `<a>` nào trong tài liệu.

## Tóm tắt một dòng
HTMLBaseElement cho phép lập trình viên JavaScript quản lý URL cơ sở cho các liên kết trong tài liệu HTML, giúp dễ dàng điều hướng giữa các trang.