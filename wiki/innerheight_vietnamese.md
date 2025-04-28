<!--
Meta Description: # innerHeight trong JavaScript: Đo chiều cao vùng hiển thị của cửa sổ ## Tóm tắt `innerHeight` là một thuộc tính trong JavaScript cho phép bạn lấy chi...
Meta Keywords: innerheight, của, chiều, cao, hiển
-->

# innerHeight trong JavaScript: Đo chiều cao vùng hiển thị của cửa sổ

## Tóm tắt
`innerHeight` là một thuộc tính trong JavaScript cho phép bạn lấy chiều cao của vùng hiển thị (viewport) của một cửa sổ trình duyệt. Nó là một phần của đối tượng `window` và thường được sử dụng để điều chỉnh giao diện người dùng dựa trên kích thước màn hình.

## Tài liệu
### Mục đích
`window.innerHeight` trả về chiều cao của vùng hiển thị hiện tại trong trình duyệt, tính bằng pixel. Đây là một thuộc tính hữu ích khi bạn cần biết kích thước của cửa sổ để tạo các bố cục động hoặc responsive.

### Cách sử dụng
`innerHeight` có thể được sử dụng như sau:

```javascript
let height = window.innerHeight;
```

### Chi tiết
- **Giá trị trả về**: Giá trị của `innerHeight` là một số nguyên đại diện cho chiều cao của vùng hiển thị, không bao gồm thanh cuộn.
- **Thay đổi kích thước cửa sổ**: Khi người dùng thay đổi kích thước cửa sổ trình duyệt, giá trị của `innerHeight` sẽ tự động cập nhật.
- **Tương thích**: `innerHeight` được hỗ trợ trên tất cả các trình duyệt hiện đại, bao gồm Chrome, Firefox, Safari và Edge.

## Ví dụ
### Ví dụ cơ bản
```javascript
// Lấy chiều cao của vùng hiển thị
let height = window.innerHeight;
console.log("Chiều cao vùng hiển thị: " + height + "px");
```

### Ví dụ với sự kiện thay đổi kích thước
```javascript
window.addEventListener('resize', function() {
    console.log("Chiều cao vùng hiển thị mới: " + window.innerHeight + "px");
});
```

## Giải thích
- **Điểm cần lưu ý**: `innerHeight` không bao gồm các yếu tố như thanh điều hướng hoặc thanh cuộn của trình duyệt. Do đó, nếu bạn muốn có chiều cao chính xác cho nội dung mà bạn có thể hiển thị, hãy chắc chắn kiểm tra các yếu tố khác có thể ảnh hưởng đến chiều cao.
- **Tránh việc sử dụng không cần thiết**: Gọi `window.innerHeight` nhiều lần trong một sự kiện `resize` có thể ảnh hưởng đến hiệu suất. Tốt nhất là bạn nên lưu trữ giá trị và chỉ gọi lại khi cần thiết.

## Tóm tắt một dòng
`innerHeight` trong JavaScript cho phép bạn lấy chiều cao của vùng hiển thị của cửa sổ trình duyệt, hữu ích cho việc phát triển giao diện người dùng đáp ứng.