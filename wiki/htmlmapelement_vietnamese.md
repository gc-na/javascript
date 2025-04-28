<!--
Meta Description: # HTMLMapElement trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt HTMLMapElement là một đối tượng trong JavaScript đại diện cho thẻ `<map>` trong HTML,...
Meta Keywords: map, một, trong, thẻ, html
-->

# HTMLMapElement trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
HTMLMapElement là một đối tượng trong JavaScript đại diện cho thẻ `<map>` trong HTML, cho phép bạn tạo các bản đồ hình ảnh tương tác trên trang web. 

## Tài liệu
HTMLMapElement là một phần của API DOM (Document Object Model) của HTML. Đối tượng này cho phép lập trình viên truy cập và thao tác với các thuộc tính và phương thức liên quan đến thẻ `<map>`. Thẻ `<map>` thường được sử dụng kết hợp với thẻ `<area>` để định nghĩa các vùng tương tác trên một hình ảnh.

### Mục đích
- Để định nghĩa các vùng có thể nhấp vào trên hình ảnh.
- Giúp người dùng tương tác với các phần khác nhau của hình ảnh.

### Cách sử dụng
Để sử dụng HTMLMapElement, trước tiên bạn cần tạo một thẻ `<map>` trong HTML và sau đó sử dụng JavaScript để truy cập và quản lý các thuộc tính của nó.

```html
<img src="example.jpg" usemap="#examplemap" alt="Example Image">
<map name="examplemap">
    <area shape="rect" coords="34,44,270,350" href="link1.html" alt="Link 1">
    <area shape="circle" coords="337,300,44" href="link2.html" alt="Link 2">
</map>
```

## Ví dụ
Dưới đây là một ví dụ về cách tạo và thao tác với một đối tượng HTMLMapElement trong JavaScript:

```javascript
// Lấy đối tượng map từ DOM
const map = document.querySelector('map[name="examplemap"]');

// Thay đổi thuộc tính của map
map.id = "newMapId";
console.log(map.id); // Kết quả: newMapId

// Thêm một area mới
const newArea = document.createElement('area');
newArea.shape = "poly";
newArea.coords = "100,100,150,150,200,100";
newArea.href = "link3.html";
newArea.alt = "Link 3";
map.appendChild(newArea);
```

## Giải thích
Khi sử dụng HTMLMapElement, có một số điểm cần lưu ý:
- Đảm bảo rằng thẻ `<img>` có thuộc tính `usemap` trỏ đến thẻ `<map>` bạn đã định nghĩa.
- Các vùng `<area>` phải có thuộc tính `shape` và `coords` được xác định rõ ràng để hoạt động đúng.
- Nếu không có vùng nào được định nghĩa trong `<map>`, hình ảnh sẽ không có vùng tương tác.

## Tóm tắt một dòng
HTMLMapElement trong JavaScript cho phép lập trình viên tạo và quản lý các vùng tương tác trên hình ảnh thông qua thẻ `<map>` trong HTML.