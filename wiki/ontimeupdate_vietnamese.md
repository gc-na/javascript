<!--
Meta Description: # Sự kiện ontimeupdate trong JavaScript: Cách sử dụng và ví dụ ## Tóm tắt Sự kiện `ontimeupdate` trong JavaScript là một sự kiện quan trọng liên quan ...
Meta Keywords: video, phát, kiện, ontimeupdate, hoặc
-->

# Sự kiện ontimeupdate trong JavaScript: Cách sử dụng và ví dụ

## Tóm tắt
Sự kiện `ontimeupdate` trong JavaScript là một sự kiện quan trọng liên quan đến các phần tử video và audio, được kích hoạt khi thời gian phát của phương tiện thay đổi. Sự kiện này cho phép lập trình viên theo dõi tiến trình phát video hoặc âm thanh, từ đó có thể thực hiện các thao tác tương ứng.

## Tài liệu
### Mục đích
Sự kiện `ontimeupdate` được sử dụng để theo dõi thời gian phát hiện tại của video hoặc âm thanh. Khi sự kiện này xảy ra, nó cho phép bạn thực hiện các hành động như cập nhật giao diện người dùng, hiển thị thông tin tiến độ, hoặc thực hiện các thao tác khác liên quan đến tiến độ phát.

### Cách sử dụng
Sự kiện `ontimeupdate` có thể được gán trực tiếp cho phần tử video hoặc audio trong HTML hoặc thông qua JavaScript. Cú pháp cơ bản là:

```javascript
element.ontimeupdate = function() {
    // Thực hiện hành động khi thời gian phát được cập nhật
};
```

### Chi tiết
Khi thời gian phát của video hoặc âm thanh thay đổi, sự kiện `ontimeupdate` sẽ được kích hoạt. Điều này có thể xảy ra khi người dùng nhấn vào nút phát, tạm dừng, hoặc khi video hoặc âm thanh tự động phát. Bạn có thể sử dụng thuộc tính `currentTime` của phần tử để lấy thời gian phát hiện tại.

## Ví dụ
Dưới đây là một ví dụ đơn giản minh họa cách sử dụng sự kiện `ontimeupdate`:

```html
<video id="myVideo" width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<p id="timeDisplay">Thời gian phát: 0 giây</p>

<script>
    var video = document.getElementById('myVideo');
    var timeDisplay = document.getElementById('timeDisplay');

    video.ontimeupdate = function() {
        timeDisplay.innerHTML = "Thời gian phát: " + Math.floor(video.currentTime) + " giây";
    };
</script>
```

## Giải thích
Một số vấn đề thường gặp khi sử dụng sự kiện `ontimeupdate` bao gồm:

- **Tần suất cập nhật**: Sự kiện này có thể được kích hoạt với tần suất cao, vì vậy bạn nên hạn chế việc thực hiện các hành động nặng nề trong callback của sự kiện để tránh làm chậm hiệu suất.
- **Truy cập thuộc tính `currentTime`**: Nếu bạn không kiểm tra xem video hoặc âm thanh đang ở trạng thái phát hay không, bạn có thể nhận được giá trị không chính xác.
- **Trình duyệt không hỗ trợ**: Đảm bảo rằng trình duyệt của bạn hỗ trợ các phần tử video và audio.

## Tóm tắt một dòng
Sự kiện `ontimeupdate` trong JavaScript giúp theo dõi thời gian phát của video hoặc audio, cho phép lập trình viên thực hiện các hành động tương ứng khi thời gian phát thay đổi.