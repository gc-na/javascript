<!--
Meta Description: # Hàm isFinite trong JavaScript: Kiểm Tra Tính Hợp Lệ của Số ## Tóm tắt Hàm `isFinite` trong JavaScript được sử dụng để xác định xem một giá trị có ph...
Meta Keywords: isfinite, không, console, log, true
-->

# Hàm isFinite trong JavaScript: Kiểm Tra Tính Hợp Lệ của Số

## Tóm tắt
Hàm `isFinite` trong JavaScript được sử dụng để xác định xem một giá trị có phải là số hữu hạn hay không. Hàm này trả về `true` nếu giá trị là một số, và không phải là `Infinity`, `-Infinity`, hoặc `NaN`.

## Tài liệu
Hàm `isFinite` là một phần của đối tượng toàn cục `Global` trong JavaScript. Mục đích chính của hàm này là kiểm tra xem một giá trị có phải là một số hữu hạn hay không. Cú pháp của hàm là:

```javascript
isFinite(value)
```

### Tham số
- **value**: Giá trị cần được kiểm tra. Có thể là bất kỳ kiểu dữ liệu nào.

### Trả về
- Trả về `true` nếu giá trị là một số hữu hạn.
- Trả về `false` nếu giá trị là `Infinity`, `-Infinity`, hoặc `NaN`.

### Lưu ý
- Hàm `isFinite` sẽ tự động chuyển đổi giá trị không phải là số thành số trước khi kiểm tra. Ví dụ: chuỗi số sẽ được chuyển đổi thành số.

## Ví dụ
### Ví dụ cơ bản
```javascript
console.log(isFinite(10)); // true
console.log(isFinite(-10)); // true
console.log(isFinite(0)); // true
console.log(isFinite(Infinity)); // false
console.log(isFinite(-Infinity)); // false
console.log(isFinite(NaN)); // false
console.log(isFinite("10")); // true
console.log(isFinite("hello")); // false
```

### Ví dụ với các kiểu dữ liệu khác
```javascript
console.log(isFinite(null)); // true (null được chuyển đổi thành 0)
console.log(isFinite(undefined)); // false (undefined không phải là số)
console.log(isFinite([])); // true (mảng rỗng được chuyển đổi thành 0)
console.log(isFinite([1])); // true (mảng có một phần tử số được chuyển đổi thành 1)
console.log(isFinite([1, 2])); // false (mảng có nhiều phần tử không thể chuyển đổi thành số)
```

## Giải thích
Hàm `isFinite` có thể gây nhầm lẫn khi làm việc với các giá trị không phải số. Một số điểm cần lưu ý:
- Khi bạn truyền vào một chuỗi, nếu chuỗi đó có thể được chuyển đổi thành số, hàm sẽ trả về `true`. Nếu không, nó sẽ trả về `false`.
- `isFinite` không giống như `Number.isFinite`, hàm này không thực hiện chuyển đổi kiểu dữ liệu. `Number.isFinite` chỉ trả về `true` cho các số hữu hạn và không chấp nhận các kiểu dữ liệu khác.

## Tóm tắt một dòng
Hàm `isFinite` trong JavaScript kiểm tra xem một giá trị có phải là số hữu hạn hay không, trả về `true` cho số hợp lệ và `false` cho các giá trị không hợp lệ.