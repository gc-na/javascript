<!--
Meta Description: # TextTrackList trong JavaScript: Hướng dẫn chi tiết và ví dụ ## Tóm tắt TextTrackList là một đối tượng trong JavaScript, được sử dụng để quản lý danh...
Meta Keywords: track, video, các, bản, văn
-->

# TextTrackList trong JavaScript: Hướng dẫn chi tiết và ví dụ

## Tóm tắt
TextTrackList là một đối tượng trong JavaScript, được sử dụng để quản lý danh sách các track văn bản trong các phần tử video hoặc audio, như phụ đề hoặc chú thích.

## Tài liệu
TextTrackList là một giao diện trong API HTML5, cho phép truy cập và quản lý các track văn bản liên quan đến các phần tử media (như `<video>` và `<audio>`). Đối tượng này chứa một danh sách các đối tượng TextTrack, mỗi đối tượng đại diện cho một track văn bản cụ thể, ví dụ như phụ đề, chú thích, hay ngôn ngữ dịch.

### Mục đích
Mục đích chính của TextTrackList là cung cấp một cách dễ dàng để lấy thông tin về các track văn bản có sẵn và cho phép người dùng tùy chỉnh việc hiển thị chúng.

### Cách sử dụng
Để sử dụng TextTrackList, bạn cần truy cập thuộc tính `textTracks` của phần tử video hoặc audio. Dưới đây là cú pháp cơ bản:

```javascript
let videoElement = document.querySelector('video');
let trackList = videoElement.textTracks;
```

### Chi tiết
- **Các thuộc tính**:
  - `length`: Trả về số lượng track văn bản trong danh sách.
  - `item(index)`: Trả về track văn bản tại vị trí chỉ định.
  - `getTrackById(id)`: Trả về track văn bản dựa trên ID của nó.

- **Sự kiện**:
  - `change`: Sự kiện này được kích hoạt khi danh sách track thay đổi.

## Ví dụ
### Ví dụ cơ bản
```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English">
  <track src="subtitles_vi.vtt" kind="subtitles" srclang="vi" label="Tiếng Việt">
  Your browser does not support the video tag.
</video>

<script>
  let video = document.querySelector('video');
  let textTracks = video.textTracks;

  for (let i = 0; i < textTracks.length; i++) {
    console.log(`Track ${i}: ${textTracks[i].label}`);
  }
</script>
```

### Ví dụ lấy track theo ID
```javascript
let trackById = textTracks.getTrackById('track-id');
console.log(`Track found: ${trackById.label}`);
```

## Giải thích
Khi làm việc với TextTrackList, người lập trình cần chú ý đến một số vấn đề sau:
- **Trình duyệt không hỗ trợ**: Không phải tất cả các trình duyệt đều hỗ trợ đầy đủ API này. Hãy kiểm tra tính tương thích trước khi sử dụng.
- **Thay đổi track**: Khi track được thay đổi (thêm hoặc xóa), sự kiện `change` sẽ được kích hoạt. Điều này có thể ảnh hưởng đến cách bạn quản lý giao diện người dùng.
- **Trạng thái track**: Mỗi track có thể có trạng thái khác nhau như 'showing', 'hidden', hoặc 'disabled'. Cần kiểm tra trạng thái này trước khi thao tác với track.

## Tóm tắt ngắn gọn
TextTrackList trong JavaScript cho phép bạn quản lý và truy vấn danh sách các track văn bản trong các phần tử media như video và audio.