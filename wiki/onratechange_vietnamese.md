<!--
Meta Description: # Sự kiện onratechange trong JavaScript: Tìm hiểu và Cách sử dụng ## Tóm tắt Sự kiện `onratechange` trong JavaScript được sử dụng để theo dõi khi tốc ...
Meta Keywords: video, kiện, phát, tốc, lại
-->

# Sự kiện onratechange trong JavaScript: Tìm hiểu và Cách sử dụng

## Tóm tắt
Sự kiện `onratechange` trong JavaScript được sử dụng để theo dõi khi tốc độ phát lại của một media (như video hoặc audio) thay đổi. Đây là một sự kiện quan trọng cho các ứng dụng web có tính tương tác cao, giúp tối ưu hóa trải nghiệm người dùng.

## Tài liệu
### Mục đích
Sự kiện `onratechange` được kích hoạt khi thuộc tính `playbackRate` của đối tượng media (video hoặc audio) thay đổi. Điều này rất hữu ích trong các ứng dụng mà người dùng có thể điều chỉnh tốc độ phát lại nội dung.

### Cách sử dụng
Để sử dụng sự kiện `onratechange`, bạn cần:
1. Tạo một đối tượng media (ví dụ: `<video>` hoặc `<audio>`).
2. Gán một hàm xử lý sự kiện cho sự kiện `onratechange`.

**Cú pháp:**
```javascript
mediaElement.onratechange = function() {
    // Code xử lý khi tốc độ phát lại thay đổi
};
```

### Chi tiết
- `mediaElement`: Là phần tử video hoặc audio mà bạn muốn theo dõi.
- Hàm xử lý sự kiện sẽ nhận được một đối tượng sự kiện (event) khi tốc độ phát lại thay đổi.
- Bạn có thể sử dụng thuộc tính `event.target.playbackRate` để lấy tốc độ phát lại mới.

## Ví dụ
### Ví dụ cơ bản
```html
<video id="myVideo" width="400" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support HTML5 video.
</video>

<script>
    const video = document.getElementById('myVideo');

    video.onratechange = function() {
        console.log('Tốc độ phát lại đã thay đổi: ' + video.playbackRate);
    };

    // Thay đổi tốc độ phát lại
    video.playbackRate = 1.5; // Tốc độ 1.5x
</script>
```

## Giải thích
- **Lưu ý:** Không phải tất cả các trình duyệt đều hỗ trợ sự kiện `onratechange`. Hãy kiểm tra tính tương thích trước khi sử dụng.
- **Tốc độ phát lại:** Người dùng có thể thay đổi tốc độ phát lại bằng cách sử dụng các điều khiển trong trình phát media, hoặc bạn có thể thêm các điều khiển tùy chỉnh.
- **Hiệu suất:** Đảm bảo rằng mã xử lý sự kiện không quá nặng, vì nó có thể ảnh hưởng đến hiệu suất phát lại video/audio.

## Tóm tắt một câu
Sự kiện `onratechange` trong JavaScript cho phép bạn theo dõi và xử lý khi tốc độ phát lại của media thay đổi, giúp cải thiện trải nghiệm người dùng trong các ứng dụng web.