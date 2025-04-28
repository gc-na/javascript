<!--
Meta Description: # Phạm vi (Range) trong JavaScript: Khái Niệm và Ứng Dụng ## Tóm tắt Phạm vi (Range) trong JavaScript là một khái niệm quan trọng liên quan đến việc x...
Meta Keywords: biến, phạm, trong, được, khối
-->

# Phạm vi (Range) trong JavaScript: Khái Niệm và Ứng Dụng

## Tóm tắt
Phạm vi (Range) trong JavaScript là một khái niệm quan trọng liên quan đến việc xác định giới hạn của các biến và chức năng trong một chương trình. Nó giúp xác định nơi mà một biến có thể được truy cập và sử dụng, ảnh hưởng đến tính chính xác và hiệu suất của mã.

## Tài liệu
### Mục đích
Phạm vi trong JavaScript xác định cách thức mà biến được truy cập và sử dụng trong các khối mã khác nhau. Có ba loại phạm vi chính trong JavaScript: toàn cầu (global), cục bộ (local), và khối (block).

### Cách sử dụng
- **Phạm vi toàn cầu**: Biến được định nghĩa bên ngoài bất kỳ hàm nào có thể được truy cập từ bất kỳ đâu trong mã.
- **Phạm vi cục bộ**: Biến được định nghĩa trong một hàm chỉ có thể được truy cập từ bên trong hàm đó.
- **Phạm vi khối**: Biến được định nghĩa bằng từ khóa `let` hoặc `const` trong một khối mã (như `if`, `for`, hoặc `{}`) chỉ có thể được truy cập bên trong khối đó.

### Chi tiết
- Khi một biến được khai báo bằng từ khóa `var`, nó có phạm vi toàn cầu hoặc cục bộ tùy thuộc vào vị trí khai báo.
- Từ khóa `let` và `const` cung cấp phạm vi khối, có nghĩa là biến sẽ không tồn tại bên ngoài khối mà nó được khai báo.
- Sự hiểu biết về phạm vi giúp tránh xung đột tên biến và tăng tính bảo trì của mã.

## Ví dụ
### Ví dụ 1: Phạm vi toàn cầu
```javascript
var globalVar = "Tôi là biến toàn cầu";

function checkGlobal() {
    console.log(globalVar); // In ra: Tôi là biến toàn cầu
}

checkGlobal();
```

### Ví dụ 2: Phạm vi cục bộ
```javascript
function localScope() {
    var localVar = "Tôi là biến cục bộ";
    console.log(localVar); // In ra: Tôi là biến cục bộ
}

localScope();
// console.log(localVar); // Lỗi: localVar không được định nghĩa
```

### Ví dụ 3: Phạm vi khối
```javascript
if (true) {
    let blockVar = "Tôi là biến khối";
    console.log(blockVar); // In ra: Tôi là biến khối
}

// console.log(blockVar); // Lỗi: blockVar không được định nghĩa
```

## Giải thích
Một số điểm cần lưu ý về phạm vi trong JavaScript:
- Biến toàn cầu có thể dẫn đến xung đột nếu nhiều hàm hoặc thư viện sử dụng cùng tên biến.
- Sử dụng `let` và `const` thay vì `var` có thể giúp tránh một số lỗi phổ biến liên quan đến phạm vi.
- Thay đổi giá trị của biến trong phạm vi cục bộ không ảnh hưởng đến biến cùng tên trong phạm vi toàn cầu.

## Tóm tắt một dòng
Phạm vi (Range) trong JavaScript xác định nơi mà biến có thể được truy cập, ảnh hưởng đến cách thức tổ chức và bảo trì mã.