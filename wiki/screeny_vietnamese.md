<!--
Meta Description: # screenY trong JavaScript: Định Nghĩa và Cách Sử Dụng ## Tóm tắt `screenY` là một thuộc tính trong đối tượng sự kiện của JavaScript, cho phép bạn lấy...
Meta Keywords: screeny, của, chuột, kiện, trong
-->

# screenY trong JavaScript: Định Nghĩa và Cách Sử Dụng

## Tóm tắt
`screenY` là một thuộc tính trong đối tượng sự kiện của JavaScript, cho phép bạn lấy tọa độ y của con trỏ chuột trên toàn bộ màn hình, so với điểm gốc (0,0) ở góc trên bên trái của màn hình.

## Tài liệu
### Mục đích
`screenY` được sử dụng để xác định vị trí dọc của chuột trên màn hình, giúp lập trình viên có thể xử lý các sự kiện liên quan đến vị trí của chuột, chẳng hạn như di chuyển, nhấp chuột, hoặc kéo thả.

### Cách sử dụng
`screenY` là một thuộc tính không có hàm, có thể được truy cập từ đối tượng sự kiện (event object) trong các trình xử lý sự kiện của JavaScript. Bạn có thể sử dụng nó trong các sự kiện như `mousemove`, `click`, và nhiều sự kiện khác.

### Cú pháp
```javascript
event.screenY
```

## Ví dụ
### Ví dụ 1: Lấy tọa độ Y khi nhấp chuột
```javascript
document.addEventListener('click', function(event) {
    console.log('Tọa độ Y trên màn hình:', event.screenY);
});
```

### Ví dụ 2: Theo dõi di chuyển chuột
```javascript
document.addEventListener('mousemove', function(event) {
    console.log('Tọa độ Y của chuột:', event.screenY);
});
```

## Giải thích
- **Điểm gốc:** Tọa độ Y được đo từ góc trên bên trái của màn hình, với giá trị tăng dần khi di chuyển xuống dưới.
- **Định dạng giá trị:** `screenY` trả về một số nguyên, đại diện cho pixel.
- **Khác biệt với clientY:** `screenY` khác với `clientY`, vì `clientY` chỉ cung cấp tọa độ y của chuột trong cửa sổ trình duyệt, không tính đến thanh cuộn.

### Những lưu ý
- **Trình duyệt hỗ trợ:** Tất cả các trình duyệt hiện đại đều hỗ trợ thuộc tính này.
- **Sự kiện không phải lúc nào cũng có `screenY`:** Đảm bảo rằng bạn đang sử dụng thuộc tính này trong bối cảnh của một sự kiện chuột.

## Tóm tắt một câu
`screenY` trong JavaScript là thuộc tính cho phép bạn lấy tọa độ y của con trỏ chuột trên màn hình, rất hữu ích trong việc xử lý các sự kiện liên quan đến chuột.