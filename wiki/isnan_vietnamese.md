<!--
Meta Description: # Tìm Hiểu Về Hàm isNaN Trong JavaScript ## Tóm tắt Hàm `isNaN` trong JavaScript được sử dụng để kiểm tra xem một giá trị có phải là NaN (Not-a-Number...
Meta Keywords: isnan, một, giá, trị, không
-->

# Tìm Hiểu Về Hàm isNaN Trong JavaScript

## Tóm tắt
Hàm `isNaN` trong JavaScript được sử dụng để kiểm tra xem một giá trị có phải là NaN (Not-a-Number) hay không, giúp lập trình viên xác định liệu một giá trị có thể được coi là số hay không.

## Tài liệu
Hàm `isNaN` là một phương thức toàn cục của JavaScript, dùng để xác định xem một giá trị có phải là NaN hay không. NaN là một giá trị đặc biệt trong JavaScript, biểu thị cho một giá trị không phải số. Điều này thường xảy ra trong các phép tính số học không hợp lệ, chẳng hạn như chia 0 cho 0.

### Cú pháp
```javascript
isNaN(value)
```

### Tham số
- **value**: Giá trị mà bạn muốn kiểm tra.

### Trả về
Hàm `isNaN` trả về:
- `true`: Nếu giá trị là NaN hoặc không thể chuyển đổi thành một số.
- `false`: Nếu giá trị có thể được chuyển đổi thành một số hợp lệ.

## Ví dụ
Dưới đây là một số ví dụ để minh họa cách sử dụng hàm `isNaN`:

```javascript
console.log(isNaN(NaN)); // true
console.log(isNaN("Hello")); // true
console.log(isNaN(123)); // false
console.log(isNaN("123")); // false
console.log(isNaN(undefined)); // true
console.log(isNaN(null)); // false
console.log(isNaN("")); // false
```

## Giải thích
Một số điểm cần lưu ý khi sử dụng hàm `isNaN` bao gồm:

1. **Kiểm tra kiểu dữ liệu**: `isNaN` không chỉ kiểm tra giá trị NaN mà còn kiểm tra xem giá trị có phải là số hay không. Ví dụ, `isNaN("Hello")` sẽ trả về `true` vì "Hello" không thể chuyển đổi thành số.

2. **Chuyển đổi kiểu**: Hàm này sẽ cố gắng chuyển đổi giá trị thành số trước khi kiểm tra, điều này có thể dẫn đến những kết quả không như mong đợi. Ví dụ, `isNaN("123")` trả về `false` vì chuỗi "123" có thể được chuyển đổi thành số 123.

3. **Sử dụng isNaN một cách cẩn thận**: Có những tình huống mà bạn nên sử dụng `Number.isNaN()` thay vì `isNaN()`. Hàm `Number.isNaN()` chỉ trả về `true` nếu giá trị là NaN và không thực hiện chuyển đổi kiểu, điều này giúp tránh những kết quả không mong muốn.

## Tóm tắt một dòng
Hàm `isNaN` trong JavaScript giúp kiểm tra xem một giá trị có phải là NaN hay không, với khả năng chuyển đổi kiểu dữ liệu.