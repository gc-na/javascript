<!--
Meta Description: # SpeechSynthesisVoice trong JavaScript: Tạo Giọng Nói Tự Nhiên cho Ứng Dụng Web ## Tóm tắt `SpeechSynthesisVoice` là một giao diện trong API Speech S...
Meta Keywords: giọng, nói, dụng, các, cho
-->

# SpeechSynthesisVoice trong JavaScript: Tạo Giọng Nói Tự Nhiên cho Ứng Dụng Web

## Tóm tắt
`SpeechSynthesisVoice` là một giao diện trong API Speech Synthesis của JavaScript, cho phép lập trình viên truy cập các giọng nói có sẵn trên thiết bị và sử dụng chúng để chuyển đổi văn bản thành giọng nói trong các ứng dụng web.

## Tài liệu
### Mục đích
`SpeechSynthesisVoice` cho phép bạn lấy thông tin về các giọng nói khác nhau mà API Speech Synthesis có thể sử dụng để phát âm văn bản. Nó cung cấp thông tin như tên, ngôn ngữ, và các đặc điểm khác của giọng nói.

### Cách sử dụng
Để sử dụng `SpeechSynthesisVoice`, bạn cần truy cập vào đối tượng `speechSynthesis` trong trình duyệt. Bạn có thể liệt kê các giọng nói khả dụng bằng cách sử dụng phương thức `getVoices()` và sau đó chọn một giọng nói cụ thể để sử dụng cho việc phát âm.

### Chi tiết
Mỗi đối tượng `SpeechSynthesisVoice` bao gồm các thuộc tính sau:
- `name`: Tên của giọng nói.
- `lang`: Mã ngôn ngữ (ví dụ: "en-US" cho tiếng Anh - Hoa Kỳ).
- `default`: Một giá trị boolean cho biết liệu giọng nói này có phải là giọng nói mặc định hay không.
- `uri`: Đường dẫn đến giọng nói.

Để lấy danh sách giọng nói có sẵn, bạn có thể sử dụng đoạn mã sau:

```javascript
const voices = speechSynthesis.getVoices();
```

Sau khi có danh sách giọng nói, bạn có thể tạo một đối tượng `SpeechSynthesisUtterance` và gán giọng nói cụ thể cho nó như sau:

```javascript
const utterance = new SpeechSynthesisUtterance("Xin chào, đây là một ví dụ về giọng nói.");
const selectedVoice = voices.find(voice => voice.name === 'Google Tiếng Việt');
utterance.voice = selectedVoice;
speechSynthesis.speak(utterance);
```

## Ví dụ
### Ví dụ cơ bản
```javascript
// Lấy các giọng nói có sẵn
const voices = speechSynthesis.getVoices();

// Tạo một đối tượng SpeechSynthesisUtterance
const utterance = new SpeechSynthesisUtterance("Chào mừng bạn đến với JavaScript!");

// Chọn giọng nói
const selectedVoice = voices.find(voice => voice.lang === 'vi-VN');
utterance.voice = selectedVoice;

// Phát âm
speechSynthesis.speak(utterance);
```

## Giải thích
Khi sử dụng `SpeechSynthesisVoice`, có một số điều cần lưu ý:
- Danh sách giọng nói có thể không được tải ngay lập tức. Bạn có thể cần lắng nghe sự kiện `voiceschanged` để đảm bảo rằng danh sách giọng nói đã sẵn sàng trước khi truy cập.
- Không phải tất cả các giọng nói đều hỗ trợ tất cả các ngôn ngữ. Hãy kiểm tra thuộc tính `lang` để đảm bảo rằng bạn chọn giọng nói phù hợp cho ngôn ngữ bạn muốn sử dụng.
- Một số thiết bị hoặc trình duyệt có thể không hỗ trợ tất cả các giọng nói, vì vậy hãy đảm bảo kiểm tra tính khả dụng.

## Tóm tắt một dòng
`SpeechSynthesisVoice` trong JavaScript cho phép truy cập và sử dụng các giọng nói khác nhau để chuyển đổi văn bản thành giọng nói trong ứng dụng web.