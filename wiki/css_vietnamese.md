<!--
Meta Description: # CSS trong JavaScript: Tinh chỉnh Giao Diện Web ## Tóm Tắt CSS (Cascading Style Sheets) là ngôn ngữ được sử dụng để mô tả giao diện và định dạng của ...
Meta Keywords: css, thuộc, tính, javascript, dụng
-->

# CSS trong JavaScript: Tinh chỉnh Giao Diện Web

## Tóm Tắt
CSS (Cascading Style Sheets) là ngôn ngữ được sử dụng để mô tả giao diện và định dạng của tài liệu HTML. Trong JavaScript, việc thao tác với CSS cho phép các nhà phát triển thay đổi phong cách trang web một cách linh hoạt và động.

## Tài Liệu

### Mục Đích
CSS trong JavaScript cho phép các lập trình viên điều chỉnh phong cách của các phần tử HTML thông qua DOM (Document Object Model). Điều này có thể bao gồm việc thay đổi màu sắc, kích thước, bố cục và nhiều thuộc tính khác theo cách động.

### Cách Sử Dụng
Để thao tác với CSS trong JavaScript, bạn có thể sử dụng thuộc tính `style` của phần tử DOM. Dưới đây là cách tiếp cận cơ bản:

1. **Chọn phần tử HTML**: Sử dụng các phương thức như `document.getElementById`, `document.querySelector`, v.v.
2. **Thay đổi thuộc tính CSS**: Sử dụng thuộc tính `style` để thay đổi các thuộc tính CSS.

### Chi Tiết
- **Thay đổi nhiều thuộc tính**: Bạn có thể thay đổi nhiều thuộc tính CSS cùng lúc bằng cách gán giá trị cho từng thuộc tính.
- **Thao tác với lớp CSS**: Bạn cũng có thể thêm hoặc xóa lớp CSS bằng cách sử dụng `classList.add()`, `classList.remove()`, hoặc `classList.toggle()`.

## Ví Dụ

### Ví Dụ 1: Thay đổi màu nền
```javascript
document.getElementById("myElement").style.backgroundColor = "blue";
```

### Ví Dụ 2: Thay đổi nhiều thuộc tính
```javascript
const element = document.querySelector(".myClass");
element.style.color = "white";
element.style.fontSize = "20px";
element.style.margin = "10px";
```

### Ví Dụ 3: Thêm lớp mới
```javascript
const button = document.getElementById("myButton");
button.classList.add("active");
```

## Giải Thích
- **Không áp dụng toàn bộ thuộc tính**: Khi sử dụng `style`, bạn chỉ có thể thay đổi các thuộc tính CSS mà không thể áp dụng các quy tắc CSS phức tạp hơn như media queries hoặc pseudo-classes.
- **Tránh ghi đè**: Nếu bạn sử dụng CSS trong tệp CSS bên ngoài và đồng thời thay đổi trong JavaScript, thuộc tính trong JavaScript sẽ ghi đè lên thuộc tính trong CSS, điều này có thể dẫn đến sự không nhất quán.

## Tóm Tắt Một Dòng
CSS trong JavaScript cho phép lập trình viên điều chỉnh phong cách trang web một cách động thông qua DOM.