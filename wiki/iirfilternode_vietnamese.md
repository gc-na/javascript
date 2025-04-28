<!--
Meta Description: # IIRFilterNode: Lọc Tín Hiệu Trong JavaScript ## Tóm tắt IIRFilterNode là một phần của Web Audio API, cho phép lập trình viên áp dụng bộ lọc vô hạn (...
Meta Keywords: iirfilternode, thanh, lọc, một, audiocontext
-->

# IIRFilterNode: Lọc Tín Hiệu Trong JavaScript

## Tóm tắt
IIRFilterNode là một phần của Web Audio API, cho phép lập trình viên áp dụng bộ lọc vô hạn (IIR) cho tín hiệu âm thanh trong các ứng dụng web. Nó giúp xử lý và điều chỉnh âm thanh một cách linh hoạt và hiệu quả.

## Tài liệu

### Mục đích
IIRFilterNode được sử dụng để thực hiện các phép lọc tín hiệu âm thanh, như lọc cao tần, lọc thấp tần, hoặc lọc thông tần, cho phép người dùng kiểm soát tần số và độ khuếch đại của âm thanh.

### Cách sử dụng
Để sử dụng IIRFilterNode, bạn cần tạo một đối tượng AudioContext và sau đó tạo một IIRFilterNode bằng phương thức `createIIRFilter`. Dưới đây là cú pháp cơ bản:

```javascript
const audioContext = new AudioContext();
const feedbackCoefficients = [0.5, 0.5];
const feedforwardCoefficients = [1.0, 0.0];
const iirFilterNode = audioContext.createIIRFilter(feedforwardCoefficients, feedbackCoefficients);
```

### Chi tiết
- **feedforwardCoefficients**: Là một mảng số đại diện cho các hệ số của bộ lọc.
- **feedbackCoefficients**: Là một mảng số đại diện cho các hệ số phản hồi.

IIRFilterNode có thể được kết nối với các node âm thanh khác, như AudioBufferSourceNode hoặc GainNode, để thực hiện các thao tác xử lý âm thanh phức tạp hơn.

## Ví dụ

### Ví dụ Cơ Bản
Dưới đây là một ví dụ đơn giản về cách sử dụng IIRFilterNode để lọc âm thanh:

```javascript
const audioContext = new AudioContext();
const source = audioContext.createBufferSource();

// Tải âm thanh vào buffer
fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    source.buffer = buffer;

    const feedbackCoefficients = [0.5, 0.5];
    const feedforwardCoefficients = [1.0, 0.0];
    const iirFilterNode = audioContext.createIIRFilter(feedforwardCoefficients, feedbackCoefficients);

    // Kết nối các node
    source.connect(iirFilterNode);
    iirFilterNode.connect(audioContext.destination);
    
    // Phát âm thanh
    source.start();
  });
```

## Giải thích
Khi sử dụng IIRFilterNode, có một số điều cần lưu ý:
- **Hiệu suất**: Bộ lọc IIR có thể tiêu tốn tài nguyên CPU. Việc tối ưu hóa các hệ số có thể cải thiện hiệu suất.
- **Tương thích**: Không phải tất cả trình duyệt đều hỗ trợ IIRFilterNode. Kiểm tra tính tương thích trước khi triển khai.
- **Cách tính toán**: Các hệ số không được vượt quá giá trị 1.0, điều này có thể gây ra âm thanh méo mó.

## Tóm tắt một dòng
IIRFilterNode là một node trong Web Audio API cho phép áp dụng bộ lọc vô hạn cho tín hiệu âm thanh trong JavaScript, giúp điều chỉnh và xử lý âm thanh linh hoạt.