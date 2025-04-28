<!--
Meta Description: # AggregateError trong JavaScript: Hiểu Rõ và Sử Dụng Hiệu Quả ## Tóm Tắt AggregateError là một loại lỗi trong JavaScript, được sử dụng để nhóm nhiều ...
Meta Keywords: lỗi, aggregateerror, nhiều, các, new
-->

# AggregateError trong JavaScript: Hiểu Rõ và Sử Dụng Hiệu Quả

## Tóm Tắt
AggregateError là một loại lỗi trong JavaScript, được sử dụng để nhóm nhiều lỗi lại với nhau, thường hữu ích trong các tình huống mà nhiều Promise có thể bị từ chối.

## Tài Liệu
### Mục Đích
AggregateError được giới thiệu trong ECMAScript 2021 (ES12) để quản lý nhiều lỗi đồng thời, cho phép lập trình viên xử lý các lỗi từ nhiều nguồn khác nhau một cách hiệu quả.

### Cách Sử Dụng
AggregateError có thể được khởi tạo bằng cách sử dụng từ khóa `new` và truyền vào một mảng các lỗi (Error). Đối tượng này có một thuộc tính `errors`, chứa danh sách các lỗi đã nhóm lại.

```javascript
const errors = [new Error('Lỗi 1'), new Error('Lỗi 2')];
const aggregateError = new AggregateError(errors, 'Đã xảy ra nhiều lỗi');
```

### Chi Tiết
- **Cú Pháp**: 
  ```javascript
  new AggregateError(errors: Error[], message?: string)
  ```
- **Thuộc Tính**:
  - `errors`: Mảng chứa các lỗi đã nhóm lại.
  - `message`: Chuỗi mô tả lỗi tổng quát.

## Ví Dụ
### Ví dụ 1: Khởi Tạo AggregateError
```javascript
try {
    throw new AggregateError([new Error('Lỗi A'), new Error('Lỗi B')], 'Có nhiều lỗi');
} catch (e) {
    console.log(e.message); // Có nhiều lỗi
    console.log(e.errors); // [Error: Lỗi A, Error: Lỗi B]
}
```

### Ví dụ 2: Sử Dụng Trong Promise
```javascript
async function fetchData() {
    const promises = [
        Promise.reject(new Error('Lỗi 1')),
        Promise.reject(new Error('Lỗi 2'))
    ];

    try {
        await Promise.all(promises);
    } catch (e) {
        if (e instanceof AggregateError) {
            console.log(e.errors); // Xuất ra danh sách các lỗi
        }
    }
}

fetchData();
```

## Giải Thích
### Các Lỗi Thông Thường
- **Bỏ Qua Xử Lý Lỗi**: Khi làm việc với nhiều Promise, nếu không xử lý AggregateError, bạn dễ dàng bỏ lỡ các lỗi quan trọng.
- **Sử Dụng Không Đúng Cách**: Đảm bảo rằng bạn truyền đúng định dạng khi khởi tạo AggregateError, nếu không sẽ dẫn đến lỗi không mong muốn.

### Điểm Cần Lưu Ý
- AggregateError là một phần quan trọng trong việc xử lý lỗi bất đồng bộ, giúp lập trình viên dễ dàng quản lý các lỗi phát sinh từ nhiều Promise.
- Đảm bảo rằng bạn kiểm tra loại lỗi để xử lý đúng cách khi làm việc với AggregateError.

## Tóm Tắt Một Dòng
AggregateError là một đối tượng trong JavaScript cho phép nhóm nhiều lỗi lại với nhau, hỗ trợ lập trình viên trong việc quản lý và xử lý lỗi từ các Promise.