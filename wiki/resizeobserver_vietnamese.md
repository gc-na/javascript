<!--
Meta Description: # ResizeObserver: Theo dõi sự thay đổi kích thước của phần tử trong JavaScript ## Tóm tắt ResizeObserver là một API trong JavaScript cho phép bạn theo...
Meta Keywords: theo, dõi, phần, một, resizeobserver
-->

# ResizeObserver: Theo dõi sự thay đổi kích thước của phần tử trong JavaScript

## Tóm tắt
ResizeObserver là một API trong JavaScript cho phép bạn theo dõi sự thay đổi kích thước của các phần tử DOM. Điều này rất hữu ích khi bạn cần thực hiện các hành động cụ thể khi kích thước của một phần tử thay đổi, như điều chỉnh bố cục hoặc cập nhật nội dung.

## Tài liệu

### Mục đích
ResizeObserver được thiết kế để cung cấp một phương thức hiệu quả cho việc theo dõi kích thước của các phần tử DOM mà không cần sử dụng các giải pháp tốn kém như việc kiểm tra kích thước bằng cách lặp vòng lặp hay sử dụng sự kiện cuộn.

### Cách sử dụng
Để sử dụng ResizeObserver, bạn cần tạo một đối tượng ResizeObserver và cung cấp một callback function sẽ được gọi mỗi khi kích thước của phần tử mà bạn đang theo dõi thay đổi. 

**Cú pháp:**
```javascript
const observer = new ResizeObserver(callback);
observer.observe(targetElement);
```

**Tham số:**
- `callback`: Hàm sẽ nhận các đối số là một danh sách các mục ResizeObserverEntry, mỗi mục chứa thông tin về phần tử đã thay đổi kích thước.
- `targetElement`: Phần tử DOM mà bạn muốn theo dõi.

### Chi tiết
1. **Tạo đối tượng ResizeObserver**: Bắt đầu bằng cách khởi tạo một đối tượng ResizeObserver với một hàm callback.
2. **Theo dõi phần tử**: Sử dụng phương thức `observe` để theo dõi kích thước của một phần tử cụ thể.
3. **Ngừng theo dõi**: Nếu bạn không còn cần theo dõi phần tử, bạn có thể sử dụng phương thức `unobserve` để ngừng theo dõi nó.
4. **Ngừng theo dõi tất cả**: Sử dụng `disconnect` để ngừng theo dõi tất cả các phần tử mà đối tượng ResizeObserver đang theo dõi.

## Ví dụ

### Ví dụ 1: Theo dõi kích thước của một phần tử
```javascript
const box = document.querySelector('.box');
const observer = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log('Kích thước thay đổi:', entry.contentRect.width, entry.contentRect.height);
    }
});

observer.observe(box);
```

### Ví dụ 2: Ngừng theo dõi
```javascript
observer.unobserve(box); // Ngừng theo dõi phần tử box
```

### Ví dụ 3: Ngừng theo dõi tất cả
```javascript
observer.disconnect(); // Ngừng theo dõi tất cả các phần tử
```

## Giải thích
- **Hạn chế**: ResizeObserver không được hỗ trợ trên tất cả các trình duyệt. Bạn nên kiểm tra tính tương thích trước khi sử dụng.
- **Callback được gọi nhiều lần**: Nếu nhiều thay đổi kích thước xảy ra trong một khoảng thời gian ngắn, callback có thể được gọi nhiều lần. Bạn có thể cần phải tối ưu hóa để tránh thực hiện quá nhiều công việc trong callback.
- **Hiệu suất**: ResizeObserver không phải là giải pháp cho tất cả các tình huống. Nếu bạn chỉ cần theo dõi một số thay đổi kích thước đơn giản, hãy xem xét các cách tiếp cận khác để tránh làm giảm hiệu suất.

## Tóm tắt một dòng
ResizeObserver là một API JavaScript cho phép theo dõi sự thay đổi kích thước của các phần tử DOM, giúp tối ưu hóa trải nghiệm người dùng.