<!--
Meta Description: # NavigationHistoryEntry trong JavaScript: Quản lý Lịch sử Điều hướng ## Tóm Tắt `NavigationHistoryEntry` là một đối tượng trong JavaScript cho phép l...
Meta Keywords: trong, lịch, của, các, thông
-->

# NavigationHistoryEntry trong JavaScript: Quản lý Lịch sử Điều hướng

## Tóm Tắt
`NavigationHistoryEntry` là một đối tượng trong JavaScript cho phép lập trình viên truy cập và quản lý thông tin liên quan đến lịch sử điều hướng trong các ứng dụng web, giúp cải thiện trải nghiệm người dùng.

## Tài Liệu
### Mục Đích
`NavigationHistoryEntry` được sử dụng để lấy thông tin về các trang mà người dùng đã truy cập trong lịch sử điều hướng của trình duyệt. Đối tượng này cho phép lập trình viên truy cập các thuộc tính của các mục trong lịch sử, chẳng hạn như URL, tiêu đề, và trạng thái.

### Cách Sử Dụng
Đối tượng `NavigationHistoryEntry` có thể được sử dụng thông qua API `window.history` trong JavaScript. Bạn có thể truy cập các mục lịch sử thông qua các phương thức như `history.back()`, `history.forward()`, và `history.go()` để di chuyển qua lại giữa các mục lịch sử.

### Chi Tiết
- **Khởi Tạo**: `NavigationHistoryEntry` không được khởi tạo trực tiếp mà được tạo ra bởi trình duyệt khi người dùng điều hướng.
- **Thuộc Tính**:
  - `url`: URL hiện tại của mục trong lịch sử.
  - `title`: Tiêu đề của trang tương ứng với URL.
  - `state`: Trạng thái của mục trong lịch sử, có thể chứa thông tin bổ sung.

## Ví Dụ
### Ví dụ 1: Lấy thông tin về URL hiện tại
```javascript
// Lấy URL hiện tại từ đối tượng history
let currentUrl = window.location.href;
console.log(currentUrl);
```

### Ví dụ 2: Quay lại trang trước đó
```javascript
// Quay lại trang trước đó trong lịch sử
window.history.back();
```

### Ví dụ 3: Di chuyển tới một trang cụ thể trong lịch sử
```javascript
// Di chuyển đến trang thứ ba trong lịch sử
window.history.go(-2);
```

## Giải Thích
- **Nhầm Lẫn Về Trạng Thái**: Người dùng có thể gặp khó khăn trong việc hiểu trạng thái của các mục lịch sử, vì trạng thái có thể không luôn luôn rõ ràng.
- **Lỗi Truy Cập**: Một số thuộc tính của `NavigationHistoryEntry` có thể không khả dụng trong tất cả các trình duyệt hoặc trong một số điều kiện nhất định.
- **Bảo Mật**: Đảm bảo rằng bạn không cố gắng thu thập thông tin nhạy cảm từ lịch sử điều hướng của người dùng mà không có sự đồng ý của họ.

## Tóm Tắt Một Dòng
`NavigationHistoryEntry` trong JavaScript cho phép lập trình viên quản lý và truy cập thông tin về lịch sử điều hướng của người dùng, nâng cao trải nghiệm sử dụng ứng dụng web.