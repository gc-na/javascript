<!--
Meta Description: # Sự kiện onanimationiteration trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Sự kiện `onanimationiteration` trong JavaScript cho phép lập trình viên...
Meta Keywords: một, animation, kiện, onanimationiteration, các
-->

# Sự kiện onanimationiteration trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Sự kiện `onanimationiteration` trong JavaScript cho phép lập trình viên theo dõi và xử lý các lần lặp của một animation CSS đang diễn ra trên một phần tử HTML.

## Tài liệu
### Mục đích
Sự kiện `onanimationiteration` được kích hoạt mỗi khi một animation CSS hoàn thành một lần lặp. Điều này rất hữu ích khi bạn cần thực hiện một hành động cụ thể mỗi khi một phần của animation diễn ra, chẳng hạn như thay đổi trạng thái, cập nhật nội dung hoặc thực hiện các thao tác khác trong ứng dụng.

### Cách sử dụng
Để sử dụng sự kiện `onanimationiteration`, bạn có thể gán nó trực tiếp cho một phần tử DOM hoặc thông qua JavaScript. Dưới đây là cú pháp cơ bản:

```javascript
element.onanimationiteration = function(event) {
  // Xử lý khi animation lặp lại
};
```

### Chi tiết
- **Tham số sự kiện**: Sự kiện `onanimationiteration` nhận một đối tượng sự kiện, cho phép bạn truy cập thông tin chi tiết về lần lặp animation.
- **Tương thích**: Hầu hết các trình duyệt hiện đại đều hỗ trợ sự kiện này, nhưng bạn nên kiểm tra tính tương thích với các phiên bản cũ hơn nếu cần thiết.

## Ví dụ
### Ví dụ cơ bản
Dưới đây là một ví dụ đơn giản về cách sử dụng sự kiện `onanimationiteration`:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animation Iteration Example</title>
    <style>
        .animate {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: move 2s infinite;
        }

        @keyframes move {
            0% { transform: translateX(0); }
            100% { transform: translateX(100px); }
        }
    </style>
</head>
<body>

<div class="animate" id="box"></div>

<script>
    const box = document.getElementById('box');

    box.onanimationiteration = function(event) {
        console.log('Animation iteration completed');
    };
</script>

</body>
</html>
```
Trong ví dụ trên, mỗi khi animation hoàn thành một lần lặp, một thông báo sẽ được in ra console.

## Giải thích
### Những điều cần lưu ý
- **Thời gian và tần suất**: Nếu animation diễn ra quá nhanh hoặc quá chậm, có thể bạn sẽ không nhận thấy các lần lặp rõ ràng. Chỉnh sửa tốc độ animation để dễ dàng kiểm tra sự kiện này.
- **Hiệu suất**: Theo dõi nhiều animation trên một trang có thể ảnh hưởng đến hiệu suất. Hãy đảm bảo rằng các hành động trong callback không gây tắc nghẽn hoặc làm chậm trang web.

## Tóm tắt một dòng
Sự kiện `onanimationiteration` trong JavaScript cho phép bạn xử lý các lần lặp của animation CSS, cung cấp khả năng tương tác linh hoạt trong các ứng dụng web.