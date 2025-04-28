<!--
Meta Description: # HTMLAreaElement trong JavaScript: Tất cả những gì bạn cần biết ## Tóm tắt HTMLAreaElement là một giao diện trong JavaScript đại diện cho phần tử `<a...
Meta Keywords: area, các, trong, phần, hình
-->

# HTMLAreaElement trong JavaScript: Tất cả những gì bạn cần biết

## Tóm tắt
HTMLAreaElement là một giao diện trong JavaScript đại diện cho phần tử `<area>` trong tài liệu HTML, cho phép bạn tương tác với các vùng nhấp của hình ảnh.

## Tài liệu
### Mục đích
HTMLAreaElement cung cấp các thuộc tính và phương thức để thao tác với các phần tử `<area>`, cho phép phát triển web dễ dàng hơn khi làm việc với các hình ảnh nhấp chuột và vùng liên kết.

### Cách sử dụng
Để sử dụng HTMLAreaElement, bạn có thể truy cập các phần tử `<area>` trong DOM bằng cách sử dụng phương thức `document.querySelector()` hoặc `document.getElementsByTagName()`. 

#### Cấu trúc của phần tử `<area>`
```html
<map name="exampleMap">
    <area shape="rect" coords="34,44,270,350" href="example.html" alt="Example" />
</map>
<img src="example.jpg" usemap="#exampleMap" alt="Example Image" />
```

### Các thuộc tính chính
- `href`: Đường dẫn đến tài nguyên mà phần tử `<area>` liên kết.
- `alt`: Văn bản thay thế cho phần tử, hiển thị khi không thể tải hình ảnh.
- `shape`: Hình dạng của vùng liên kết, có thể là `rect`, `circle`, hoặc `poly`.
- `coords`: Tọa độ của vùng trong hình ảnh.

## Ví dụ
### Ví dụ cơ bản
Dưới đây là một ví dụ đơn giản về cách sử dụng HTMLAreaElement:

```html
<map name="myMap">
    <area shape="rect" coords="34,44,270,350" href="https://example.com" alt="Example Area" />
</map>
<img src="myImage.jpg" usemap="#myMap" alt="My Image" />
```

### Sử dụng JavaScript để truy cập thuộc tính
```javascript
const area = document.querySelector('area');
console.log(area.href); // In ra đường dẫn liên kết
console.log(area.alt);  // In ra văn bản thay thế
```

## Giải thích
### Những điều cần lưu ý
- Hãy chắc chắn rằng phần tử `<map>` có tên khớp với giá trị của thuộc tính `usemap` trong phần tử `<img>`.
- Các tọa độ trong thuộc tính `coords` cần phải chính xác và phù hợp với hình dạng được chỉ định trong thuộc tính `shape`.
- Không sử dụng các vùng liên kết quá nhỏ; điều này có thể làm cho người dùng khó khăn khi nhấp chuột vào chúng.

## Tóm tắt một câu
HTMLAreaElement trong JavaScript cho phép bạn tương tác với các vùng nhấp của hình ảnh, cung cấp các thuộc tính và phương thức để quản lý các liên kết hiệu quả.