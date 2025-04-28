<!--
Meta Description: # Lệnh `prompt` trong JavaScript: Hướng dẫn chi tiết và cách sử dụng ## Tóm tắt Lệnh `prompt` trong JavaScript là một hàm cho phép hiển thị một hộp th...
Meta Keywords: prompt, một, người, dùng, nhập
-->

# Lệnh `prompt` trong JavaScript: Hướng dẫn chi tiết và cách sử dụng

## Tóm tắt
Lệnh `prompt` trong JavaScript là một hàm cho phép hiển thị một hộp thoại để người dùng nhập dữ liệu. Đây là công cụ hữu ích cho việc thu thập thông tin từ người dùng trong các ứng dụng web.

## Tài liệu
### Mục đích
Hàm `prompt` được sử dụng để yêu cầu người dùng nhập một giá trị. Hộp thoại này sẽ hiển thị một thông điệp tùy chỉnh và có thể được sử dụng để thu thập dữ liệu như tên, số điện thoại, hoặc bất kỳ thông tin nào khác mà bạn cần.

### Cú pháp
```javascript
let userInput = prompt(message, defaultInput);
```

- **message** (tùy chọn): Một chuỗi thông điệp sẽ được hiển thị trong hộp thoại để hướng dẫn người dùng.
- **defaultInput** (tùy chọn): Một giá trị chuỗi mặc định sẽ được hiển thị trong trường nhập liệu, nếu không có gì được nhập.

### Trả về
Hàm `prompt` trả về giá trị mà người dùng đã nhập vào. Nếu người dùng nhấn "Cancel", hàm sẽ trả về `null`.

## Ví dụ
### Ví dụ Cơ Bản
```javascript
let name = prompt("Nhập tên của bạn:", "Tên của bạn");
alert("Xin chào, " + name);
```
Trong ví dụ này, một hộp thoại sẽ xuất hiện yêu cầu người dùng nhập tên của họ, và sau đó hiển thị thông báo chào mừng.

### Ví dụ với giá trị mặc định
```javascript
let age = prompt("Nhập tuổi của bạn:", "18");
console.log("Tuổi của bạn là: " + age);
```
Hộp thoại sẽ hiển thị tuổi mặc định là 18, và sau đó in ra giá trị tuổi người dùng nhập vào.

## Giải thích
### Những điều cần lưu ý
- **Chỉ định kiểu dữ liệu**: Giá trị trả về từ `prompt` luôn là một chuỗi. Nếu cần, bạn phải chuyển đổi nó sang kiểu dữ liệu khác (ví dụ: số nguyên).
- **Trải nghiệm người dùng**: Hộp thoại `prompt` có thể gây gián đoạn trải nghiệm người dùng, vì vậy nên sử dụng nó cẩn thận và chỉ khi thật sự cần thiết.
- **Trình duyệt**: Một số trình duyệt có thể không hỗ trợ hoặc không hiển thị hộp thoại `prompt` theo cách giống nhau, do đó, cần kiểm tra tính tương thích.

## Tóm tắt một câu
Hàm `prompt` trong JavaScript cho phép thu thập dữ liệu từ người dùng thông qua một hộp thoại nhập liệu.