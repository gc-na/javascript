<!--
Meta Description: # Sự kiện ondurationchange trong JavaScript: Hướng dẫn đầy đủ ## Tóm tắt Sự kiện `ondurationchange` trong JavaScript được sử dụng để theo dõi sự thay ...
Meta Keywords: kiện, dài, video, thay, đổi
-->

# Sự kiện ondurationchange trong JavaScript: Hướng dẫn đầy đủ

## Tóm tắt
Sự kiện `ondurationchange` trong JavaScript được sử dụng để theo dõi sự thay đổi độ dài của một phương tiện (như video hoặc âm thanh) trong tài liệu HTML5. Sự kiện này cho phép lập trình viên nhận biết khi độ dài của phương tiện đã được cập nhật, từ đó có thể thực hiện các hành động phù hợp.

## Tài liệu
### Mục đích
Sự kiện `ondurationchange` được kích hoạt khi độ dài của một phương tiện thay đổi, thường là khi thông tin về độ dài được nhận từ máy chủ hoặc khi người dùng thay đổi độ dài của phương tiện.

### Cách sử dụng
Sự kiện này thường được sử dụng với các phần tử `<audio>` hoặc `<video>` trong HTML5. Để sử dụng sự kiện này, bạn có thể gán một hàm xử lý sự kiện cho thuộc tính `ondurationchange` của phần tử.

### Cấu trúc
```javascript
element.ondurationchange = function() {
    // mã xử lý khi độ dài thay đổi
};
```

### Ví dụ
Dưới đây là một số ví dụ đơn giản về cách sử dụng sự kiện `ondurationchange`:

#### Ví dụ 1: Thay đổi độ dài video
```html
<video id="myVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Trình duyệt của bạn không hỗ trợ video.
</video>

<script>
    const video = document.getElementById('myVideo');
    video.ondurationchange = function() {
        console.log('Độ dài video đã thay đổi: ' + video.duration + ' giây');
    };
</script>
```

#### Ví dụ 2: Thay đổi độ dài âm thanh
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mp3">
    Trình duyệt của bạn không hỗ trợ âm thanh.
</audio>

<script>
    const audio = document.getElementById('myAudio');
    audio.ondurationchange = function() {
        console.log('Độ dài âm thanh đã thay đổi: ' + audio.duration + ' giây');
    };
</script>
```

## Giải thích
### Những điểm cần lưu ý
- **Không phải lúc nào cũng thay đổi**: Sự kiện `ondurationchange` không được kích hoạt trong mọi trường hợp. Ví dụ, nếu độ dài của phương tiện không thay đổi, sự kiện sẽ không được gọi.
- **Hỗ trợ trình duyệt**: Hầu hết các trình duyệt hiện đại đều hỗ trợ sự kiện này, nhưng bạn nên kiểm tra tính tương thích nếu dự án của bạn cần hỗ trợ trình duyệt cũ hơn.
- **Tối ưu hiệu suất**: Nếu bạn thực hiện nhiều thao tác khi sự kiện này xảy ra, hãy đảm bảo rằng mã của bạn được tối ưu hóa để tránh gây ra lag hoặc giảm hiệu suất.

## Tóm tắt một câu
Sự kiện `ondurationchange` trong JavaScript cho phép lập trình viên theo dõi và xử lý thay đổi độ dài của phương tiện đa phương tiện trong HTML5.