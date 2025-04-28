<!--
Meta Description: # Lập Lịch Trình (Scheduler) Trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt Lập lịch trình trong JavaScript là một phương pháp mạnh mẽ cho phép người...
Meta Keywords: dụng, lập, trình, một, hàm
-->

# Lập Lịch Trình (Scheduler) Trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
Lập lịch trình trong JavaScript là một phương pháp mạnh mẽ cho phép người lập trình quản lý và thực thi các tác vụ theo thời gian hoặc theo chu kỳ nhất định, giúp tối ưu hóa hiệu suất và trải nghiệm người dùng.

## Tài Liệu
### Mục Đích
Lập lịch trình giúp thực hiện các tác vụ không đồng bộ, cho phép lập trình viên quản lý thời gian thực thi của các hàm, từ đó cải thiện hiệu suất ứng dụng và trải nghiệm người dùng. Điều này đặc biệt hữu ích trong các ứng dụng web, nơi mà việc xử lý nhiều tác vụ đồng thời là cần thiết.

### Cách Sử Dụng
Trong JavaScript, có một số phương thức lập lịch trình phổ biến:

- **`setTimeout()`**: Gọi một hàm sau một khoảng thời gian nhất định.
- **`setInterval()`**: Gọi một hàm sau mỗi khoảng thời gian xác định.
- **`requestAnimationFrame()`**: Lập lịch cho việc cập nhật hoạt ảnh trong trình duyệt.

### Chi Tiết
- **`setTimeout(callback, delay)`**: 
  - Tham số `callback` là hàm sẽ được thực thi sau `delay` (thời gian tính bằng mili giây).
  - Trả về một ID mà bạn có thể sử dụng với `clearTimeout()` để hủy lời gọi nếu cần.

- **`setInterval(callback, interval)`**: 
  - Tương tự như `setTimeout()`, nhưng sẽ thực hiện hàm `callback` lặp lại sau mỗi `interval`.
  - Trả về một ID mà bạn có thể sử dụng với `clearInterval()` để dừng việc thực hiện.

- **`requestAnimationFrame(callback)`**: 
  - Được sử dụng để lập lịch cho các cập nhật hoạt ảnh, giúp cải thiện hiệu suất bằng cách đồng bộ hóa với tốc độ làm mới của màn hình.
  - Nó không trả về một ID có thể hủy bỏ như hai phương thức trên, nhưng bạn có thể gọi lại `requestAnimationFrame()` trong hàm `callback` để tiếp tục lập lịch.

## Ví Dụ
### Sử Dụng `setTimeout()`
```javascript
setTimeout(() => {
    console.log('Đây là thông báo sau 2 giây');
}, 2000);
```

### Sử Dụng `setInterval()`
```javascript
const intervalId = setInterval(() => {
    console.log('Đây là thông báo lặp lại mỗi 1 giây');
}, 1000);

// Dừng lặp lại sau 5 giây
setTimeout(() => {
    clearInterval(intervalId);
    console.log('Đã dừng thông báo');
}, 5000);
```

### Sử Dụng `requestAnimationFrame()`
```javascript
let start = null;
function animate(timestamp) {
    if (!start) start = timestamp;
    const progress = timestamp - start;

    // Cập nhật trạng thái hoạt ảnh ở đây

    if (progress < 2000) {
        requestAnimationFrame(animate);
    }
}
requestAnimationFrame(animate);
```

## Giải Thích
Khi sử dụng `setTimeout()` và `setInterval()`, có thể xảy ra hiện tượng "độ trễ" nếu các tác vụ được thực hiện lâu hơn thời gian đã chỉ định. Điều này có thể dẫn đến việc gọi hàm không đúng thời điểm mong muốn. Ngoài ra, việc sử dụng `setInterval()` có thể dẫn đến việc xảy ra nhiều lần gọi hàm nếu hàm không hoàn thành trước khi lần gọi tiếp theo diễn ra.

Với `requestAnimationFrame()`, bạn nên nhớ rằng nó chỉ hoạt động khi tab trình duyệt đang mở và không bị tạm dừng, do đó nó không tiêu tốn tài nguyên khi người dùng không nhìn vào trang.

## Tóm Tắt Một Dòng
Lập lịch trình trong JavaScript cho phép quản lý và tối ưu hóa các tác vụ không đồng bộ, giúp cải thiện hiệu suất và trải nghiệm người dùng.