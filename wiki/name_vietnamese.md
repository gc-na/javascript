<!--
Meta Description: # Tên (name) trong JavaScript: Hiểu Biết Cơ Bản ## Tóm Tắt Trong JavaScript, "name" thường được sử dụng để xác định danh tính của một hàm, biến, hoặc ...
Meta Keywords: trong, tên, javascript, một, định
-->

# Tên (name) trong JavaScript: Hiểu Biết Cơ Bản

## Tóm Tắt
Trong JavaScript, "name" thường được sử dụng để xác định danh tính của một hàm, biến, hoặc đối tượng. Nó giúp lập trình viên dễ dàng quản lý và truy xuất các thành phần trong mã nguồn.

## Tài Liệu
Tên (name) trong JavaScript không chỉ đơn thuần là một chuỗi ký tự; nó còn mang lại ý nghĩa trong việc xác định và phân loại các thành phần trong mã. Mỗi hàm và biến có thể được gán một tên để phục vụ cho việc gọi và sử dụng lại. Việc đặt tên hợp lý giúp tăng khả năng đọc hiểu và bảo trì mã.

### Mục đích
- Giúp xác định rõ ràng các thành phần trong mã.
- Tăng tính khả dụng và dễ hiểu cho các lập trình viên khác (hoặc cho chính bạn trong tương lai).

### Cách sử dụng
Khi bạn định nghĩa một hàm hoặc biến, bạn sẽ gán cho nó một tên. Ví dụ:
```javascript
function myFunction() {
    // code here
}
```
Trong ví dụ trên, "myFunction" là tên của hàm.

## Ví Dụ
### Ví dụ 1: Định nghĩa hàm
```javascript
function greet() {
    console.log("Hello, World!");
}
greet(); // Kết quả: Hello, World!
```

### Ví dụ 2: Định nghĩa biến
```javascript
let userName = "John Doe";
console.log(userName); // Kết quả: John Doe
```

### Ví dụ 3: Sử dụng thuộc tính name trong hàm
```javascript
function myFunction() {
    console.log(myFunction.name); // Kết quả: myFunction
}
myFunction();
```

## Giải Thích
Một số điểm cần lưu ý khi sử dụng tên trong JavaScript:
- Tên phải tuân theo quy tắc đặt tên của JavaScript: Bắt đầu bằng chữ cái, dấu gạch dưới (_) hoặc dấu đô la ($). Không được bắt đầu bằng số.
- Tên không được trùng với các từ khóa của JavaScript (như `if`, `for`, `while`, v.v.).
- Có thể dùng các ký tự đặc biệt trong tên nhưng không nên quá phức tạp để dễ hiểu.

## Tóm Tắt Một Dòng
Tên (name) trong JavaScript là một thành phần quan trọng giúp xác định và quản lý các phần của mã, từ hàm đến biến, nhằm tăng cường khả năng đọc hiểu và bảo trì mã.