<!--
Meta Description: # Sự kiện onUnload trong JavaScript: Tất cả những gì bạn cần biết ## Tóm tắt Sự kiện `onunload` trong JavaScript được sử dụng để thực hiện các hành độ...
Meta Keywords: kiện, người, dùng, trang, onunload
-->

# Sự kiện onUnload trong JavaScript: Tất cả những gì bạn cần biết

## Tóm tắt
Sự kiện `onunload` trong JavaScript được sử dụng để thực hiện các hành động khi người dùng rời khỏi trang web. Điều này có thể bao gồm việc lưu trữ dữ liệu, làm sạch tài nguyên, hoặc thông báo cho người dùng về việc mất dữ liệu.

## Tài liệu
### Mục đích
Sự kiện `onunload` cho phép lập trình viên gán các hàm để thực hiện khi người dùng rời khỏi trang (ví dụ: đóng tab, điều hướng đến trang khác). Đây là một phần quan trọng trong việc quản lý trạng thái ứng dụng và cải thiện trải nghiệm người dùng.

### Cách sử dụng
Để sử dụng sự kiện `onunload`, bạn có thể gán nó cho đối tượng `window` hoặc cho một phần tử cụ thể. Dưới đây là cú pháp cơ bản:

```javascript
window.onunload = function() {
    // Hành động khi người dùng rời khỏi trang
};
```

Bạn cũng có thể sử dụng phương thức `addEventListener` để thêm sự kiện:

```javascript
window.addEventListener('unload', function() {
    // Hành động khi người dùng rời khỏi trang
});
```

### Chi tiết
- **Thuộc tính**: `onunload` là một thuộc tính của đối tượng `window`.
- **Sự kiện**: Khi sự kiện `unload` xảy ra, hệ thống sẽ ngắt kết nối với trang hiện tại, và các hành động đã định nghĩa trong hàm sẽ được thực hiện.
- **Trình duyệt hỗ trợ**: Hầu hết các trình duyệt hiện đại đều hỗ trợ sự kiện này, nhưng hành vi có thể khác nhau giữa các trình duyệt.

## Ví dụ
### Ví dụ cơ bản
```javascript
window.onunload = function() {
    alert("Bạn sắp rời khỏi trang!");
};
```

### Ví dụ sử dụng addEventListener
```javascript
window.addEventListener('unload', function() {
    console.log("Người dùng đã rời khỏi trang.");
});
```

## Giải thích
### Những điều cần lưu ý
- **Hạn chế**: Một số trình duyệt có thể không cho phép hiển thị hộp thoại xác nhận trong sự kiện `onunload` vì lý do trải nghiệm người dùng.
- **Không đồng bộ**: Các hành động không nên thực hiện bất kỳ yêu cầu mạng không đồng bộ nào trong sự kiện `unload`, vì chúng có thể không hoàn thành trước khi trang đóng.
- **Khuyến nghị**: Sử dụng sự kiện `beforeunload` để thông báo cho người dùng trước khi họ rời khỏi trang, vì `unload` không cho người dùng có cơ hội để phản hồi.

## Tóm tắt một dòng
Sự kiện `onunload` trong JavaScript cho phép thực hiện các hành động khi người dùng rời khỏi trang, nhưng cần lưu ý về những hạn chế và hành vi không đồng bộ.