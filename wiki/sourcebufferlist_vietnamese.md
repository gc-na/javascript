<!--
Meta Description: # SourceBufferList trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng ## Tóm tắt `SourceBufferList` là một đối tượng trong JavaScript, thuộc về Web API, c...
Meta Keywords: sourcebuffer, mediasource, một, sourcebufferlist, các
-->

# SourceBufferList trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng

## Tóm tắt
`SourceBufferList` là một đối tượng trong JavaScript, thuộc về Web API, cho phép quản lý danh sách các `SourceBuffer` trong một `MediaSource`, giúp xử lý và phát các đoạn video và âm thanh một cách hiệu quả.

## Tài liệu
### Mục đích
`SourceBufferList` là một phần của API Media Source Extensions (MSE) trong JavaScript, cho phép lập trình viên thao tác với các nguồn phát media. Đối tượng này chứa danh sách các `SourceBuffer` đã được tạo ra từ một `MediaSource`, hỗ trợ việc thêm, xóa và truy cập các `SourceBuffer`.

### Cách sử dụng
Để sử dụng `SourceBufferList`, bạn cần tạo một đối tượng `MediaSource` và sau đó thêm các `SourceBuffer` vào đó. Dưới đây là quy trình cơ bản:

1. Tạo một đối tượng `MediaSource`.
2. Sử dụng phương thức `addSourceBuffer()` để thêm các `SourceBuffer` vào `MediaSource`.
3. Truy cập danh sách các `SourceBuffer` qua thuộc tính `sourceBuffers`.

### Chi tiết
- **Thuộc tính**: 
  - `length`: Trả về số lượng `SourceBuffer` trong danh sách.
  
- **Phương thức**:
  - `item(index)`: Trả về `SourceBuffer` tại vị trí chỉ định trong danh sách.
  
- **Mô tả**: 
  - `SourceBufferList` không trực tiếp được tạo ra, mà nó được sinh ra khi bạn gọi `addSourceBuffer()` trên một đối tượng `MediaSource`. 
  - Ví dụ, nếu bạn thêm hai `SourceBuffer`, bạn có thể truy cập chúng qua `sourceBuffers[0]` và `sourceBuffers[1]`.

## Ví dụ
Dưới đây là một ví dụ đơn giản về việc tạo một `MediaSource` và thêm một `SourceBuffer` vào đó:

```javascript
// Tạo đối tượng MediaSource
const mediaSource = new MediaSource();

// Thêm sự kiện để xử lý khi MediaSource sẵn sàng
mediaSource.addEventListener('sourceopen', function() {
    // Thêm SourceBuffer
    const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.64001E, mp4a.40.2"');
    
    // Kiểm tra danh sách SourceBuffer
    const sourceBufferList = mediaSource.sourceBuffers;
    console.log(sourceBufferList.length); // In ra số lượng SourceBuffer
});
```

## Giải thích
- **Cạm bẫy phổ biến**: 
  - Đảm bảo rằng `MediaSource` đã được mở trước khi thêm `SourceBuffer`, nếu không sẽ dẫn đến lỗi.
  - Kiểm tra định dạng MIME của `SourceBuffer` để đảm bảo nó hỗ trợ loại video hoặc âm thanh mà bạn đang cố gắng phát.

- **Ghi chú bổ sung**: 
  - `SourceBufferList` không có khả năng bị thay đổi trực tiếp, vì vậy bạn cần quản lý `SourceBuffer` thông qua phương thức của `MediaSource`.

## Tóm tắt một dòng
`SourceBufferList` trong JavaScript là danh sách các `SourceBuffer` trong một `MediaSource`, cho phép quản lý hiệu quả việc phát media.