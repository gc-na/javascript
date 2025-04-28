<!--
Meta Description: # Chọn Lọc (Selection) trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm Tắt Chọn lọc (Selection) trong JavaScript đề cập đến việc truy xuất và tha...
Meta Keywords: các, document, phần, javascript, chọn
-->

# Chọn Lọc (Selection) trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm Tắt
Chọn lọc (Selection) trong JavaScript đề cập đến việc truy xuất và thao tác các phần tử trong DOM (Document Object Model) của trang web, cho phép lập trình viên thay đổi nội dung, kiểu dáng và hành vi của trang.

## Tài Liệu
Chọn lọc là một kỹ thuật quan trọng trong JavaScript, cho phép lập trình viên truy cập và thay đổi các phần tử HTML trên trang. Điều này có thể được thực hiện thông qua các phương thức như `document.getElementById()`, `document.getElementsByClassName()`, `document.querySelector()`, và `document.querySelectorAll()`. 

### Mục Đích
- Giúp lập trình viên truy cập và thao tác với các phần tử HTML trên trang.
- Cho phép thay đổi nội dung, kiểu dáng và hành vi của trang một cách linh hoạt.

### Cách Sử Dụng
- **`document.getElementById(id)`**: Trả về phần tử đầu tiên có ID tương ứng.
- **`document.getElementsByClassName(className)`**: Trả về một danh sách các phần tử có cùng lớp.
- **`document.querySelector(selector)`**: Trả về phần tử đầu tiên khớp với bộ chọn CSS.
- **`document.querySelectorAll(selector)`**: Trả về tất cả các phần tử khớp với bộ chọn CSS.

Các phương thức này cho phép lập trình viên dễ dàng truy cập và thay đổi các thuộc tính của phần tử, như `innerHTML`, `style`, và các thuộc tính khác.

## Ví Dụ
### Ví Dụ 1: Sử dụng `getElementById`
```javascript
let element = document.getElementById("myElement");
element.innerHTML = "Nội dung mới!";
```

### Ví Dụ 2: Sử dụng `getElementsByClassName`
```javascript
let elements = document.getElementsByClassName("myClass");
for (let i = 0; i < elements.length; i++) {
    elements[i].style.color = "blue";
}
```

### Ví Dụ 3: Sử dụng `querySelector`
```javascript
let firstElement = document.querySelector(".myClass");
firstElement.style.backgroundColor = "yellow";
```

### Ví Dụ 4: Sử dụng `querySelectorAll`
```javascript
let allElements = document.querySelectorAll("p");
allElements.forEach(element => {
    element.style.fontSize = "20px";
});
```

## Giải Thích
Một số điểm cần lưu ý khi sử dụng kỹ thuật chọn lọc trong JavaScript:

- **Hiệu suất**: `getElementById` nhanh hơn so với `querySelector` vì nó chỉ tìm kiếm theo ID.
- **Danh sách Node**: Các phương thức như `getElementsByClassName` và `getElementsByTagName` trả về danh sách các phần tử (HTMLCollection), không phải mảng, do đó không thể sử dụng trực tiếp các phương thức mảng như `forEach`.
- **Thao tác DOM**: Khi thay đổi nội dung hoặc kiểu dáng của phần tử, hãy chắc chắn rằng nó không làm ảnh hưởng đến trải nghiệm người dùng hoặc làm hỏng cấu trúc của trang.

## Tóm Tắt Một Câu
Chọn lọc trong JavaScript cho phép lập trình viên truy cập và thao tác linh hoạt với các phần tử HTML trong DOM.