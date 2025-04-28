<!--
Meta Description: # NodeList trong JavaScript: Hiểu biết và Sử dụng ## Tóm tắt NodeList là một đối tượng trong JavaScript đại diện cho một tập hợp các nút DOM (Document...
Meta Keywords: nodelist, dụng, một, các, mảng
-->

# NodeList trong JavaScript: Hiểu biết và Sử dụng

## Tóm tắt
NodeList là một đối tượng trong JavaScript đại diện cho một tập hợp các nút DOM (Document Object Model). Nó thường được sử dụng để thao tác với các phần tử trong tài liệu HTML, cho phép lập trình viên truy cập và xử lý nhiều phần tử cùng một lúc.

## Tài liệu
### Mục đích
NodeList được tạo ra khi bạn sử dụng các phương thức như `document.querySelectorAll()` hoặc khi truy cập thuộc tính `childNodes` của một nút. NodeList không phải là một mảng, nhưng nó có thể được chuyển đổi thành mảng để thực hiện các phép toán mảng.

### Cách sử dụng
NodeList có thể được sử dụng trong nhiều tình huống khác nhau, đặc biệt là khi bạn cần thao tác với một nhóm phần tử DOM. Để tạo một NodeList, bạn có thể sử dụng:

- `document.querySelectorAll(selector)`: Trả về tất cả các phần tử khớp với bộ chọn CSS.
- `element.childNodes`: Trả về tất cả các nút con của một nút cụ thể.

### Chi tiết
- **NodeList tĩnh vs động**: NodeList có thể là tĩnh (như từ `querySelectorAll`) hoặc động (như từ `childNodes`). NodeList tĩnh không thay đổi khi nội dung trang được thay đổi, trong khi NodeList động sẽ tự động cập nhật.
- **Các phương thức**: NodeList có thể sử dụng một số phương thức như `forEach()` (đối với NodeList tĩnh) để lặp qua các phần tử.

## Ví dụ
### Ví dụ 1: Sử dụng `document.querySelectorAll()`
```javascript
const elements = document.querySelectorAll('.my-class');
elements.forEach((el) => {
    console.log(el.textContent);
});
```

### Ví dụ 2: Sử dụng `childNodes`
```javascript
const parent = document.getElementById('parent');
const children = parent.childNodes;

children.forEach((child) => {
    console.log(child.nodeName);
});
```

## Giải thích
- **Khi nào sử dụng NodeList**: Sử dụng NodeList khi bạn cần thao tác với nhiều phần tử DOM cùng lúc. Tuy nhiên, cần lưu ý rằng NodeList không phải là một mảng, vì vậy bạn không thể sử dụng các phương thức mảng như `map()` hoặc `filter()` trực tiếp trên nó.
- **Chuyển đổi NodeList thành mảng**: Để sử dụng các phương thức mảng, bạn có thể chuyển đổi NodeList thành mảng bằng cách sử dụng `Array.from()` hoặc toán tử spread (`...`):
```javascript
const elementsArray = Array.from(elements);
// Hoặc
const elementsArray = [...elements];
```

## Tóm tắt một dòng
NodeList là một đối tượng trong JavaScript cho phép truy cập và thao tác với nhiều nút DOM trong tài liệu HTML.