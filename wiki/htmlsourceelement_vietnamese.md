<!--
Meta Description: # HTMLSourceElement trong JavaScript: Tìm Hiểu và Sử Dụng ## Tóm Tắt `HTMLSourceElement` là một giao diện trong DOM (Document Object Model) đại diện c...
Meta Keywords: video, audio, phần, source, trong
-->

# HTMLSourceElement trong JavaScript: Tìm Hiểu và Sử Dụng

## Tóm Tắt
`HTMLSourceElement` là một giao diện trong DOM (Document Object Model) đại diện cho phần tử `<source>` trong HTML, được sử dụng chủ yếu để cung cấp nguồn cho các phần tử media như `<audio>` và `<video>` trong JavaScript.

## Tài Liệu
### Mục Đích
`HTMLSourceElement` cho phép bạn xác định các nguồn khác nhau cho các tệp âm thanh và video, giúp tối ưu hóa khả năng phát lại trên nhiều trình duyệt và thiết bị. 

### Cách Sử Dụng
Phần tử `<source>` thường được sử dụng bên trong các phần tử `<audio>` hoặc `<video>`. Bạn có thể truy cập và thay đổi thuộc tính của `HTMLSourceElement` thông qua JavaScript.

### Chi Tiết
- **Thuộc tính chính**:
  - `src`: Đường dẫn đến tệp media.
  - `type`: Loại tệp media (ví dụ: `audio/mp3`, `video/mp4`).
- **Phương pháp**: 
  - Bạn có thể thêm hoặc thay đổi phần tử `<source>` bằng JavaScript để thay đổi nguồn media mà không cần phải tải lại toàn bộ phần tử `<audio>` hoặc `<video>`.

## Ví Dụ
Dưới đây là một số ví dụ cơ bản về cách sử dụng `HTMLSourceElement` trong JavaScript:

### Ví dụ 1: Thêm phần tử `<source>` vào `<audio>`
```html
<audio controls>
    <source id="audioSource" src="audio.mp3" type="audio/mp3">
    Your browser does not support the audio element.
</audio>

<script>
    var audioSource = document.getElementById('audioSource');
    audioSource.src = 'new-audio.mp3'; // Thay đổi nguồn âm thanh
</script>
```

### Ví dụ 2: Sử dụng nhiều phần tử `<source>` trong `<video>`
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.ogg" type="video/ogg">
    Your browser does not support the video tag.
</video>

<script>
    // Thay đổi nguồn video
    var video = document.querySelector('video');
    var newSource = document.createElement('source');
    newSource.src = 'new-video.mp4';
    newSource.type = 'video/mp4';
    
    video.appendChild(newSource);
    video.load(); // Tải lại video với nguồn mới
</script>
```

## Giải Thích
- **Lưu Ý Thường Gặp**: Đảm bảo rằng các loại tệp mà bạn cung cấp trong thuộc tính `type` tương thích với các trình duyệt mà bạn nhắm đến. Một số trình duyệt có thể không hỗ trợ tất cả các định dạng media.
- **Ứng Dụng Thực Tế**: Việc sử dụng các phần tử `<source>` giúp tối ưu hóa trải nghiệm người dùng bằng cách cho phép người dùng chọn nguồn phù hợp nhất với thiết bị của họ.

## Tóm Tắt Một Dòng
`HTMLSourceElement` trong JavaScript cho phép bạn quản lý và thay đổi nguồn cho các phần tử media như `<audio>` và `<video>`, nâng cao trải nghiệm phát lại trên nhiều nền tảng.