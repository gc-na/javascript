<!--
Meta Description: # setTimeout trong JavaScript: Cách sử dụng và ví dụ ## Tóm tắt `setTimeout` là một hàm trong JavaScript cho phép bạn thực hiện một đoạn mã sau một kh...
Meta Keywords: một, hàm, settimeout, thực, thời
-->

# setTimeout trong JavaScript: Cách sử dụng và ví dụ

## Tóm tắt
`setTimeout` là một hàm trong JavaScript cho phép bạn thực hiện một đoạn mã sau một khoảng thời gian nhất định. Đây là một công cụ hữu ích để tạo ra độ trễ trong thực thi mã, giúp điều khiển luồng của ứng dụng.

## Tài liệu
Hàm `setTimeout` được sử dụng để lập lịch thực thi một hàm hoặc một đoạn mã sau một khoảng thời gian cụ thể. Cú pháp của hàm như sau:

```javascript
setTimeout(function, delay, param1, param2, ...)
```

### Tham số:
- **function**: Hàm hoặc đoạn mã cần thực thi.
- **delay**: Thời gian trễ (tính bằng mili giây) trước khi thực thi hàm.
- **param1, param2, ...**: Các tham số tùy chọn sẽ được truyền vào hàm khi nó được gọi.

### Ví dụ:
```javascript
setTimeout(() => {
    console.log("Hello, world!");
}, 2000); // In ra "Hello, world!" sau 2 giây
```

## Giải thích
Mặc dù `setTimeout` là một công cụ mạnh mẽ, nhưng có một số điều cần lưu ý khi sử dụng:

1. **Thời gian không chính xác**: Thời gian trễ không đảm bảo chính xác. Nếu có nhiều tác vụ đang chạy, thời gian thực thi có thể bị trì hoãn.
2. **Hàm không được gọi**: Nếu bạn quên truyền hàm vào `setTimeout`, hoặc truyền một tham số không phải là hàm, mã sẽ không hoạt động như mong đợi.
3. **Hủy bỏ**: Bạn có thể hủy một `setTimeout` bằng cách sử dụng `clearTimeout` với ID trả về từ `setTimeout`.

### Ví dụ hủy bỏ:
```javascript
const timeoutId = setTimeout(() => {
    console.log("This will not run");
}, 3000);

clearTimeout(timeoutId); // Hủy bỏ hàm trên
```

## Tóm tắt một dòng
`setTimeout` trong JavaScript cho phép lập lịch thực thi một hàm sau một khoảng thời gian nhất định, giúp điều khiển luồng thực thi của mã.