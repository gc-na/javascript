<!--
Meta Description: # NamedNodeMap trong JavaScript: Hướng dẫn và Ví dụ Cụ thể ## Tóm tắt NamedNodeMap là một đặc tính trong JavaScript được sử dụng để quản lý danh sách ...
Meta Keywords: tính, thuộc, attributes, một, các
-->

# NamedNodeMap trong JavaScript: Hướng dẫn và Ví dụ Cụ thể

## Tóm tắt
NamedNodeMap là một đặc tính trong JavaScript được sử dụng để quản lý danh sách các thuộc tính của một nút trong Document Object Model (DOM). Nó cho phép truy cập và thao tác các thuộc tính của phần tử HTML một cách dễ dàng.

## Tài liệu
### Mục đích
NamedNodeMap là một đối tượng trong JavaScript mà lưu trữ các thuộc tính của một nút (element) trong DOM. Nó thường được sử dụng khi bạn muốn lấy hoặc thay đổi các thuộc tính của các phần tử HTML như `<div>`, `<span>`, `<img>`, và nhiều hơn nữa.

### Cách sử dụng
NamedNodeMap thường được truy cập thông qua thuộc tính `attributes` của một phần tử. Ví dụ:

```javascript
let element = document.getElementById("myElement");
let attributes = element.attributes;
```

### Chi tiết
- **Truy cập thuộc tính**: Bạn có thể sử dụng chỉ số hoặc tên thuộc tính để truy cập các thuộc tính trong NamedNodeMap. 
- **Phương thức**: NamedNodeMap hỗ trợ một số phương thức như `getNamedItem()`, `item()`, và `length` để quản lý các thuộc tính.
- **Khả năng tương thích**: NamedNodeMap được hỗ trợ trên hầu hết các trình duyệt hiện đại.

## Ví dụ
### Ví dụ 1: Lấy tất cả thuộc tính của một phần tử
```javascript
let element = document.getElementById("myElement");
let attributes = element.attributes;

for (let i = 0; i < attributes.length; i++) {
    console.log(attributes[i].name + " = " + attributes[i].value);
}
```

### Ví dụ 2: Truy cập thuộc tính theo tên
```javascript
let element = document.getElementById("myElement");
let attributes = element.attributes;
let className = attributes.getNamedItem("class").value;

console.log("Class name: " + className);
```

### Ví dụ 3: Sử dụng phương thức item()
```javascript
let element = document.getElementById("myElement");
let attributes = element.attributes;

let firstAttribute = attributes.item(0);
console.log("First attribute: " + firstAttribute.name + " = " + firstAttribute.value);
```

## Giải thích
- **Thao tác với thuộc tính chưa được hỗ trợ**: Một số thuộc tính có thể không có tên, do đó việc sử dụng `getNamedItem()` có thể trả về `null`.
- **Không thể thêm/ xóa thuộc tính trực tiếp**: NamedNodeMap không cho phép bạn thêm hoặc xóa thuộc tính trực tiếp. Bạn cần phải sử dụng các phương thức của đối tượng phần tử để thực hiện việc này.
- **Thứ tự thuộc tính**: Thứ tự của các thuộc tính trong NamedNodeMap có thể không giống với thứ tự chúng xuất hiện trong HTML.

## Tóm tắt một câu
NamedNodeMap trong JavaScript là một đối tượng cho phép truy cập và quản lý danh sách các thuộc tính của phần tử trong DOM.