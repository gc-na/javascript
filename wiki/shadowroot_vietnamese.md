<!--
Meta Description: # ShadowRoot trong JavaScript: Tạo và Quản lý Shadow DOM ## Tóm tắt ShadowRoot là một phần của Web Components trong JavaScript, cho phép tạo ra Shadow...
Meta Keywords: dom, shadow, một, các, phần
-->

# ShadowRoot trong JavaScript: Tạo và Quản lý Shadow DOM

## Tóm tắt
ShadowRoot là một phần của Web Components trong JavaScript, cho phép tạo ra Shadow DOM, giúp encapsulate (đóng gói) các thành phần web, ngăn chặn xung đột với các phần khác trên trang.

## Tài liệu
ShadowRoot là một đối tượng đại diện cho một Shadow DOM. Shadow DOM là một kỹ thuật cho phép bạn tạo ra một DOM riêng biệt cho một thành phần mà không ảnh hưởng đến DOM chính của trang. Điều này rất hữu ích khi bạn muốn tạo ra các thành phần có thể tái sử dụng mà không lo lắng về sự xung đột với các CSS hoặc JavaScript bên ngoài.

### Mục đích
- **Encapsulation**: Giúp bảo vệ các thành phần khỏi bị ảnh hưởng bởi CSS hoặc JavaScript bên ngoài.
- **Reusability**: Tạo ra các thành phần có thể sử dụng lại mà không lo lắng về các xung đột.

### Cách sử dụng
Để tạo một ShadowRoot, bạn cần gọi phương thức `attachShadow` trên một phần tử DOM. Phương thức này sẽ trả về một đối tượng ShadowRoot.

```javascript
const hostElement = document.querySelector('#my-element');
const shadowRoot = hostElement.attachShadow({ mode: 'open' });
```

- **mode**: Có hai giá trị có thể sử dụng: `open` và `closed`.
  - `open`: Shadow DOM có thể truy cập từ bên ngoài.
  - `closed`: Shadow DOM không thể truy cập từ bên ngoài.

## Ví dụ
### Ví dụ 1: Tạo một Shadow DOM đơn giản

```html
<div id="my-element">Hello World</div>

<script>
  const hostElement = document.querySelector('#my-element');
  const shadowRoot = hostElement.attachShadow({ mode: 'open' });
  const shadowContent = document.createElement('span');
  shadowContent.textContent = 'This is inside Shadow DOM!';
  shadowRoot.appendChild(shadowContent);
</script>
```

### Ví dụ 2: Sử dụng Shadow DOM với CSS

```html
<style>
  #my-element {
    color: red;
  }
</style>

<div id="my-element">Hello World</div>

<script>
  const hostElement = document.querySelector('#my-element');
  const shadowRoot = hostElement.attachShadow({ mode: 'open' });

  const style = document.createElement('style');
  style.textContent = `
    span {
      color: blue;
    }
  `;
  shadowRoot.appendChild(style);

  const shadowContent = document.createElement('span');
  shadowContent.textContent = 'This is inside Shadow DOM!';
  shadowRoot.appendChild(shadowContent);
</script>
```

## Giải thích
### Những vấn đề thường gặp
1. **Truy cập Shadow DOM**: Nếu bạn sử dụng `mode: 'closed'`, bạn sẽ không thể truy cập Shadow DOM từ bên ngoài. Điều này có thể gây khó khăn khi cần tương tác với các phần tử bên trong Shadow DOM.
   
2. **CSS không hoạt động**: Nếu bạn không tạo một `<style>` bên trong Shadow DOM, các quy tắc CSS từ DOM chính sẽ không ảnh hưởng đến các phần tử bên trong Shadow DOM.

3. **Sự kiện không được phát**: Các sự kiện xảy ra trong Shadow DOM không tự động bùng phát ra ngoài. Bạn cần phải quản lý sự kiện một cách cẩn thận nếu bạn cần chúng tương tác với các phần tử bên ngoài.

## Tóm tắt một dòng
ShadowRoot trong JavaScript cho phép tạo một Shadow DOM, giúp encapsulate các thành phần web và ngăn chặn sự xung đột với các phần khác của trang.