<!--
Meta Description: # AudioScheduledSourceNode trong JavaScript: Cách Sử Dụng và Lợi Ích ## Tóm tắt AudioScheduledSourceNode là một thành phần trong Web Audio API, cho ph...
Meta Keywords: thanh, phát, một, audiocontext, lập
-->

# AudioScheduledSourceNode trong JavaScript: Cách Sử Dụng và Lợi Ích

## Tóm tắt
AudioScheduledSourceNode là một thành phần trong Web Audio API, cho phép lập lịch phát âm thanh và tạo ra âm thanh trong các ứng dụng web.

## Tài liệu
### Mục đích
AudioScheduledSourceNode là lớp cha cho tất cả các nguồn âm thanh có thể được lập lịch trong Web Audio API, như `AudioBufferSourceNode` và `ConstantSourceNode`. Nó cho phép bạn lập lịch thời gian phát âm thanh, giúp tối ưu hóa trải nghiệm âm thanh trong các ứng dụng web.

### Cách sử dụng
Để sử dụng AudioScheduledSourceNode, bạn cần tạo một trong các lớp con của nó. Dưới đây là quy trình cơ bản:

1. Tạo một `AudioContext`.
2. Tạo một `AudioBufferSourceNode` hoặc `ConstantSourceNode` từ `AudioContext`.
3. Lập lịch phát âm thanh bằng các phương thức như `start()` và `stop()`.

### Chi tiết
- **AudioBufferSourceNode**: Dùng để phát âm thanh từ một buffer đã được tải trước.
- **ConstantSourceNode**: Dùng để phát âm thanh liên tục với tần số ổn định.

## Ví dụ
### Ví dụ 1: Phát âm thanh từ AudioBufferSourceNode
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const sourceNode = audioContext.createBufferSource();

// Tải một âm thanh vào buffer
fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    sourceNode.buffer = buffer;
    sourceNode.connect(audioContext.destination);
    sourceNode.start(0); // Bắt đầu phát ngay lập tức
  });
```

### Ví dụ 2: Sử dụng ConstantSourceNode
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const constantSource = audioContext.createConstantSource();
constantSource.offset.value = 0.5; // Tăng âm lượng lên 50%

constantSource.connect(audioContext.destination);
constantSource.start(); // Bắt đầu phát âm thanh liên tục
```

## Giải thích
Một số lưu ý khi làm việc với AudioScheduledSourceNode:
- **Thời gian lập lịch**: Phát âm thanh không thể bắt đầu trước thời điểm hiện tại. Nếu bạn cố gắng lập lịch trước thời điểm này, âm thanh sẽ không phát.
- **Chỉ có thể phát một lần**: AudioBufferSourceNode chỉ có thể được phát một lần. Nếu bạn cần phát lại, bạn cần tạo một instance mới.
- **Quản lý tài nguyên**: Hãy chắc chắn dừng âm thanh khi không cần thiết để giải phóng tài nguyên hệ thống.

## Tóm tắt một dòng
AudioScheduledSourceNode là một phần của Web Audio API cho phép lập lịch và phát âm thanh trong các ứng dụng web một cách linh hoạt và hiệu quả.