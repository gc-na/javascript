<!--
Meta Description: # globalThis trong JavaScript: Khám Phá Biến Toàn Cục Mới ## Tóm tắt `globalThis` là một biến toàn cục trong JavaScript, cung cấp một cách tiếp cận nh...
Meta Keywords: globalthis, toàn, cục, trong, javascript
-->

# globalThis trong JavaScript: Khám Phá Biến Toàn Cục Mới

## Tóm tắt
`globalThis` là một biến toàn cục trong JavaScript, cung cấp một cách tiếp cận nhất quán để truy cập đối tượng toàn cục bất kể môi trường thực thi, bao gồm trình duyệt và Node.js.

## Tài liệu
### Mục đích
`globalThis` được giới thiệu trong ECMAScript 2020 (ES11) như một cách để truy cập đối tượng toàn cục mà không cần quan tâm đến môi trường thực thi. Điều này giúp lập trình viên dễ dàng viết mã có thể chạy trên cả trình duyệt và Node.js mà không cần phải kiểm tra loại môi trường.

### Cách sử dụng
`globalThis` có thể được sử dụng bất cứ nơi nào trong mã JavaScript để truy cập các thuộc tính hoặc phương thức của đối tượng toàn cục. 

```javascript
console.log(globalThis); // In ra đối tượng toàn cục
```

### Chi tiết
- Trong trình duyệt, `globalThis` tương đương với `window`.
- Trong Node.js, `globalThis` tương đương với `global`.
- `globalThis` có thể được sử dụng để xác định các biến toàn cục, định nghĩa hàm hoặc truy cập các phương thức mà không cần biết chính xác môi trường mà mã đang chạy.

## Ví dụ
### Ví dụ cơ bản
```javascript
// Truy cập thuộc tính toàn cục
globalThis.myGlobalVar = 42;
console.log(globalThis.myGlobalVar); // Kết quả: 42

// Định nghĩa hàm toàn cục
globalThis.myGlobalFunction = function() {
    return "Hello from global!";
};
console.log(globalThis.myGlobalFunction()); // Kết quả: "Hello from global!"
```

### Ví dụ trong môi trường Node.js
```javascript
// Sử dụng globalThis trong Node.js
console.log(globalThis === global); // Kết quả: true
```

## Giải thích
### Những cạm bẫy thường gặp
- Mặc dù `globalThis` hoạt động trong cả trình duyệt và Node.js, nhưng việc lạm dụng biến toàn cục có thể dẫn đến xung đột tên và khó khăn trong việc quản lý mã. Lập trình viên nên hạn chế việc tạo ra quá nhiều biến toàn cục.
- Một số môi trường có thể không hỗ trợ `globalThis` nếu họ sử dụng phiên bản JavaScript cũ hơn. Đảm bảo kiểm tra tính tương thích của trình duyệt hoặc môi trường thực thi.

### Ghi chú bổ sung
`globalThis` là một phần quan trọng trong việc phát triển mã JavaScript hiện đại, giúp đơn giản hóa việc truy cập đối tượng toàn cục và làm cho mã dễ đọc hơn. 

## Tóm tắt một dòng
`globalThis` là cách duy nhất và đồng nhất để truy cập đối tượng toàn cục trong JavaScript, bất kể môi trường thực thi là gì.