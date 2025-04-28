<!--
Meta Description: # Sự kiện onblur trong JavaScript: Hướng dẫn Cách Sử Dụng và Ví Dụ Thực Tế ## Tóm tắt Sự kiện `onblur` trong JavaScript được sử dụng để xử lý các tình...
Meta Keywords: onblur, dụng, html, kiện, phần
-->

# Sự kiện onblur trong JavaScript: Hướng dẫn Cách Sử Dụng và Ví Dụ Thực Tế

## Tóm tắt
Sự kiện `onblur` trong JavaScript được sử dụng để xử lý các tình huống khi một phần tử mất tiêu điểm, giúp lập trình viên tạo ra các phản hồi tương tác cho người dùng.

## Tài liệu
Sự kiện `onblur` xảy ra khi một phần tử, chẳng hạn như trường nhập liệu (input), mất tiêu điểm. Điều này có nghĩa là khi người dùng nhấp chuột ra ngoài phần tử hoặc điều hướng đến một phần tử khác, sự kiện này sẽ được kích hoạt. Thông thường, `onblur` được sử dụng để thực hiện các hành động như kiểm tra dữ liệu đầu vào hoặc cập nhật giao diện người dùng.

### Cách sử dụng
- Bạn có thể gán sự kiện `onblur` trực tiếp trong HTML hoặc thông qua JavaScript.
- Sự kiện `onblur` có thể được áp dụng cho các phần tử như `input`, `textarea`, và `select`.

### Ví dụ
Dưới đây là một số ví dụ cơ bản về cách sử dụng sự kiện `onblur`.

**Ví dụ 1: Sử dụng onblur trong HTML**
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Ví dụ onblur</title>
</head>
<body>
    <input type="text" id="username" onblur="checkUsername()" placeholder="Nhập tên người dùng">
    <script>
        function checkUsername() {
            alert("Bạn đã rời khỏi trường tên người dùng!");
        }
    </script>
</body>
</html>
```

**Ví dụ 2: Sử dụng onblur với JavaScript**
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Ví dụ onblur với JavaScript</title>
</head>
<body>
    <input type="text" id="email" placeholder="Nhập email">
    <script>
        const emailInput = document.getElementById('email');
        emailInput.onblur = function() {
            console.log("Trường email đã mất tiêu điểm.");
        };
    </script>
</body>
</html>
```

## Giải thích
- **Cạm bẫy thông thường**: Một số trình duyệt có thể không hỗ trợ `onblur` cho tất cả các phần tử, vì vậy việc kiểm tra tính tương thích của trình duyệt là quan trọng.
- **Hành vi không mong muốn**: Khi sử dụng `onblur`, các hành động có thể bị kích hoạt không mong muốn nếu người dùng nhấp vào các phần tử khác trên trang. Do đó, cần phải lên kế hoạch cho các hành động phản hồi sao cho hợp lý.
- **Sự khác biệt với onfocus**: Sự kiện `onfocus` hoạt động ngược lại với `onblur`, tức là nó xảy ra khi một phần tử nhận được tiêu điểm.

## Tóm tắt một câu
Sự kiện `onblur` trong JavaScript cho phép lập trình viên xử lý khi một phần tử mất tiêu điểm, hỗ trợ tạo ra tương tác hiệu quả trong ứng dụng web.