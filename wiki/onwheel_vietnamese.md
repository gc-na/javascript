<!--
Meta Description: # Sự kiện onwheel trong JavaScript: Hiểu và Sử Dụng ## Tóm tắt Sự kiện `onwheel` trong JavaScript giúp phát hiện các hành động cuộn chuột trên trang w...
Meta Keywords: cuộn, kiện, onwheel, cho, một
-->

# Sự kiện onwheel trong JavaScript: Hiểu và Sử Dụng

## Tóm tắt
Sự kiện `onwheel` trong JavaScript giúp phát hiện các hành động cuộn chuột trên trang web, cho phép lập trình viên xử lý các tương tác cuộn một cách linh hoạt và hiệu quả.

## Tài liệu
Sự kiện `onwheel` là một sự kiện DOM được kích hoạt khi người dùng cuộn chuột. Sự kiện này cho phép bạn theo dõi và phản ứng với hành động cuộn, cung cấp thông tin về hướng và tốc độ cuộn. Sự kiện `onwheel` là một phần của tiêu chuẩn DOM Level 3 Events và hỗ trợ các trình duyệt hiện đại.

### Mục đích
Mục đích chính của sự kiện `onwheel` là để cung cấp cho lập trình viên khả năng xử lý các hành động cuộn một cách chi tiết, bao gồm cả việc xác định hướng cuộn (lên hoặc xuống) và tốc độ cuộn.

### Cách sử dụng
Để sử dụng sự kiện `onwheel`, bạn có thể gán nó cho một phần tử DOM như sau:

```javascript
element.onwheel = function(event) {
    // Xử lý sự kiện cuộn
};
```

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng sự kiện `onwheel`:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ví dụ onwheel</title>
</head>
<body>
    <div style="height: 200px; overflow-y: scroll;">
        <p>Nội dung dài...</p>
        <p>Nội dung dài...</p>
        <p>Nội dung dài...</p>
        <p>Nội dung dài...</p>
        <p>Nội dung dài...</p>
    </div>

    <script>
        const scrollDiv = document.querySelector('div');

        scrollDiv.onwheel = function(event) {
            if (event.deltaY > 0) {
                console.log('Cuộn xuống');
            } else {
                console.log('Cuộn lên');
            }
        };
    </script>
</body>
</html>
```

Trong ví dụ này, khi người dùng cuộn chuột trong vùng div, thông báo sẽ được in ra console để cho biết hướng cuộn.

## Giải thích
### Những điểm cần lưu ý
- **Tốc độ cuộn:** Giá trị `event.deltaY` cho biết tốc độ cuộn. Một giá trị dương cho biết cuộn xuống, trong khi giá trị âm cho biết cuộn lên.
- **Ngăn chặn hành động mặc định:** Nếu bạn muốn ngăn chặn hành động cuộn mặc định của trình duyệt, bạn có thể gọi `event.preventDefault()`.
- **Hiệu suất:** Hãy cẩn thận với việc sử dụng sự kiện `onwheel` trong các ứng dụng lớn hoặc phức tạp, vì nó có thể gây ra hiệu suất kém nếu không được tối ưu hóa.

## Tóm tắt một câu
Sự kiện `onwheel` trong JavaScript cho phép phát hiện và xử lý các hành động cuộn chuột, mang lại khả năng kiểm soát chi tiết hơn cho các tương tác cuộn trên trang web.