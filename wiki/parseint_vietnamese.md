<!--
Meta Description: # Hàm `parseInt` trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm Tắt Hàm `parseInt` trong JavaScript được sử dụng để chuyển đổi một chuỗi thành m...
Meta Keywords: parseint, chuỗi, một, trả, chuyển
-->

# Hàm `parseInt` trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm Tắt
Hàm `parseInt` trong JavaScript được sử dụng để chuyển đổi một chuỗi thành một số nguyên. Nó giúp lập trình viên xử lý và chuyển đổi dữ liệu đầu vào từ dạng chuỗi sang số một cách dễ dàng.

## Tài Liệu
### Mục Đích
Hàm `parseInt` chuyển đổi chuỗi đầu vào thành một số nguyên. Nếu chuỗi không thể được chuyển đổi, nó sẽ trả về giá trị `NaN` (Not-a-Number).

### Cú Pháp
```javascript
parseInt(string, radix);
```

### Tham Số
- **string**: Chuỗi cần chuyển đổi thành số nguyên.
- **radix** (tùy chọn): Một số nguyên từ 2 đến 36, xác định hệ cơ số của chuỗi. Nếu không chỉ định, hệ cơ số mặc định sẽ là 10, trừ khi chuỗi bắt đầu bằng "0x" (hệ thập lục phân).

### Giá Trị Trả Về
- Trả về số nguyên tương ứng với chuỗi đầu vào.
- Nếu không thể chuyển đổi, trả về `NaN`.

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
console.log(parseInt("123"));        // Kết quả: 123
console.log(parseInt("1010", 2));    // Kết quả: 10 (hệ nhị)
console.log(parseInt("10.5"));       // Kết quả: 10
console.log(parseInt("abc"));        // Kết quả: NaN
```

### Ví Dụ Với Radix
```javascript
console.log(parseInt("0xF", 16));    // Kết quả: 15
console.log(parseInt("10", 8));       // Kết quả: 8 (hệ bát phân)
console.log(parseInt("31", 10));      // Kết quả: 31
```

## Giải Thích
### Những Lưu Ý Quan Trọng
- **NaN**: Nếu chuỗi đầu vào không chứa ký tự số, `parseInt` sẽ trả về `NaN`. Ví dụ, `parseInt("abc")` và `parseInt("")` đều trả về `NaN`.
- **Radix**: Không chỉ định giá trị radix có thể gây ra sự nhầm lẫn trong một số trường hợp. Ví dụ, `parseInt("08")` trong một số trình duyệt có thể trả về 8, nhưng trong một số hệ thống có thể trả về `NaN` vì 8 không hợp lệ trong hệ bát phân.
- **Ký tự không phải số**: `parseInt` sẽ dừng chuyển đổi ngay khi gặp ký tự không phải số. Ví dụ, `parseInt("123abc")` sẽ trả về 123.

## Tóm Tắt Một Dòng
Hàm `parseInt` trong JavaScript chuyển đổi chuỗi thành số nguyên, hỗ trợ nhiều hệ cơ số và giúp xử lý dữ liệu đầu vào hiệu quả.