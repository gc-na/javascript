<!--
Meta Description: # visualViewport: Hiểu Biết và Ứng Dụng trong JavaScript ## Tóm tắt `visualViewport` là một API trong JavaScript cho phép lập trình viên truy cập và t...
Meta Keywords: viewport, visualviewport, của, trình, các
-->

# visualViewport: Hiểu Biết và Ứng Dụng trong JavaScript

## Tóm tắt
`visualViewport` là một API trong JavaScript cho phép lập trình viên truy cập và tương tác với viewport hiển thị của trình duyệt, bao gồm các thông tin như kích thước và vị trí của viewport, từ đó cải thiện trải nghiệm người dùng trên các thiết bị di động.

## Tài liệu
### Mục đích
`visualViewport` cung cấp một giao diện để truy cập thông tin về viewport đang hiển thị, giúp lập trình viên có thể điều chỉnh bố cục và hành vi của giao diện người dùng (UI) dựa trên kích thước và vị trí của nó.

### Cách sử dụng
Để sử dụng `visualViewport`, bạn chỉ cần truy cập nó qua thuộc tính toàn cục `window.visualViewport`. Dưới đây là các thuộc tính chính mà bạn có thể sử dụng:

- **`width`**: Chiều rộng của viewport trong pixel.
- **`height`**: Chiều cao của viewport trong pixel.
- **`offsetLeft`**: Khoảng cách từ bên trái của viewport đến bên trái của cửa sổ trình duyệt.
- **`offsetTop`**: Khoảng cách từ trên cùng của viewport đến trên cùng của cửa sổ trình duyệt.
- **`scale`**: Tỷ lệ phóng lớn của viewport, cho phép bạn biết liệu có zoom hay không.
  
### Chi tiết
`visualViewport` cũng hỗ trợ các sự kiện mà bạn có thể lắng nghe để nhận thông tin khi viewport thay đổi:

- **`resize`**: Khi kích thước của viewport thay đổi.
- **`scroll`**: Khi viewport cuộn.
  
Để sử dụng các sự kiện này, bạn có thể thêm các hàm xử lý sự kiện như sau:

```javascript
window.visualViewport.addEventListener('resize', () => {
    console.log('Viewport đã thay đổi kích thước:', window.visualViewport.width, window.visualViewport.height);
});
```

## Ví dụ
### Cách lấy kích thước viewport
```javascript
const viewportWidth = window.visualViewport.width;
const viewportHeight = window.visualViewport.height;
console.log(`Chiều rộng viewport: ${viewportWidth}, Chiều cao viewport: ${viewportHeight}`);
```

### Lắng nghe sự kiện thay đổi kích thước
```javascript
window.visualViewport.addEventListener('resize', () => {
    console.log('Kích thước viewport đã thay đổi!');
});
```

## Giải thích
Mặc dù `visualViewport` rất hữu ích, nhưng có một số điểm cần lưu ý:

- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ `visualViewport`. Hãy kiểm tra khả năng tương thích trước khi sử dụng.
- **Thay đổi kích thước**: Khi sử dụng sự kiện `resize`, hãy cẩn thận với việc thực thi mã quá nhiều lần. Bạn có thể cần phải tối ưu hóa mã của mình để giảm thiểu hiệu suất.

## Tóm tắt một dòng
`visualViewport` là một API trong JavaScript cho phép lập trình viên truy cập và xử lý thông tin về viewport hiển thị, cải thiện trải nghiệm người dùng trên các thiết bị di động.