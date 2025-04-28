<!--
Meta Description: # SpeechSynthesisUtterance trong JavaScript: Tạo Giọng Nói Từ Văn Bản ## Tóm tắt SpeechSynthesisUtterance là một đối tượng trong JavaScript cho phép p...
Meta Keywords: nói, giọng, utterance, speechsynthesisutterance, javascript
-->

# SpeechSynthesisUtterance trong JavaScript: Tạo Giọng Nói Từ Văn Bản

## Tóm tắt
SpeechSynthesisUtterance là một đối tượng trong JavaScript cho phép phát âm văn bản thông qua công nghệ Text-to-Speech (TTS), tạo ra giọng nói tự động từ nội dung văn bản.

## Tài liệu
### Mục đích
SpeechSynthesisUtterance được sử dụng trong các ứng dụng web để chuyển đổi văn bản thành giọng nói, giúp cải thiện trải nghiệm người dùng và hỗ trợ những người có khó khăn trong việc đọc.

### Cách sử dụng
Để sử dụng SpeechSynthesisUtterance, bạn cần làm theo các bước sau:

1. **Tạo đối tượng SpeechSynthesisUtterance**: Khởi tạo một đối tượng mới bằng cách truyền văn bản mà bạn muốn phát âm.

   ```javascript
   const utterance = new SpeechSynthesisUtterance('Chào mừng bạn đến với JavaScript!');
   ```

2. **Tùy chỉnh thuộc tính**: Bạn có thể thay đổi các thuộc tính như giọng nói, tốc độ, âm lượng và cao độ của giọng nói.

   ```javascript
   utterance.voice = speechSynthesis.getVoices()[0]; // Chọn giọng nói
   utterance.rate = 1; // Tốc độ nói
   utterance.pitch = 1; // Cao độ
   utterance.volume = 1; // Âm lượng (0.0 đến 1.0)
   ```

3. **Phát âm**: Sử dụng phương thức `speechSynthesis.speak()` để phát âm văn bản.

   ```javascript
   speechSynthesis.speak(utterance);
   ```

### Chi tiết
- **Phương thức**: `speechSynthesis.speak(utterance)` sẽ bắt đầu phát âm văn bản.
- **Thuộc tính**:
  - `text`: Văn bản cần phát âm.
  - `voice`: Giọng nói được sử dụng để phát âm.
  - `rate`: Tốc độ nói (0.1 đến 10).
  - `pitch`: Cao độ giọng nói (0 đến 2).
  - `volume`: Âm lượng giọng nói (0.0 đến 1.0).

## Ví dụ
### Ví dụ cơ bản
```javascript
if ('speechSynthesis' in window) {
    const utterance = new SpeechSynthesisUtterance('Xin chào! Đây là một ví dụ về SpeechSynthesisUtterance.');
    speechSynthesis.speak(utterance);
} else {
    console.log('Trình duyệt của bạn không hỗ trợ Speech Synthesis.');
}
```

### Tùy chỉnh giọng nói
```javascript
const utterance = new SpeechSynthesisUtterance('Tôi thích học JavaScript!');
const voices = speechSynthesis.getVoices();
utterance.voice = voices.find(voice => voice.name === 'Google Tiếng Việt'); // Chọn giọng nói tiếng Việt
utterance.rate = 1.2; // Tốc độ hơi nhanh
speechSynthesis.speak(utterance);
```

## Giải thích
- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ SpeechSynthesis. Hãy kiểm tra tính khả dụng trước khi sử dụng.
- **Giọng nói không có sẵn**: Danh sách giọng nói có thể khác nhau giữa các trình duyệt và hệ điều hành. Sử dụng `speechSynthesis.getVoices()` để lấy danh sách giọng nói hiện có.
- **Thời gian tải giọng nói**: Có thể mất một khoảng thời gian để tải danh sách giọng nói, vì vậy hãy đảm bảo thực hiện kiểm tra sau khi danh sách đã được tải xong.

## Tóm tắt một dòng
SpeechSynthesisUtterance trong JavaScript cho phép bạn chuyển đổi văn bản thành giọng nói, cung cấp trải nghiệm tương tác cho người dùng.