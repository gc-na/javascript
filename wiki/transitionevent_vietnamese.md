<!--
Meta Description: # TransitionEvent trong JavaScript: Hiểu Biết và Ứng Dụng ## Tóm tắt TransitionEvent là một sự kiện trong JavaScript được kích hoạt khi một chuyển tiế...
Meta Keywords: chuyển, tiếp, một, transitionevent, các
-->

# TransitionEvent trong JavaScript: Hiểu Biết và Ứng Dụng

## Tóm tắt
TransitionEvent là một sự kiện trong JavaScript được kích hoạt khi một chuyển tiếp CSS bắt đầu hoặc kết thúc, cho phép lập trình viên theo dõi và quản lý các hiệu ứng chuyển tiếp trên các phần tử DOM.

## Tài liệu
### Mục đích
TransitionEvent cung cấp thông tin về các sự kiện chuyển tiếp CSS, cho phép bạn thực hiện các hành động cụ thể khi một chuyển tiếp bắt đầu hoặc kết thúc.

### Cách sử dụng
Để sử dụng TransitionEvent, bạn cần lắng nghe sự kiện `transitionend` trên một phần tử DOM. Sự kiện này sẽ được kích hoạt khi một chuyển tiếp CSS hoàn tất. Bạn có thể truy cập các thuộc tính của TransitionEvent để lấy thông tin chi tiết về chuyển tiếp.

### Chi tiết
- **Thuộc tính**:
  - `propertyName`: Tên thuộc tính CSS mà chuyển tiếp diễn ra.
  - `elapsedTime`: Thời gian (tính bằng giây) đã trôi qua từ khi chuyển tiếp bắt đầu.
  - `pseudoElement`: Nếu có, tên của pseudo-element liên quan đến chuyển tiếp.

### Cú pháp
```javascript
element.addEventListener('transitionend', function(event) {
    console.log('Chuyển tiếp hoàn tất cho:', event.propertyName);
});
```

## Ví dụ
### Ví dụ Cơ Bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TransitionEvent Ví Dụ</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: background-color 2s;
        }
        .box.active {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div class="box" id="box"></div>
    <button id="toggle">Chuyển đổi Màu</button>

    <script>
        const box = document.getElementById('box');
        const button = document.getElementById('toggle');

        button.addEventListener('click', () => {
            box.classList.toggle('active');
        });

        box.addEventListener('transitionend', (event) => {
            console.log('Chuyển tiếp hoàn tất cho:', event.propertyName);
        });
    </script>
</body>
</html>
```

## Giải thích
### Những cạm bẫy phổ biến
- **Thời gian chuyển tiếp**: Đảm bảo rằng thời gian chuyển tiếp trong CSS phù hợp với thời gian bạn mong đợi để các sự kiện được kích hoạt đúng lúc.
- **Một số trình duyệt không hỗ trợ**: Một số trình duyệt cũ có thể không hỗ trợ đầy đủ TransitionEvent. Hãy kiểm tra tính tương thích trước khi triển khai.
- **Pseudo-elements**: Nếu bạn sử dụng pseudo-elements, hãy nhớ rằng chúng cũng có thể tạo ra sự kiện `transitionend`, vì vậy hãy kiểm tra thuộc tính `pseudoElement` để xử lý đúng.

## Tóm tắt một câu
TransitionEvent là một sự kiện trong JavaScript cho phép theo dõi các chuyển tiếp CSS trên các phần tử DOM, cung cấp thông tin chi tiết về quá trình chuyển tiếp.