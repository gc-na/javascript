<!--
Meta Description: # screenX trong JavaScript: Định vị vị trí chuột trên màn hình ## Tóm tắt `screenX` là một thuộc tính trong đối tượng `MouseEvent` trong JavaScript, c...
Meta Keywords: chuột, screenx, của, event, trí
-->

# screenX trong JavaScript: Định vị vị trí chuột trên màn hình

## Tóm tắt
`screenX` là một thuộc tính trong đối tượng `MouseEvent` trong JavaScript, cho phép bạn lấy tọa độ x của chuột tính từ góc trên bên trái của màn hình.

## Tài liệu
### Mục đích
`screenX` được sử dụng để xác định vị trí của chuột trên màn hình toàn cầu. Điều này rất hữu ích trong các ứng dụng web cần biết vị trí chính xác của chuột để thực hiện các hành động như kéo thả, hiển thị tooltip, hoặc xử lý sự kiện tương tác với người dùng.

### Cách sử dụng
Để sử dụng thuộc tính `screenX`, bạn cần lắng nghe sự kiện chuột (như `click`, `mousemove`, v.v.) và truy cập thuộc tính này từ đối tượng sự kiện:

```javascript
element.addEventListener('mousemove', function(event) {
    console.log('Vị trí chuột X trên màn hình: ' + event.screenX);
});
```

### Chi tiết
- `screenX` trả về giá trị kiểu số (number), là tọa độ x của chuột trên màn hình.
- Giá trị này được đo từ cạnh trái của màn hình, với giá trị 0 tương ứng với vị trí bắt đầu.
- `screenX` có thể được sử dụng cùng với thuộc tính `screenY` để lấy tọa độ y của chuột.

## Ví dụ
### Ví dụ 1: Lấy vị trí chuột khi di chuyển
```javascript
document.addEventListener('mousemove', function(event) {
    console.log('Vị trí chuột X: ' + event.screenX + ', Y: ' + event.screenY);
});
```

### Ví dụ 2: Hiển thị vị trí chuột trong một phần tử
```html
<div id="coordinateDisplay" style="position: absolute; background: lightgrey;"></div>

<script>
document.addEventListener('mousemove', function(event) {
    const display = document.getElementById('coordinateDisplay');
    display.style.left = event.screenX + 'px';
    display.style.top = event.screenY + 'px';
    display.textContent = 'X: ' + event.screenX + ', Y: ' + event.screenY;
});
</script>
```

## Giải thích
- **Những cạm bẫy phổ biến**: Một số lập trình viên có thể nhầm lẫn giữa `screenX` và `clientX`. `clientX` trả về tọa độ x tính từ góc trên bên trái của cửa sổ trình duyệt, trong khi `screenX` tính từ góc trên bên trái của màn hình.
- **Lưu ý**: Vị trí của chuột có thể thay đổi khi người dùng phóng to hoặc thu nhỏ cửa sổ trình duyệt. Đảm bảo kiểm tra các điều kiện tương thích khi xử lý sự kiện chuột.

## Tóm tắt một dòng
`screenX` trong JavaScript cho phép lấy tọa độ x của chuột tính từ góc trên bên trái của màn hình, hỗ trợ trong việc phát triển các ứng dụng tương tác.