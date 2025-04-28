<!--
Meta Description: # Sự Kiện onresize trong JavaScript: Cách Sử Dụng và Ví Dụ ## Tóm tắt Sự kiện `onresize` trong JavaScript cho phép lập trình viên theo dõi và xử lý cá...
Meta Keywords: kiện, onresize, kích, thước, cửa
-->

# Sự Kiện onresize trong JavaScript: Cách Sử Dụng và Ví Dụ

## Tóm tắt
Sự kiện `onresize` trong JavaScript cho phép lập trình viên theo dõi và xử lý các thay đổi kích thước của cửa sổ trình duyệt, từ đó tạo ra những trải nghiệm tương tác tốt hơn cho người dùng.

## Tài liệu
Sự kiện `onresize` là một sự kiện xảy ra khi kích thước của cửa sổ trình duyệt thay đổi. Điều này có thể xảy ra khi người dùng thay đổi kích thước cửa sổ hoặc khi một yếu tố DOM thay đổi kích thước. Sự kiện này rất hữu ích để thực hiện các điều chỉnh giao diện người dùng hoặc cập nhật nội dung trong thời gian thực.

### Cách sử dụng
Để sử dụng sự kiện `onresize`, bạn có thể gán một hàm xử lý sự kiện cho đối tượng `window`. Dưới đây là cách thức thực hiện:

```javascript
window.onresize = function() {
    console.log("Kích thước cửa sổ đã thay đổi!");
};
```

Ngoài ra, bạn cũng có thể sử dụng phương thức `addEventListener` để thêm sự kiện:

```javascript
window.addEventListener('resize', function() {
    console.log("Kích thước cửa sổ đã thay đổi!");
});
```

### Chi tiết
- **Tham số**: Sự kiện `onresize` không có tham số cụ thể nào. Tuy nhiên, bạn có thể truy cập kích thước cửa sổ thông qua `window.innerWidth` và `window.innerHeight`.
- **Trả về**: Sự kiện này không trả về giá trị, mà chỉ thực hiện hàm xử lý mà bạn đã gán.
- **Tương thích**: Sự kiện `onresize` được hỗ trợ trên hầu hết các trình duyệt hiện đại, bao gồm Chrome, Firefox, Safari và Edge.

## Ví dụ
Dưới đây là một ví dụ minh họa cách sử dụng sự kiện `onresize` để thay đổi văn bản hiển thị dựa trên kích thước cửa sổ:

```javascript
window.onresize = function() {
    const width = window.innerWidth;
    const height = window.innerHeight;
    document.getElementById("sizeInfo").innerText = `Kích thước cửa sổ: ${width} x ${height}`;
};
```

## Giải thích
Khi sử dụng sự kiện `onresize`, có một số điểm cần lưu ý:
- **Hiệu suất**: Nếu xử lý sự kiện thực hiện các tác vụ tốn thời gian, điều này có thể gây ra độ trễ trong trải nghiệm người dùng. Hãy cân nhắc việc sử dụng `debounce` hoặc `throttle` để giới hạn số lần gọi hàm trong một khoảng thời gian nhất định.
- **Tương tác với các yếu tố khác**: Đảm bảo rằng việc thay đổi kích thước cửa sổ không gây ra các vấn đề không mong muốn với các yếu tố khác trên trang.

## Tóm tắt một câu
Sự kiện `onresize` trong JavaScript cho phép theo dõi và xử lý sự thay đổi kích thước của cửa sổ trình duyệt, mang lại trải nghiệm người dùng mượt mà hơn.