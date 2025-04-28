<!--
Meta Description: # Hàm trong JavaScript: Tất cả những gì bạn cần biết ## Tóm tắt Hàm trong JavaScript là một khối mã có thể gọi lại để thực hiện một nhiệm vụ cụ thể. C...
Meta Keywords: hàm, thể, trong, javascript, dụng
-->

# Hàm trong JavaScript: Tất cả những gì bạn cần biết

## Tóm tắt
Hàm trong JavaScript là một khối mã có thể gọi lại để thực hiện một nhiệm vụ cụ thể. Chúng giúp tổ chức mã, tái sử dụng và quản lý logic trong ứng dụng.

## Tài liệu
Hàm là một trong những khái niệm cơ bản và quan trọng nhất trong JavaScript. Chúng được sử dụng để nhóm các câu lệnh lại với nhau nhằm thực hiện một nhiệm vụ cụ thể. Hàm có thể nhận tham số đầu vào và trả về giá trị đầu ra. Cú pháp cơ bản của một hàm trong JavaScript như sau:

```javascript
function tenHam(thamSo1, thamSo2) {
    // Các câu lệnh ở đây
    return giaTri; // Giá trị trả về
}
```

### Mục đích
Hàm giúp cải thiện khả năng đọc và bảo trì mã. Bằng cách chia nhỏ mã thành các phần nhỏ hơn và có thể quản lý, lập trình viên có thể dễ dàng phát hiện và sửa lỗi.

### Cách sử dụng
- **Khai báo hàm**: Sử dụng từ khóa `function` để định nghĩa hàm.
- **Gọi hàm**: Sử dụng tên hàm kèm theo dấu ngoặc đơn để thực thi.

### Chi tiết
- **Hàm ẩn danh**: Có thể được định nghĩa mà không có tên và thường được sử dụng như một hàm callback.
- **Hàm mũi tên**: Cú pháp ngắn gọn hơn cho việc khai báo hàm, được giới thiệu trong ES6:

```javascript
const tenHam = (thamSo1, thamSo2) => {
    // Các câu lệnh ở đây
    return giaTri;
};
```

- **Hàm trả về**: Hàm có thể trả về giá trị bằng cách sử dụng từ khóa `return`. Nếu không có `return`, hàm sẽ trả về `undefined`.

## Ví dụ
### Ví dụ 1: Hàm cơ bản
```javascript
function cong(a, b) {
    return a + b;
}

console.log(cong(5, 3)); // Kết quả: 8
```

### Ví dụ 2: Hàm mũi tên
```javascript
const tru = (a, b) => a - b;

console.log(tru(10, 4)); // Kết quả: 6
```

### Ví dụ 3: Hàm ẩn danh
```javascript
setTimeout(function() {
    console.log("Đã trễ 1 giây");
}, 1000);
```

## Giải thích
- **Lỗi phổ biến**: Một số lập trình viên mới có thể quên gọi hàm hoặc sử dụng tên hàm không chính xác.
- **Scope**: Biến được khai báo trong hàm không thể truy cập từ bên ngoài hàm đó.
- **Tham số và đối số**: Hàm có thể nhận bất kỳ số lượng tham số nào, nhưng có thể được gọi mà không truyền đối số nào.

## Tóm tắt một dòng
Hàm trong JavaScript là các khối mã giúp tổ chức, tái sử dụng và thực hiện các tác vụ cụ thể trong lập trình.