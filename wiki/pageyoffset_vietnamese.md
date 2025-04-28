<!--
Meta Description: # pageYOffset trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt `pageYOffset` là một thuộc tính trong JavaScript cho phép bạn lấy giá trị vị tr...
Meta Keywords: pageyoffset, tính, cuộn, trong, một
-->

# pageYOffset trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
`pageYOffset` là một thuộc tính trong JavaScript cho phép bạn lấy giá trị vị trí cuộn theo chiều dọc của tài liệu trong cửa sổ trình duyệt. Nó hữu ích để xác định vị trí hiện tại của người dùng trên trang web.

## Tài liệu
### Mục đích
`pageYOffset` cung cấp thông tin về khoảng cách mà người dùng đã cuộn xuống từ đầu trang web. Thuộc tính này trả về một giá trị số dương và có thể được sử dụng trong nhiều tình huống như tạo hiệu ứng cuộn, xác định vị trí của các phần tử, và nhiều tính năng tương tác khác.

### Cách sử dụng
`pageYOffset` là một thuộc tính của đối tượng `window`. Để truy cập giá trị này, bạn chỉ cần gọi `window.pageYOffset`. Không cần thêm bất kỳ tham số nào.

### Chi tiết
- **Kiểu trả về**: `Number`
- **Giá trị trả về**: Khoảng cách tính bằng pixel mà người dùng đã cuộn theo chiều dọc.
- **Trình duyệt hỗ trợ**: Hầu hết các trình duyệt hiện đại đều hỗ trợ `pageYOffset`.

## Ví dụ
Dưới đây là một số ví dụ cơ bản về cách sử dụng `pageYOffset`:

### Ví dụ 1: Lấy giá trị `pageYOffset`
```javascript
window.addEventListener('scroll', function() {
    console.log('Vị trí cuộn hiện tại: ' + window.pageYOffset + 'px');
});
```

### Ví dụ 2: Tạo hiệu ứng cuộn khi cuộn xuống
```javascript
window.addEventListener('scroll', function() {
    if (window.pageYOffset > 100) {
        document.body.style.backgroundColor = 'lightblue';
    } else {
        document.body.style.backgroundColor = 'white';
    }
});
```

## Giải thích
### Những điều cần lưu ý
- **Khác biệt với `scrollY`**: `pageYOffset` tương đương với thuộc tính `scrollY`. Cả hai đều trả về vị trí cuộn theo chiều dọc, nhưng `scrollY` là thuộc tính của đối tượng `window` trong khi `pageYOffset` có thể được sử dụng như một thuộc tính toàn cục.
- **Trình duyệt cũ**: Đối với một số trình duyệt cũ, có thể cần kiểm tra tính khả dụng của `pageYOffset` trước khi sử dụng.
- **Hiệu suất**: Khi sử dụng trong các sự kiện cuộn, hãy cẩn thận với hiệu suất, vì việc gọi quá nhiều lần có thể làm giảm hiệu suất trang web.

## Tóm tắt một dòng
`pageYOffset` là thuộc tính JavaScript giúp xác định vị trí cuộn theo chiều dọc của tài liệu trong cửa sổ trình duyệt.