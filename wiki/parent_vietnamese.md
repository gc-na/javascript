<!--
Meta Description: # Parent trong JavaScript: Hiểu Biết Về Quan Hệ Cha Con ## Tóm tắt Trong JavaScript, khái niệm "parent" (cha) thường được sử dụng để chỉ đối tượng cha...
Meta Keywords: đối, tượng, cha, trong, parent
-->

# Parent trong JavaScript: Hiểu Biết Về Quan Hệ Cha Con

## Tóm tắt
Trong JavaScript, khái niệm "parent" (cha) thường được sử dụng để chỉ đối tượng cha của một đối tượng con trong cấu trúc dữ liệu. Điều này thường xuất hiện trong ngữ cảnh của cây DOM (Document Object Model) hoặc trong việc kế thừa các thuộc tính và phương thức giữa các đối tượng.

## Tài liệu
### Mục đích
Khái niệm "parent" trong JavaScript chủ yếu được áp dụng trong lập trình hướng đối tượng và quản lý DOM. Đối tượng cha (parent) là đối tượng bao quanh hoặc chứa đối tượng con (child), cho phép chia sẻ các thuộc tính và phương thức giữa chúng.

### Cách sử dụng
1. **Trong DOM**: Để truy cập đối tượng cha của một phần tử trong cây DOM, bạn có thể sử dụng thuộc tính `parentNode` hoặc `parentElement`.
2. **Trong lập trình hướng đối tượng**: Khi sử dụng prototype, bạn có thể truy cập đối tượng cha thông qua thuộc tính `__proto__` hoặc `Object.getPrototypeOf()`.

### Chi tiết
- **DOM**: 
  - `element.parentNode` trả về nút cha của phần tử hiện tại.
  - `element.parentElement` tương tự nhưng chỉ trả về phần tử cha (không phải nút văn bản).
  
- **Hướng đối tượng**:
  - Khi tạo một đối tượng con từ một đối tượng cha, các thuộc tính và phương thức của đối tượng cha có thể được truy cập từ đối tượng con.
  - Ví dụ:
    ```javascript
    function Parent() {
      this.name = 'Parent';
    }

    function Child() {
      Parent.call(this); // Gọi hàm cha
      this.age = 10;
    }

    Child.prototype = Object.create(Parent.prototype);
    Child.prototype.constructor = Child;
    ```

## Ví dụ
### Ví dụ 1: Truy cập đối tượng cha trong DOM
```javascript
const childElement = document.getElementById('child');
const parentElement = childElement.parentNode; // Trả về phần tử cha
console.log(parentElement);
```

### Ví dụ 2: Kế thừa trong JavaScript
```javascript
function Parent() {
  this.name = 'Parent';
}

function Child() {
  Parent.call(this); // Gọi hàm cha
  this.age = 10;
}

Child.prototype = Object.create(Parent.prototype);
Child.prototype.constructor = Child;

const childInstance = new Child();
console.log(childInstance.name); // 'Parent'
```

## Giải thích
- **Cạm bẫy thường gặp**: Khi sử dụng `parentNode`, hãy chắc chắn rằng phần tử bạn đang kiểm tra thực sự có phần tử cha. Nếu không, bạn có thể gặp lỗi hoặc nhận giá trị `null`.
- **Kế thừa**: Đảm bảo rằng bạn đã thiết lập đúng prototype để tránh mất các thuộc tính và phương thức của đối tượng cha.

## Tóm tắt một câu
Khái niệm "parent" trong JavaScript liên quan đến việc truy cập và kế thừa thuộc tính từ đối tượng cha trong cây DOM hoặc trong lập trình hướng đối tượng.