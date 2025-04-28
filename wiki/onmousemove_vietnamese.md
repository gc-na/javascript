<!--
Meta Description: # Sự kiện onmousemove trong JavaScript: Cách sử dụng và ví dụ ## Tóm tắt Sự kiện `onmousemove` trong JavaScript cho phép bạn theo dõi vị trí của chuột...
Meta Keywords: kiện, chuột, html, onmousemove, event
-->

# Sự kiện onmousemove trong JavaScript: Cách sử dụng và ví dụ

## Tóm tắt
Sự kiện `onmousemove` trong JavaScript cho phép bạn theo dõi vị trí của chuột khi nó di chuyển trên một phần tử HTML. Đây là một công cụ hữu ích để tạo ra các hiệu ứng tương tác trong ứng dụng web của bạn.

## Tài liệu
Sự kiện `onmousemove` là một phần trong các sự kiện của chuột, được kích hoạt mỗi khi con trỏ chuột di chuyển trên một phần tử cụ thể. Nó thường được sử dụng để tạo ra các hiệu ứng động, như làm nổi bật các phần tử, hiển thị thông tin bổ sung, hoặc thay đổi giao diện người dùng.

### Cú pháp
```javascript
element.onmousemove = function(event) {
    // Code xử lý sự kiện
};
```

### Tham số
- **event**: Một đối tượng sự kiện chứa thông tin về vị trí của chuột và các trạng thái khác tại thời điểm sự kiện được kích hoạt.

### Sử dụng
Để sử dụng sự kiện `onmousemove`, bạn cần gán nó cho một phần tử HTML, như sau:
```html
<div id="myElement">Di chuyển chuột vào đây!</div>
<script>
    document.getElementById("myElement").onmousemove = function(event) {
        console.log("X: " + event.clientX + ", Y: " + event.clientY);
    };
</script>
```
Trong ví dụ trên, khi chuột di chuyển vào khu vực của `div`, tọa độ X và Y của chuột sẽ được in ra console.

## Ví dụ
### Ví dụ 1: Theo dõi vị trí chuột
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onmousemove Example</title>
</head>
<body>
    <div id="trackingArea" style="width: 300px; height: 300px; border: 1px solid black;">
        Di chuyển chuột vào đây
    </div>
    <p id="coordinates">Tọa độ: </p>

    <script>
        document.getElementById("trackingArea").onmousemove = function(event) {
            document.getElementById("coordinates").innerText = "Tọa độ: X=" + event.clientX + ", Y=" + event.clientY;
        };
    </script>
</body>
</html>
```

### Ví dụ 2: Thay đổi màu nền khi di chuyển chuột
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Change Background Color</title>
</head>
<body>
    <div id="colorArea" style="width: 100%; height: 100vh;">
        Di chuyển chuột để thay đổi màu nền
    </div>

    <script>
        document.getElementById("colorArea").onmousemove = function(event) {
            const red = Math.floor((event.clientX / window.innerWidth) * 255);
            const green = Math.floor((event.clientY / window.innerHeight) * 255);
            this.style.backgroundColor = `rgb(${red}, ${green}, 150)`;
        };
    </script>
</body>
</html>
```

## Giải thích
Khi sử dụng `onmousemove`, có một số điều cần lưu ý:
- **Hiệu suất**: Nếu bạn thực hiện các phép toán nặng trong hàm xử lý sự kiện, điều này có thể làm giảm hiệu suất của trang web. Hãy tối ưu hóa mã của bạn để giảm tải khi sự kiện xảy ra.
- **Sự kiện liên tục**: Sự kiện này có thể được kích hoạt rất nhiều lần trong một khoảng thời gian ngắn, vì vậy hãy cân nhắc việc sử dụng debounce hoặc throttle nếu bạn cần thực hiện thao tác phức tạp hơn.
- **Tương tác với các phần tử khác**: Hãy chú ý rằng nếu bạn có nhiều phần tử lồng nhau, sự kiện có thể được kích hoạt trên nhiều phần tử, dẫn đến việc xử lý không như mong đợi.

## Tóm tắt một dòng
Sự kiện `onmousemove` trong JavaScript cho phép theo dõi vị trí chuột trên một phần tử HTML, mở ra nhiều khả năng tương tác cho ứng dụng web.