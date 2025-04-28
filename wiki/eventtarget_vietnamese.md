<!--
Meta Description: # EventTarget trong JavaScript: Hướng dẫn toàn diện ## Tóm tắt `EventTarget` là một interface trong JavaScript cho phép một đối tượng có thể nhận và x...
Meta Keywords: kiện, một, các, trình, eventtarget
-->

# EventTarget trong JavaScript: Hướng dẫn toàn diện

## Tóm tắt
`EventTarget` là một interface trong JavaScript cho phép một đối tượng có thể nhận và xử lý các sự kiện. Nó cung cấp các phương thức để thêm, xóa và kích hoạt các sự kiện, giúp xây dựng các ứng dụng web tương tác.

## Tài liệu
### Mục đích
`EventTarget` là một phần quan trọng trong mô hình sự kiện của JavaScript. Nó cho phép các đối tượng, như DOM elements, nhận các sự kiện như click, load, và input. Bằng cách sử dụng `EventTarget`, bạn có thể tạo ra các ứng dụng web mà người dùng có thể tương tác một cách trực quan.

### Cách sử dụng
`EventTarget` không được khởi tạo trực tiếp. Thay vào đó, các đối tượng DOM như `HTMLElement`, `Document`, và `Window` kế thừa từ `EventTarget`. Bạn có thể sử dụng các phương thức như `addEventListener`, `removeEventListener`, và `dispatchEvent` để quản lý sự kiện.

#### Ví dụ các phương thức:
- **addEventListener**: Thêm một trình xử lý sự kiện.
- **removeEventListener**: Xóa một trình xử lý sự kiện.
- **dispatchEvent**: Kích hoạt một sự kiện.

### Chi tiết
- **Phương thức**
  - `addEventListener(type, listener, options)`: Thêm một trình xử lý sự kiện cho một loại sự kiện cụ thể.
  - `removeEventListener(type, listener, options)`: Xóa một trình xử lý sự kiện đã được thêm.
  - `dispatchEvent(event)`: Kích hoạt một sự kiện mà bạn đã tạo.

- **Tùy chọn cho `addEventListener`**
  - `options`: Có thể là một đối tượng với các thuộc tính như `capture`, `once`, và `passive`.

- **Sự kiện**
  - Các sự kiện có thể là sự kiện mặc định của trình duyệt hoặc sự kiện tùy chỉnh do người dùng tạo ra.

## Ví dụ
### Thêm và xóa trình xử lý sự kiện
```javascript
const button = document.getElementById('myButton');

function handleClick() {
    alert('Button clicked!');
}

// Thêm trình xử lý sự kiện
button.addEventListener('click', handleClick);

// Xóa trình xử lý sự kiện
button.removeEventListener('click', handleClick);
```

### Kích hoạt một sự kiện tùy chỉnh
```javascript
const event = new Event('myCustomEvent');

document.addEventListener('myCustomEvent', function() {
    console.log('Custom event triggered!');
});

// Kích hoạt sự kiện tùy chỉnh
document.dispatchEvent(event);
```

## Giải thích
Một số điểm cần lưu ý khi làm việc với `EventTarget`:
- **Bẫy sự kiện**: Khi thêm nhiều trình xử lý sự kiện cho cùng một sự kiện, hãy chắc chắn rằng bạn đã định nghĩa đúng loại sự kiện và trình xử lý để tránh xung đột.
- **Khi nào xóa trình xử lý**: Luôn luôn xóa trình xử lý sự kiện khi không còn cần thiết để tránh rò rỉ bộ nhớ, đặc biệt khi sử dụng các đối tượng DOM.
- **Sự kiện nổi bọt và bắt**: Khi sử dụng `addEventListener`, bạn có thể chỉ định chế độ bắt hoặc nổi bọt cho sự kiện để kiểm soát cách thức mà sự kiện được xử lý.

## Tóm tắt một dòng
`EventTarget` là interface trong JavaScript cho phép đối tượng nhận và xử lý các sự kiện, giúp xây dựng các ứng dụng web tương tác một cách hiệu quả.