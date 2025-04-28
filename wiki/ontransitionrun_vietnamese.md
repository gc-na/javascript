<!--
Meta Description: # Sự kiện ontransitionrun trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt Sự kiện `ontransitionrun` trong JavaScript được sử dụng để theo dõi và xử lý...
Meta Keywords: đổi, kiện, chuyển, bắt, đầu
-->

# Sự kiện ontransitionrun trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
Sự kiện `ontransitionrun` trong JavaScript được sử dụng để theo dõi và xử lý các chuyển đổi CSS đang diễn ra trên phần tử DOM. Khi một chuyển đổi bắt đầu, sự kiện này sẽ được kích hoạt, giúp lập trình viên có thể thực hiện các hành động tùy chỉnh.

## Tài liệu
### Mục đích
Sự kiện `ontransitionrun` được sử dụng để lắng nghe và phản hồi khi một chuyển đổi CSS bắt đầu. Điều này rất hữu ích để tạo ra các hiệu ứng động hoặc thực hiện các thao tác cụ thể ngay khi một chuyển đổi bắt đầu diễn ra.

### Cách sử dụng
Để sử dụng sự kiện `ontransitionrun`, bạn cần thêm một trình xử lý sự kiện cho phần tử DOM mà bạn muốn theo dõi. Dưới đây là cú pháp cơ bản:

```javascript
element.addEventListener("transitionrun", function(event) {
    // Xử lý khi chuyển đổi bắt đầu
});
```

### Thông tin chi tiết
- **Sự kiện**: `transitionrun` được kích hoạt khi một chuyển đổi CSS bắt đầu. 
- **Thuộc tính sự kiện**: Sự kiện này có thể cung cấp thông tin về phần tử đang thực hiện chuyển đổi thông qua thuộc tính `event.target`.
- **Tính tương thích**: Sự kiện này được hỗ trợ trên hầu hết các trình duyệt hiện đại, bao gồm Chrome, Firefox, Safari và Edge.

## Ví dụ
Dưới đây là vài ví dụ đơn giản về cách sử dụng sự kiện `ontransitionrun`:

### Ví dụ 1: Sử dụng ontransitionrun để thay đổi màu nền
```html
<div id="myElement" style="width: 100px; height: 100px; background-color: red; transition: background-color 2s;"></div>
<button id="startTransition">Bắt đầu chuyển đổi</button>

<script>
    const element = document.getElementById('myElement');
    const button = document.getElementById('startTransition');

    element.addEventListener('transitionrun', function(event) {
        console.log('Chuyển đổi bắt đầu!');
    });

    button.addEventListener('click', function() {
        element.style.backgroundColor = 'blue';
    });
</script>
```

### Ví dụ 2: Hiển thị thông báo khi chuyển đổi bắt đầu
```html
<div id="box" style="width: 100px; height: 100px; background-color: green; transition: transform 1s;"></div>

<script>
    const box = document.getElementById('box');

    box.addEventListener('transitionrun', function() {
        alert('Chuyển đổi bắt đầu!');
    });

    // Kích hoạt chuyển đổi
    box.style.transform = 'rotate(45deg)';
</script>
```

## Giải thích
### Những điều cần lưu ý
- **Đảm bảo rằng chuyển đổi CSS đã được định nghĩa**: Sự kiện `ontransitionrun` sẽ không được kích hoạt nếu không có chuyển đổi nào được áp dụng cho phần tử.
- **Bật sự kiện cho các phần tử khác nhau**: Bạn có thể thêm nhiều trình xử lý cho các phần tử khác nhau, nhưng hãy chắc chắn xác định đúng phần tử để tránh nhầm lẫn.
- **Kiểm tra tính tương thích trình duyệt**: Mặc dù hầu hết các trình duyệt hiện đại hỗ trợ sự kiện này, hãy chắc chắn kiểm tra trước khi triển khai trong ứng dụng thực tế.

## Tóm tắt một dòng
Sự kiện `ontransitionrun` trong JavaScript cho phép lập trình viên theo dõi và phản hồi khi một chuyển đổi CSS bắt đầu trên phần tử DOM.