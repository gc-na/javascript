<!--
Meta Description: # Lỗi trong JavaScript: Tìm hiểu về Đối tượng Error ## Tóm tắt Đối tượng Error trong JavaScript được sử dụng để xử lý và quản lý các lỗi phát sinh tro...
Meta Keywords: lỗi, error, đối, tượng, dụng
-->

# Lỗi trong JavaScript: Tìm hiểu về Đối tượng Error

## Tóm tắt
Đối tượng Error trong JavaScript được sử dụng để xử lý và quản lý các lỗi phát sinh trong quá trình thực thi mã. Nó cung cấp một cách thức linh hoạt để phát hiện, thông báo và xử lý các tình huống không mong muốn.

## Tài liệu
### Mục đích
Đối tượng Error cho phép lập trình viên tạo ra các thông báo lỗi tùy chỉnh và theo dõi các lỗi xảy ra trong ứng dụng của họ. Nó giúp dễ dàng xác định và xử lý các vấn đề trong mã nguồn.

### Cách sử dụng
Để tạo một đối tượng Error, bạn chỉ cần gọi hàm `Error` và có thể truyền vào một thông điệp mô tả lỗi:

```javascript
const myError = new Error('Đây là một lỗi tùy chỉnh.');
```

Đối tượng Error có các thuộc tính chính như:
- `name`: Tên của lỗi.
- `message`: Thông điệp mô tả lỗi.
- `stack`: Chuỗi chứa thông tin về ngăn xếp, giúp xác định vị trí xảy ra lỗi.

### Ví dụ
Dưới đây là một số ví dụ đơn giản về cách sử dụng đối tượng Error:

#### Ví dụ 1: Tạo lỗi đơn giản
```javascript
try {
    throw new Error('Có lỗi xảy ra!');
} catch (e) {
    console.error(e.name);    // "Error"
    console.error(e.message);  // "Có lỗi xảy ra!"
}
```

#### Ví dụ 2: Lỗi tùy chỉnh
```javascript
function divide(a, b) {
    if (b === 0) {
        throw new Error('Không thể chia cho 0.');
    }
    return a / b;
}

try {
    divide(10, 0);
} catch (e) {
    console.error(e.message);  // "Không thể chia cho 0."
}
```

## Giải thích
Khi sử dụng đối tượng Error, lập trình viên cần chú ý đến một số vấn đề sau:
- **Không ném lỗi vô hạn**: Đảm bảo rằng không có vòng lặp vô hạn khi ném lỗi, điều này có thể dẫn đến việc ứng dụng bị treo.
- **Xử lý lỗi**: Luôn sử dụng `try...catch` để xử lý lỗi và tránh làm ngưng trệ ứng dụng.
- **Thông điệp rõ ràng**: Cung cấp thông điệp lỗi rõ ràng và cụ thể để dễ dàng xác định nguyên nhân.

## Tóm tắt một dòng
Đối tượng Error trong JavaScript giúp quản lý và xử lý các lỗi trong mã một cách hiệu quả và linh hoạt.