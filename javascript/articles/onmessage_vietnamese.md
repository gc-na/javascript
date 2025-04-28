<!--
Meta Description: # Sự Kiện onmessage Trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt Sự kiện `onmessage` trong JavaScript được sử dụng để lắng nghe và xử lý các thông ...
Meta Keywords: onmessage, thông, điệp, worker, event
-->

# Sự Kiện onmessage Trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
Sự kiện `onmessage` trong JavaScript được sử dụng để lắng nghe và xử lý các thông điệp được gửi đến từ một Web Worker hoặc từ một cửa sổ khác. Đây là một phần quan trọng trong việc giao tiếp giữa các luồng thực thi và giúp xây dựng các ứng dụng web hiệu suất cao.

## Tài Liệu
### Mục đích
Sự kiện `onmessage` cho phép bạn nhận thông điệp từ một nguồn khác, chẳng hạn như Web Worker hoặc cửa sổ con. Điều này rất hữu ích khi bạn cần xử lý các tác vụ nặng mà không làm chậm giao diện người dùng.

### Cách sử dụng
Để sử dụng `onmessage`, bạn cần gán một hàm xử lý sự kiện cho thuộc tính `onmessage` của đối tượng mà bạn muốn lắng nghe, chẳng hạn như Worker hoặc cửa sổ. Hàm này sẽ nhận một đối tượng sự kiện chứa thông tin về thông điệp đã nhận.

**Cú pháp:**
```javascript
worker.onmessage = function(event) {
    console.log('Thông điệp nhận được:', event.data);
};
```

### Chi tiết
- `event.data`: Thuộc tính này chứa dữ liệu được gửi từ nguồn gửi thông điệp.
- Có thể sử dụng các phương thức như `postMessage` để gửi thông điệp đến Worker hoặc cửa sổ khác.
- Sự kiện `onmessage` là bất đồng bộ, có nghĩa là nó không chặn luồng chính khi nhận thông điệp.

## Ví dụ
### Ví dụ 1: Sử dụng với Web Worker
```javascript
// main.js
const worker = new Worker('worker.js');

worker.onmessage = function(event) {
    console.log('Thông điệp từ Worker:', event.data);
};

worker.postMessage('Xin chào từ main.js');
```

```javascript
// worker.js
onmessage = function(event) {
    console.log('Thông điệp từ main:', event.data);
    postMessage('Xin chào từ Worker');
};
```

### Ví dụ 2: Sử dụng giữa các cửa sổ
```javascript
// Parent window
const childWindow = window.open('child.html');

childWindow.onmessage = function(event) {
    console.log('Thông điệp từ cửa sổ con:', event.data);
};

childWindow.postMessage('Xin chào từ parent window', '*');
```

```html
<!-- child.html -->
<script>
    window.onmessage = function(event) {
        console.log('Thông điệp từ parent:', event.data);
        window.opener.postMessage('Xin chào từ child window', '*');
    };
</script>
```

## Giải Thích
### Các vấn đề thường gặp
- **Kiểm tra nguồn gốc thông điệp**: Khi nhận thông điệp, luôn kiểm tra `event.origin` để đảm bảo thông điệp đến từ nguồn tin cậy.
- **Dữ liệu lớn**: Khi gửi dữ liệu lớn, hãy cân nhắc sử dụng `Transferable Objects` để cải thiện hiệu suất.
- **Đặt lại onmessage**: Nếu bạn gán lại hàm xử lý cho `onmessage`, hãy nhớ rằng hàm cũ sẽ không còn hiệu lực.

### Lưu ý bổ sung
- `onmessage` hỗ trợ các loại dữ liệu không đồng bộ như ArrayBuffer và Blob, điều này có thể hữu ích trong các ứng dụng hiện đại.
- Hãy đảm bảo rằng bạn đã khởi tạo Worker một cách chính xác trước khi sử dụng `onmessage`.

## Tóm tắt một dòng
Sự kiện `onmessage` trong JavaScript cho phép bạn nhận và xử lý các thông điệp từ Web Workers và các cửa sổ khác, giúp tăng cường khả năng giao tiếp trong ứng dụng web.