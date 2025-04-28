<!--
Meta Description: # SpeechSynthesis trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm tắt SpeechSynthesis là một API trong JavaScript cho phép trình duyệt phát âm văn bản bằn...
Meta Keywords: speechsynthesis, giọng, nói, một, phát
-->

# SpeechSynthesis trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm tắt
SpeechSynthesis là một API trong JavaScript cho phép trình duyệt phát âm văn bản bằng giọng nói nhân tạo. Tính năng này giúp người dùng tương tác với ứng dụng web thông qua âm thanh, làm tăng trải nghiệm người dùng.

## Tài liệu
SpeechSynthesis là một phần của Web Speech API, cho phép các nhà phát triển tích hợp khả năng đọc văn bản trong ứng dụng web của họ. API này cung cấp các phương thức và thuộc tính để điều khiển việc phát âm văn bản, thay đổi giọng nói, tốc độ và âm lượng.

### Cách sử dụng
Để sử dụng SpeechSynthesis, bạn cần tạo một đối tượng `SpeechSynthesisUtterance` và truyền chuỗi văn bản cần phát âm. Sau đó, bạn có thể sử dụng đối tượng `speechSynthesis` để phát âm văn bản.

### Ví dụ cơ bản
```javascript
// Tạo một đối tượng SpeechSynthesisUtterance
const utterance = new SpeechSynthesisUtterance("Xin chào, tôi là một giọng nói nhân tạo.");

// Thiết lập giọng nói, tốc độ và âm lượng (tuỳ chọn)
utterance.voice = speechSynthesis.getVoices()[0]; // Chọn giọng nói đầu tiên
utterance.rate = 1; // Tốc độ (1 là bình thường)
utterance.volume = 1; // Âm lượng (0 đến 1)

// Phát âm văn bản
speechSynthesis.speak(utterance);
```

## Giải thích
Khi sử dụng SpeechSynthesis, có một số điểm cần lưu ý:
- **Giọng nói**: Không phải tất cả các trình duyệt đều hỗ trợ cùng một loại giọng nói. Bạn có thể sử dụng `speechSynthesis.getVoices()` để kiểm tra các giọng nói có sẵn.
- **Tốc độ và âm lượng**: Tốc độ phát âm có thể ảnh hưởng đến trải nghiệm nghe. Tốc độ 1 là bình thường, nhưng bạn có thể điều chỉnh theo nhu cầu.
- **Trình duyệt hỗ trợ**: Đảm bảo rằng bạn kiểm tra khả năng hỗ trợ của trình duyệt vì không phải tất cả các trình duyệt đều hỗ trợ SpeechSynthesis.

## Tóm tắt một dòng
SpeechSynthesis trong JavaScript cho phép phát âm văn bản bằng giọng nói nhân tạo, tạo ra trải nghiệm tương tác phong phú cho người dùng.