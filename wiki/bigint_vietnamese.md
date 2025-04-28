<!--
Meta Description: # BigInt trong JavaScript: Kiểu Dữ Liệu Số Lớn ## Tóm tắt BigInt là một kiểu dữ liệu trong JavaScript cho phép bạn làm việc với các số nguyên lớn hơn ...
Meta Keywords: bigint, các, với, number, javascript
-->

# BigInt trong JavaScript: Kiểu Dữ Liệu Số Lớn

## Tóm tắt
BigInt là một kiểu dữ liệu trong JavaScript cho phép bạn làm việc với các số nguyên lớn hơn giới hạn của kiểu Number truyền thống. BigInt rất hữu ích khi bạn cần xử lý các giá trị số lớn mà không bị mất dữ liệu do tràn số.

## Tài liệu
BigInt được giới thiệu trong ECMAScript 2020 (ES11). Kiểu dữ liệu này cho phép các nhà phát triển lưu trữ và thao tác với các số nguyên lớn mà kiểu Number không thể xử lý. Kiểu Number trong JavaScript giới hạn ở khoảng 2^53 - 1 cho các số nguyên. Nếu bạn cần làm việc với các số lớn hơn hoặc yêu cầu tính toán chính xác, BigInt là lựa chọn lý tưởng.

### Cách sử dụng
Bạn có thể tạo BigInt bằng cách thêm hậu tố `n` vào số nguyên hoặc sử dụng hàm `BigInt()`.

#### Cách tạo BigInt
1. Sử dụng hậu tố `n`:
   ```javascript
   const bigIntFromNumber = 123456789012345678901234567890n;
   ```

2. Sử dụng hàm `BigInt()`:
   ```javascript
   const bigIntFromString = BigInt("123456789012345678901234567890");
   ```

### Lưu ý
- BigInt không thể được trộn lẫn với kiểu Number trong các phép toán. Bạn cần chuyển đổi số trước khi thực hiện phép toán.
- Các phép toán như cộng, trừ, nhân và chia có thể được sử dụng với BigInt giống như với Number.

## Ví dụ
```javascript
// Tạo một BigInt từ một số
const bigInt1 = 123456789012345678901234567890n;
const bigInt2 = BigInt(12345678901234567890); // Chuyển đổi từ Number

// Phép cộng BigInt
const sum = bigInt1 + bigInt2;
console.log(sum); // 123456789024691357791012345678890n

// Phép trừ BigInt
const difference = bigInt1 - bigInt2;
console.log(difference); // 123456789000000000000000000000000n
```

## Giải thích
Khi làm việc với BigInt, có một số điều cần lưu ý:
- **Không thể trộn lẫn**: Nếu bạn cố gắng kết hợp BigInt với Number, JavaScript sẽ ném ra lỗi. Bạn cần chuyển đổi kiểu dữ liệu trước.
  ```javascript
  const bigInt = 1000n;
  const number = 1000;
  // const result = bigInt + number; // Lỗi: Cannot mix BigInt and other types
  ```
- **Sử dụng đúng phương thức**: Các phương thức như `toString()` có thể được sử dụng với BigInt để chuyển đổi về dạng chuỗi.

## Tóm tắt một dòng
BigInt trong JavaScript là kiểu dữ liệu cho phép lưu trữ và thao tác với các số nguyên lớn hơn giới hạn của Number, giúp đảm bảo tính chính xác trong các phép toán số học.