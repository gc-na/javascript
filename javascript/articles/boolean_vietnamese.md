<!--
Meta Description: # Boolean trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng ## Tóm tắt Boolean là một kiểu dữ liệu cơ bản trong JavaScript, được sử dụng để đại diện cho ...
Meta Keywords: boolean, javascript, giá, trị, trong
-->

# Boolean trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng

## Tóm tắt
Boolean là một kiểu dữ liệu cơ bản trong JavaScript, được sử dụng để đại diện cho giá trị đúng (true) hoặc sai (false). Nó là thành phần quan trọng trong lập trình điều kiện và điều khiển luồng chương trình.

## Tài liệu
### Mục đích
Kiểu dữ liệu Boolean trong JavaScript cho phép lập trình viên thực hiện các phép so sánh và điều kiện, từ đó kiểm soát luồng thực hiện của chương trình.

### Cách sử dụng
Trong JavaScript, bạn có thể tạo giá trị Boolean bằng cách sử dụng các từ khóa `true` hoặc `false`. Ngoài ra, một số biểu thức sẽ trả về giá trị Boolean, ví dụ như phép so sánh:

```javascript
let isTrue = (5 > 3); // isTrue sẽ là true
let isFalse = (5 < 3); // isFalse sẽ là false
```

### Chi tiết
- **Cách tạo giá trị Boolean**: Bạn có thể sử dụng hàm `Boolean()` để chuyển đổi các giá trị thành Boolean:
  ```javascript
  console.log(Boolean(1)); // true
  console.log(Boolean(0)); // false
  ```
- **Giá trị Falsy và Truthy**: Trong JavaScript, có những giá trị được coi là "falsy" (sai) và "truthy" (đúng). Các giá trị falsy bao gồm: `0`, `""` (chuỗi rỗng), `null`, `undefined`, và `NaN`.

## Ví dụ
### Ví dụ cơ bản
1. Sử dụng Boolean trong điều kiện `if`:
   ```javascript
   let isLoggedIn = true;
   if (isLoggedIn) {
       console.log("Chào mừng bạn!");
   } else {
       console.log("Vui lòng đăng nhập.");
   }
   ```

2. So sánh hai số:
   ```javascript
   let a = 10;
   let b = 20;
   let result = (a < b); // result sẽ là true
   console.log(result); // In ra true
   ```

3. Chuyển đổi giá trị sang Boolean:
   ```javascript
   let value = "Hello";
   console.log(Boolean(value)); // true
   ```

## Giải thích
- **Cạm bẫy phổ biến**: Một số lập trình viên mới có thể nhầm lẫn giữa các giá trị truthy và falsy, dẫn đến lỗi khi sử dụng trong các biểu thức điều kiện.
- **Kiểm tra kiểu dữ liệu**: Bạn có thể sử dụng `typeof` để xác định xem một giá trị có phải là Boolean hay không:
  ```javascript
  console.log(typeof true); // "boolean"
  console.log(typeof 0); // "number"
  ```

## Tóm tắt một dòng
Boolean là kiểu dữ liệu cơ bản trong JavaScript, chỉ có hai giá trị: true và false, dùng để kiểm soát luồng điều kiện trong lập trình.