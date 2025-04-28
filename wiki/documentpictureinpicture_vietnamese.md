<!--
Meta Description: # DocumentPictureInPicture: Tính năng Hình trong Hình trong JavaScript ## Tóm tắt `DocumentPictureInPicture` là một tính năng trong JavaScript cho phé...
Meta Keywords: video, trong, hình, chế, documentpictureinpicture
-->

# DocumentPictureInPicture: Tính năng Hình trong Hình trong JavaScript

## Tóm tắt
`DocumentPictureInPicture` là một tính năng trong JavaScript cho phép các phần tử video được phát trong chế độ hình trong hình (Picture-in-Picture - PiP), giúp người dùng có thể xem video đồng thời với việc thực hiện các tác vụ khác trên trang web.

## Tài liệu
### Mục đích
Tính năng `DocumentPictureInPicture` được thiết kế để cải thiện trải nghiệm người dùng bằng cách cho phép phát video trong một cửa sổ nhỏ hơn, có thể di chuyển được, nằm trên các nội dung khác của trang web.

### Cách sử dụng
Để sử dụng `DocumentPictureInPicture`, bạn cần gọi phương thức `requestPictureInPicture()` trên một phần tử video. Dưới đây là cú pháp cơ bản:

```javascript
element.requestPictureInPicture().then().catch();
```

### Chi tiết
- `element`: Phần tử video mà bạn muốn phát trong chế độ PiP.
- `requestPictureInPicture()`: Phương thức này trả về một Promise. Khi thành công, video sẽ được phát trong chế độ PiP.
- Nếu có lỗi, phương thức sẽ ném ra một lỗi mà bạn có thể xử lý bằng cách sử dụng `.catch()`.

## Ví dụ
Dưới đây là ví dụ cơ bản về cách sử dụng `DocumentPictureInPicture`:

```html
<video id="video" controls>
  <source src="video.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
<button id="pipButton">Bật Hình trong Hình</button>

<script>
  const video = document.getElementById('video');
  const pipButton = document.getElementById('pipButton');

  pipButton.addEventListener('click', async () => {
    try {
      if (document.pictureInPictureElement) {
        await document.exitPictureInPicture();
      } else {
        await video.requestPictureInPicture();
      }
    } catch (error) {
      console.error('Lỗi khi bật chế độ Hình trong Hình:', error);
    }
  });
</script>
```

## Giải thích
Một số điều cần lưu ý khi sử dụng `DocumentPictureInPicture`:

- **Trình duyệt hỗ trợ**: Tính năng này có thể không được hỗ trợ trên tất cả các trình duyệt. Bạn nên kiểm tra khả năng tương thích trước khi triển khai.
- **Quyền truy cập**: Người dùng cần cho phép video phát trong chế độ PiP. Trình duyệt có thể yêu cầu người dùng thực hiện hành động (như nhấp chuột) để khởi động chế độ này.
- **Đóng chế độ PiP**: Người dùng có thể thoát chế độ PiP bằng cách nhấp vào cửa sổ PiP hoặc sử dụng `document.exitPictureInPicture()`.

## Tóm tắt một dòng
`DocumentPictureInPicture` trong JavaScript cho phép phát video trong chế độ Hình trong Hình, mang lại trải nghiệm xem đồng thời và thuận tiện cho người dùng.