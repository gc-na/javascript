<!--
Meta Description: # CSSStyleDeclaration trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt `CSSStyleDeclaration` là một giao diện trong JavaScript cho phép truy cập và chỉ...
Meta Keywords: tính, thuộc, các, css, javascript
-->

# CSSStyleDeclaration trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
`CSSStyleDeclaration` là một giao diện trong JavaScript cho phép truy cập và chỉnh sửa các thuộc tính CSS của phần tử HTML. Nó hỗ trợ việc thao tác với các kiểu dáng của phần tử thông qua JavaScript, giúp tạo ra các giao diện động và tương tác hơn.

## Tài liệu
### Mục đích
`CSSStyleDeclaration` cho phép lập trình viên truy cập và thay đổi trực tiếp các thuộc tính CSS của một phần tử. Bằng cách sử dụng đối tượng này, bạn có thể làm cho trang web của mình trở nên linh hoạt và phản ứng nhanh với các thay đổi trong tương lai.

### Cách sử dụng
- Để truy cập `CSSStyleDeclaration`, bạn thường sử dụng thuộc tính `style` của một phần tử DOM. 
- Bạn có thể thiết lập hoặc lấy giá trị của các thuộc tính CSS thông qua cú pháp thuộc tính hoặc cú pháp chuỗi.

### Chi tiết
- `CSSStyleDeclaration` chứa tất cả các thuộc tính CSS mà bạn có thể áp dụng cho một phần tử.
- Các thuộc tính có thể được truy cập bằng cách sử dụng cú pháp `element.style.propertyName` hoặc `element.style['propertyName']`.
- Ví dụ: `element.style.backgroundColor = 'blue';` sẽ thay đổi màu nền của phần tử thành màu xanh.

## Ví dụ
### Thay đổi màu nền
```javascript
let element = document.getElementById('myElement');
element.style.backgroundColor = 'red';
```

### Thay đổi nhiều thuộc tính
```javascript
let element = document.getElementById('myElement');
element.style.cssText = 'color: white; background-color: black; font-size: 20px;';
```

### Lấy giá trị thuộc tính CSS
```javascript
let element = document.getElementById('myElement');
let color = element.style.color; // Trả về màu sắc hiện tại
```

## Giải thích
### Những cạm bẫy phổ biến
- **Không áp dụng được thuộc tính CSS**: Một số thuộc tính CSS không thể được thay đổi qua `style` nếu chúng không được định nghĩa trực tiếp trên phần tử. Ví dụ, nếu thuộc tính được định nghĩa trong một stylesheet bên ngoài, bạn sẽ cần sử dụng `getComputedStyle` để truy cập nó.
- **Tính khả dụng của thuộc tính**: Một số thuộc tính có tên khác nhau trong JavaScript so với CSS. Ví dụ, `background-color` trong CSS trở thành `backgroundColor` trong JavaScript.
- **Chuyển đổi đơn vị**: Khi thiết lập thuộc tính như chiều rộng hoặc chiều cao, bạn cần chắc chắn rằng bạn đã cung cấp đơn vị như `px`, `em`, hoặc `%`.

## Tóm tắt một dòng
`CSSStyleDeclaration` cho phép lập trình viên JavaScript truy cập và thay đổi các thuộc tính CSS của phần tử DOM để tạo ra các giao diện động.