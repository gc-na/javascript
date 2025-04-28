<!--
Meta Description: # JavaScript Comments: Hướng Dẫn Chi Tiết và Cách Sử Dụng ## Tóm Tắt Trong JavaScript, comment (nhận xét) được sử dụng để ghi chú và giải thích mã ngu...
Meta Keywords: comment, dòng, javascript, một, dụng
-->

# JavaScript Comments: Hướng Dẫn Chi Tiết và Cách Sử Dụng

## Tóm Tắt
Trong JavaScript, comment (nhận xét) được sử dụng để ghi chú và giải thích mã nguồn, giúp người lập trình dễ dàng hiểu và duy trì mã. Chúng không ảnh hưởng đến hoạt động của chương trình.

## Tài Liệu
Comment trong JavaScript có hai loại chính:

1. **Comment đơn dòng**: Bắt đầu bằng hai dấu gạch chéo (`//`). Tất cả nội dung phía sau dấu này trên cùng một dòng sẽ bị bỏ qua khi thực thi.
   - **Cú pháp**: 
     ```javascript
     // Đây là một comment đơn dòng
     ```

2. **Comment đa dòng**: Bắt đầu bằng `/*` và kết thúc bằng `*/`. Tất cả nội dung nằm giữa hai dấu này sẽ bị bỏ qua, cho phép ghi chú nhiều dòng.
   - **Cú pháp**:
     ```javascript
     /*
     Đây là một comment
     đa dòng
     */
     ```

### Mục Đích
Comment giúp lập trình viên:
- Ghi chú các lý do hoặc giải thích cho các đoạn mã cụ thể.
- Tạm thời vô hiệu hóa một số dòng mã mà không cần xóa chúng.
- Tăng cường khả năng đọc hiểu cho người khác hoặc cho chính mình trong tương lai.

## Ví Dụ
Dưới đây là một số ví dụ về cách sử dụng comment trong JavaScript:

### Ví dụ 1: Comment đơn dòng
```javascript
// Tính tổng của hai số
let a = 5; // Số thứ nhất
let b = 10; // Số thứ hai
let sum = a + b; // Tính tổng
console.log(sum); // In ra tổng
```

### Ví dụ 2: Comment đa dòng
```javascript
/*
Chương trình này tính toán
và in ra tổng của hai số
*/
let x = 7;
let y = 3;
let total = x + y;
console.log(total);
```

## Giải Thích
Khi sử dụng comment, lập trình viên cần lưu ý một số vấn đề:
- **Không sử dụng comment để giải thích mã rõ ràng**: Nếu mã của bạn cần nhiều comment để được hiểu, có thể bạn nên xem xét việc viết lại mã cho rõ ràng hơn.
- **Tránh sử dụng comment không cần thiết**: Sử dụng comment một cách hợp lý, chỉ cần thiết cho những phần mã phức tạp hoặc quan trọng.
- **Comment đa dòng không thể lồng vào nhau**: Nếu bạn cố gắng lồng các comment đa dòng, điều này sẽ gây ra lỗi cú pháp.

## Tóm Tắt Một Dòng
Comment trong JavaScript giúp lập trình viên ghi chú và giải thích mã, không ảnh hưởng đến hoạt động của chương trình.