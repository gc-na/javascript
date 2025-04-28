<!--
Meta Description: # HTMLTitleElement trong JavaScript: Cách sử dụng và ví dụ ## Tóm tắt HTMLTitleElement là một đối tượng trong DOM (Document Object Model) đại diện cho...
Meta Keywords: tiêu, thay, đổi, title, của
-->

# HTMLTitleElement trong JavaScript: Cách sử dụng và ví dụ

## Tóm tắt
HTMLTitleElement là một đối tượng trong DOM (Document Object Model) đại diện cho thẻ `<title>` trong tài liệu HTML. Đối tượng này cho phép lập trình viên JavaScript truy cập và thay đổi tiêu đề của trang web.

## Tài liệu
HTMLTitleElement là một phần của DOM API, cụ thể là thuộc về giao diện của phần tử HTML. Tiêu đề của một trang web được xác định bởi thẻ `<title>`, và thông qua HTMLTitleElement, bạn có thể lấy hoặc thay đổi nội dung của nó.

### Mục đích
- Cung cấp một cách để truy cập và quản lý tiêu đề của trang web thông qua JavaScript.
- Giúp cải thiện SEO (tối ưu hóa công cụ tìm kiếm) bằng cách cho phép lập trình viên thay đổi tiêu đề trang động.

### Cách sử dụng
Để truy cập đối tượng HTMLTitleElement, bạn có thể sử dụng thuộc tính `document.title` hoặc truy cập trực tiếp từ thẻ `<title>`.

```javascript
// Lấy tiêu đề hiện tại
let currentTitle = document.title;

// Thay đổi tiêu đề
document.title = "Tiêu đề mới của trang";
```

## Ví dụ
### Ví dụ cơ bản về việc lấy và thay đổi tiêu đề
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tiêu đề ban đầu</title>
</head>
<body>
    <h1>Chào mừng đến với trang web của tôi!</h1>
    <button id="changeTitle">Thay đổi tiêu đề</button>

    <script>
        // Lấy và hiển thị tiêu đề hiện tại
        console.log(document.title); // In ra: "Tiêu đề ban đầu"

        // Thay đổi tiêu đề khi nhấn nút
        document.getElementById("changeTitle").addEventListener("click", function() {
            document.title = "Tiêu đề đã được thay đổi!";
            console.log(document.title); // In ra: "Tiêu đề đã được thay đổi!"
        });
    </script>
</body>
</html>
```

## Giải thích
### Những lưu ý và lỗi thường gặp
- **SEO và tiêu đề**: Tiêu đề của trang là một trong những yếu tố quan trọng nhất trong SEO. Hãy đảm bảo rằng tiêu đề phản ánh nội dung của trang và chứa các từ khóa liên quan.
- **Thay đổi tiêu đề động**: Thay đổi tiêu đề một cách thường xuyên có thể gây nhầm lẫn cho người dùng và công cụ tìm kiếm. Hãy sử dụng tính năng này một cách hợp lý.
- **Tính tương thích**: Mặc dù HTMLTitleElement được hỗ trợ rộng rãi, hãy kiểm tra tính tương thích nếu bạn đang phát triển ứng dụng cho các trình duyệt cũ.

## Tóm tắt một dòng
HTMLTitleElement cho phép lập trình viên JavaScript truy cập và thay đổi tiêu đề của trang web thông qua đối tượng DOM.