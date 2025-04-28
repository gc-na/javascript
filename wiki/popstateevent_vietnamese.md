<!--
Meta Description: # Sự kiện PopState trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt Sự kiện `PopState` trong JavaScript cho phép bạn xử lý các thay đổi trạng thái của ...
Meta Keywords: kiện, popstate, các, trạng, thái
-->

# Sự kiện PopState trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
Sự kiện `PopState` trong JavaScript cho phép bạn xử lý các thay đổi trạng thái của lịch sử trình duyệt, giúp quản lý các URL và trạng thái ứng dụng một cách hiệu quả khi người dùng điều hướng qua lại giữa các trang.

## Tài liệu
### Mục đích
Sự kiện `PopState` được kích hoạt khi người dùng di chuyển qua lại giữa các trạng thái lịch sử của trang web, chẳng hạn như khi họ nhấn nút "Quay lại" hoặc "Tiến tới" trên trình duyệt. Điều này rất hữu ích trong các ứng dụng một trang (SPA) để cập nhật giao diện người dùng mà không cần tải lại trang.

### Cách sử dụng
Để lắng nghe sự kiện `PopState`, bạn sử dụng phương thức `addEventListener` trên đối tượng `window`. Cú pháp cơ bản như sau:

```javascript
window.addEventListener('popstate', function(event) {
    // Xử lý sự kiện popstate
});
```

### Chi tiết
- **Event Object**: Khi sự kiện `PopState` xảy ra, một đối tượng sự kiện sẽ được truyền vào hàm xử lý, chứa thông tin về trạng thái lịch sử hiện tại.
- **State Property**: Thuộc tính `state` của đối tượng sự kiện chứa dữ liệu mà bạn đã gán cho trạng thái đó thông qua `history.pushState()` hoặc `history.replaceState()`.
- **Lịch sử**: Sự kiện này chỉ xảy ra khi có sự thay đổi trong lịch sử mà bạn đã thêm bằng các phương thức của `History API`.

## Ví dụ
### Ví dụ cơ bản
```javascript
// Thêm một trạng thái mới vào lịch sử
history.pushState({ page: 1 }, "Title 1", "?page=1");

// Lắng nghe sự kiện popstate
window.addEventListener('popstate', function(event) {
    if (event.state) {
        console.log('Trạng thái hiện tại:', event.state);
    } else {
        console.log('Không có trạng thái nào trong lịch sử.');
    }
});

// Giả lập di chuyển qua lại trong lịch sử
history.pushState({ page: 2 }, "Title 2", "?page=2");
history.back();  // Kích hoạt sự kiện popstate
```

## Giải thích
### Những điều cần lưu ý
- **Chỉ hoạt động với `pushState` và `replaceState`**: Sự kiện `PopState` sẽ không được kích hoạt nếu bạn sử dụng các phương thức điều hướng thông thường (như `window.location.href`) để chuyển đổi giữa các trang.
- **Không hoạt động trên các trạng thái ban đầu**: Khi trang đầu tiên được tải, sự kiện `popstate` sẽ không được kích hoạt, chỉ khi có sự thay đổi trạng thái.
- **Hỗ trợ trình duyệt**: Kiểm tra để đảm bảo rằng trình duyệt bạn đang sử dụng hỗ trợ `History API`, đặc biệt là trên các trình duyệt cũ.

## Tóm tắt một dòng
Sự kiện `PopState` trong JavaScript cho phép quản lý trạng thái lịch sử của ứng dụng web, hỗ trợ các thao tác điều hướng mà không cần tải lại trang.