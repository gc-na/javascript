<!--
Meta Description: # Sự kiện onended trong JavaScript: Hiểu biết và Cách Sử Dụng ## Tóm tắt Sự kiện `onended` trong JavaScript được sử dụng để xử lý khi một phương thức ...
Meta Keywords: kiện, onended, phát, audio, khi
-->

# Sự kiện onended trong JavaScript: Hiểu biết và Cách Sử Dụng

## Tóm tắt
Sự kiện `onended` trong JavaScript được sử dụng để xử lý khi một phương thức phát video hoặc âm thanh kết thúc. Đây là một sự kiện quan trọng trong việc tạo ra các ứng dụng đa phương tiện, cho phép lập trình viên thực hiện các hành động cần thiết ngay sau khi nội dung phát hoàn tất.

## Tài liệu
### Mục đích
Sự kiện `onended` thuộc về đối tượng `HTMLMediaElement`, bao gồm các thẻ `<audio>` và `<video>`. Nó được kích hoạt khi phát lại âm thanh hoặc video đã hoàn tất, cho phép lập trình viên thực hiện các hành động như tự động phát lại, thông báo cho người dùng, hoặc chuyển sang nội dung khác.

### Cách sử dụng
Để sử dụng sự kiện `onended`, bạn có thể gán một hàm xử lý sự kiện cho thuộc tính `onended` của đối tượng media. Dưới đây là cú pháp cơ bản:

```javascript
var mediaElement = document.querySelector('audio'); // hoặc 'video'
mediaElement.onended = function() {
    // Hành động khi phát hoàn tất
    console.log('Phát hoàn tất!');
};
```

### Chi tiết
- **Tham số:** Không có tham số nào được truyền vào hàm xử lý.
- **Tính tương thích:** Sự kiện `onended` được hỗ trợ trên hầu hết các trình duyệt hiện đại.
- **Lưu ý:** Nếu bạn đã thiết lập các sự kiện khác như `onpause` hoặc `onstop`, hãy đảm bảo rằng chúng không xung đột với sự kiện `onended`.

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng sự kiện `onended`:

```html
<audio controls>
    <source src="audio-file.mp3" type="audio/mpeg">
    Trình duyệt của bạn không hỗ trợ thẻ audio.
</audio>

<script>
    var audio = document.querySelector('audio');
    audio.onended = function() {
        alert('Âm thanh đã phát xong!');
    };
</script>
```

Trong ví dụ trên, khi âm thanh phát kết thúc, một thông báo sẽ xuất hiện.

## Giải thích
### Những điều cần lưu ý
- **Kết nối sự kiện:** Đảm bảo rằng bạn đã kết nối sự kiện `onended` sau khi đã khởi tạo phần tử media để tránh lỗi không kích hoạt.
- **Xử lý nhiều sự kiện:** Nếu bạn cần thực hiện nhiều hành động khi phát hoàn tất, hãy xem xét sử dụng `addEventListener` thay vì gán trực tiếp cho `onended`.

```javascript
audio.addEventListener('ended', function() {
    console.log('Phát âm thanh đã hoàn tất!');
    // Thực hiện các hành động khác ở đây
});
```

### Những lỗi thường gặp
- **Không kích hoạt sự kiện:** Nếu bạn không thấy sự kiện `onended` được kích hoạt, hãy kiểm tra xem âm thanh hoặc video có thực sự phát hết không.
- **Xung đột sự kiện:** Đảm bảo rằng không có sự kiện nào khác ngăn cản sự kiện `onended` được thực thi.

## Tóm tắt một dòng
Sự kiện `onended` trong JavaScript cho phép bạn thực hiện các hành động khi phát video hoặc âm thanh kết thúc, là một phần quan trọng trong việc quản lý nội dung đa phương tiện trên web.