<!--
Meta Description: # Tài liệu về Âm Thanh trong JavaScript ## Tóm tắt JavaScript cung cấp các API mạnh mẽ để làm việc với âm thanh, cho phép các nhà phát triển chơi, dừn...
Meta Keywords: thanh, audio, javascript, phát, bạn
-->

# Tài liệu về Âm Thanh trong JavaScript

## Tóm tắt
JavaScript cung cấp các API mạnh mẽ để làm việc với âm thanh, cho phép các nhà phát triển chơi, dừng và điều chỉnh âm thanh trong ứng dụng web của họ thông qua các đối tượng như `Audio` và `AudioContext`.

## Tài liệu

### Mục đích
Âm thanh trong JavaScript cho phép người dùng tích hợp âm nhạc và hiệu ứng âm thanh vào trang web, tạo ra trải nghiệm người dùng phong phú hơn.

### Cách sử dụng
Đối tượng `Audio` trong JavaScript cho phép bạn tạo và quản lý âm thanh. Bạn có thể sử dụng nó để tải và phát các tệp âm thanh.

#### Khởi tạo
```javascript
const audio = new Audio('path/to/your/audiofile.mp3');
```

#### Phát âm thanh
```javascript
audio.play();
```

#### Dừng âm thanh
```javascript
audio.pause();
```

#### Điều chỉnh âm lượng
```javascript
audio.volume = 0.5; // Giá trị từ 0.0 đến 1.0
```

#### Thêm sự kiện
Bạn có thể thêm các sự kiện như `ended` để thực hiện hành động khi âm thanh kết thúc:
```javascript
audio.addEventListener('ended', () => {
    console.log('Âm thanh đã kết thúc.');
});
```

## Ví dụ

### Phát âm thanh khi nhấn nút
```html
<button id="playButton">Phát âm thanh</button>
<script>
    const audio = new Audio('path/to/your/audiofile.mp3');
    document.getElementById('playButton').addEventListener('click', () => {
        audio.play();
    });
</script>
```

### Dừng âm thanh
```html
<button id="stopButton">Dừng âm thanh</button>
<script>
    const audio = new Audio('path/to/your/audiofile.mp3');
    audio.play();
    document.getElementById('stopButton').addEventListener('click', () => {
        audio.pause();
    });
</script>
```

## Giải thích
Một số điểm cần lưu ý khi làm việc với âm thanh trong JavaScript:

- **CORS**: Nếu bạn tải âm thanh từ một nguồn khác (không phải cùng miền), bạn cần đảm bảo rằng máy chủ hỗ trợ CORS.
- **Tự động phát**: Nhiều trình duyệt hiện nay chặn âm thanh tự động phát mà không có tương tác của người dùng, vì vậy bạn nên đảm bảo rằng âm thanh được phát sau một hành động như nhấn nút.
- **Định dạng tệp**: Đảm bảo rằng định dạng âm thanh bạn sử dụng được hỗ trợ bởi trình duyệt (như MP3, WAV, OGG).

## Tóm tắt một dòng
JavaScript cho phép bạn tạo và quản lý âm thanh dễ dàng thông qua đối tượng `Audio`, giúp cải thiện trải nghiệm người dùng trên các trang web.