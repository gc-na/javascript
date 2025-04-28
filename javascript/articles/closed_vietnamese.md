<!--
Meta Description: # Đóng (Closed) trong JavaScript: Tính năng và Cách Sử Dụng ## Tóm tắt "Đóng" là một khái niệm trong JavaScript liên quan đến việc bảo vệ các biến khỏ...
Meta Keywords: biến, hàm, trong, một, các
-->

# Đóng (Closed) trong JavaScript: Tính năng và Cách Sử Dụng

## Tóm tắt
"Đóng" là một khái niệm trong JavaScript liên quan đến việc bảo vệ các biến khỏi việc truy cập từ bên ngoài, thường được sử dụng trong các hàm và closures.

## Tài liệu
Khái niệm "đóng" (closure) trong JavaScript cho phép một hàm truy cập đến các biến trong phạm vi (scope) của hàm cha ngay cả khi hàm cha đã hoàn thành. Điều này làm cho closures trở thành một công cụ mạnh mẽ để tạo ra các hàm với trạng thái riêng biệt.

### Mục đích
- Bảo vệ biến khỏi việc truy cập từ bên ngoài.
- Tạo ra các hàm có khả năng duy trì trạng thái.

### Cách sử dụng
Để tạo một closure, bạn chỉ cần định nghĩa một hàm bên trong một hàm khác. Các biến trong hàm cha sẽ vẫn có thể được truy cập từ hàm con.

## Ví dụ
Dưới đây là một vài ví dụ đơn giản về cách sử dụng closures trong JavaScript:

### Ví dụ 1: Tạo một hàm đếm
```javascript
function createCounter() {
    let count = 0; // Biến 'count' không thể truy cập từ bên ngoài
    return function() {
        count++; // Tăng giá trị của 'count'
        return count;
    };
}

const counter = createCounter();
console.log(counter()); // In ra 1
console.log(counter()); // In ra 2
```

### Ví dụ 2: Bảo vệ biến
```javascript
function secret() {
    let privateVariable = "Tôi là bí mật"; // Biến riêng tư
    return function() {
        return privateVariable; // Trả về biến riêng tư
    };
}

const getSecret = secret();
console.log(getSecret()); // In ra "Tôi là bí mật"
```

## Giải thích
Khi sử dụng closures, có một số điểm cần chú ý:
- **Bộ nhớ**: Biến trong closure sẽ không bị thu hồi bởi garbage collector cho đến khi không còn tham chiếu nào đến closure đó.
- **Hiệu suất**: Sử dụng closures có thể dẫn đến giảm hiệu suất nếu không được tối ưu, do việc giữ nhiều biến trong bộ nhớ.

### Những cạm bẫy thường gặp
- **Tham chiếu không mong muốn**: Nếu bạn không sử dụng closures cẩn thận, có thể dẫn đến việc biến bị thay đổi không mong muốn từ các hàm bên ngoài.
- **Hiểu rõ về phạm vi**: Người mới học có thể nhầm lẫn giữa phạm vi của biến trong các hàm khác nhau, dẫn đến lỗi không thể truy cập biến.

## Tóm tắt một dòng
"Đóng" trong JavaScript cho phép các hàm truy cập biến của hàm cha, tạo ra trạng thái riêng biệt và bảo vệ biến khỏi việc truy cập từ bên ngoài.