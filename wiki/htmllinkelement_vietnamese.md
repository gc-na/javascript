<!--
Meta Description: # HTMLLinkElement: Đối Tượng Liên Kết trong JavaScript ## Tóm tắt `HTMLLinkElement` là một đối tượng trong JavaScript đại diện cho phần tử `<link>` tr...
Meta Keywords: link, tài, các, thuộc, tính
-->

# HTMLLinkElement: Đối Tượng Liên Kết trong JavaScript

## Tóm tắt
`HTMLLinkElement` là một đối tượng trong JavaScript đại diện cho phần tử `<link>` trong tài liệu HTML, cho phép lập trình viên thao tác với các liên kết đến tài nguyên bên ngoài như CSS.

## Tài liệu
### Mục đích
`HTMLLinkElement` cho phép bạn truy cập và điều chỉnh các thuộc tính của các liên kết trong tài liệu HTML, như liên kết đến file CSS, biểu tượng favicon, và các tài nguyên khác.

### Cách sử dụng
Để sử dụng `HTMLLinkElement`, bạn có thể truy cập nó thông qua phương thức `document.createElement('link')` hoặc thông qua thuộc tính `document.links` để lấy tất cả các phần tử `<link>` trong tài liệu.

### Chi tiết
- **Thuộc tính**:
  - `href`: URL của tài nguyên liên kết.
  - `rel`: Quan hệ giữa tài liệu hiện tại và tài nguyên liên kết (ví dụ: "stylesheet").
  - `type`: Loại MIME của tài nguyên liên kết (ví dụ: "text/css").
  - `media`: Điều kiện mà tài nguyên sẽ được áp dụng (ví dụ: "screen" hoặc "print").
  
- **Phương thức**:
  - `setAttribute(name, value)`: Thiết lập giá trị cho thuộc tính của phần tử.
  - `getAttribute(name)`: Lấy giá trị của một thuộc tính đã xác định.

## Ví dụ
### Ví dụ 1: Tạo một phần tử `<link>`
```javascript
const link = document.createElement('link');
link.href = 'styles.css';
link.rel = 'stylesheet';
link.type = 'text/css';
document.head.appendChild(link);
```

### Ví dụ 2: Thay đổi thuộc tính của phần tử `<link>` đã tồn tại
```javascript
const links = document.getElementsByTagName('link');
if (links.length > 0) {
    links[0].href = 'new-styles.css';
}
```

## Giải thích
Khi làm việc với `HTMLLinkElement`, một số điểm cần chú ý bao gồm:
- Đảm bảo rằng bạn đang thay đổi thuộc tính của một phần tử `<link>` đã tồn tại trong DOM.
- Nếu bạn tạo một phần tử `<link>` mới, cần chắc chắn rằng nó được thêm vào DOM trước khi bạn cố gắng truy cập các thuộc tính của nó.
- Thay đổi thuộc tính `href` mà không cập nhật các thuộc tính khác có thể dẫn đến việc trình duyệt không áp dụng các thay đổi đúng cách.

## Tóm tắt một dòng
`HTMLLinkElement` trong JavaScript cho phép bạn thao tác với các phần tử `<link>` trong tài liệu HTML để quản lý và điều chỉnh các liên kết đến tài nguyên bên ngoài.