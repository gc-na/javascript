<!--
Meta Description: # Sự kiện onwebkitAnimationEnd trong JavaScript: Hướng dẫn Chi tiết ## Tóm tắt `onwebkitAnimationEnd` là sự kiện trong JavaScript được kích hoạt khi m...
Meta Keywords: kiện, hoạt, các, ảnh, bạn
-->

# Sự kiện onwebkitAnimationEnd trong JavaScript: Hướng dẫn Chi tiết

## Tóm tắt
`onwebkitAnimationEnd` là sự kiện trong JavaScript được kích hoạt khi một hoạt ảnh (animation) được thực hiện xong trên các trình duyệt hỗ trợ WebKit. Sự kiện này cho phép lập trình viên thực hiện các hành động hoặc thay đổi trạng thái khi hoạt ảnh kết thúc.

## Tài liệu

### Mục đích
Sự kiện `onwebkitAnimationEnd` giúp lập trình viên theo dõi và xử lý khi một hoạt ảnh CSS hoàn tất. Điều này rất hữu ích khi bạn muốn thực hiện các thao tác như xóa lớp CSS, bắt đầu một hoạt ảnh mới, hoặc thông báo cho người dùng rằng một hành động đã hoàn tất.

### Cách sử dụng
Để sử dụng sự kiện `onwebkitAnimationEnd`, bạn cần gán nó cho một phần tử DOM. Đây là cách thực hiện:

```javascript
const element = document.querySelector('.animated-element');

element.addEventListener('webkitAnimationEnd', function() {
    console.log('Hoạt ảnh đã kết thúc!');
});
```

### Chi tiết
- **Trình duyệt hỗ trợ**: Sự kiện `onwebkitAnimationEnd` chủ yếu được hỗ trợ trên các trình duyệt sử dụng WebKit như Safari và một số phiên bản của Chrome. Đối với các trình duyệt khác, bạn nên sử dụng `animationend` để đảm bảo khả năng tương thích.
- **Các thuộc tính có liên quan**: Khi sự kiện này xảy ra, bạn có thể truy cập vào thuộc tính `animationName`, `elapsedTime`, và các thông tin khác thông qua đối tượng sự kiện.

## Ví dụ

### Ví dụ Cơ bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .animated-element {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: example-animation 2s forwards;
        }

        @keyframes example-animation {
            from { transform: translateX(0); }
            to { transform: translateX(200px); }
        }
    </style>
</head>
<body>

<div class="animated-element"></div>

<script>
    const element = document.querySelector('.animated-element');

    element.addEventListener('webkitAnimationEnd', function() {
        console.log('Hoạt ảnh đã kết thúc!');
        element.style.backgroundColor = 'green'; // Thay đổi màu sắc sau khi hoạt ảnh kết thúc
    });
</script>

</body>
</html>
```

## Giải thích
- **Điểm mạnh**: Sự kiện này cho phép bạn thực hiện các hành động ngay khi hoạt ảnh hoàn tất, giúp tạo trải nghiệm người dùng mượt mà hơn.
- **Điểm yếu**: Không phải tất cả các trình duyệt đều hỗ trợ sự kiện `onwebkitAnimationEnd`. Bạn nên sử dụng `animationend` như một lựa chọn thay thế để đảm bảo mã của bạn hoạt động trên tất cả các trình duyệt.
- **Lưu ý**: Khi sử dụng sự kiện này, hãy chắc chắn rằng hoạt ảnh CSS của bạn đã được định nghĩa và áp dụng đúng cho phần tử mà bạn đang theo dõi.

## Tóm tắt một dòng
`onwebkitAnimationEnd` là sự kiện trong JavaScript cho phép bạn theo dõi khi một hoạt ảnh CSS hoàn tất trên các trình duyệt hỗ trợ WebKit.