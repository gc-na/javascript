<!--
Meta Description: # MediaRecorder trong JavaScript: Ghi âm và Ghi hình trên Web ## Tóm tắt MediaRecorder là một API trong JavaScript cho phép người dùng ghi âm và ghi h...
Meta Keywords: mediarecorder, ghi, các, dụng, function
-->

# MediaRecorder trong JavaScript: Ghi âm và Ghi hình trên Web

## Tóm tắt
MediaRecorder là một API trong JavaScript cho phép người dùng ghi âm và ghi hình từ các nguồn media như camera và microphone, giúp xây dựng các ứng dụng web tương tác và đa phương tiện.

## Tài liệu
### Mục đích
MediaRecorder được sử dụng để ghi lại các luồng media từ các thiết bị như microphone và camera. API này cho phép lập trình viên dễ dàng tạo ra các video và audio files từ các nguồn này, phục vụ cho nhiều ứng dụng như hội nghị trực tuyến, ghi âm giọng nói, hoặc tạo video.

### Cách sử dụng
Để sử dụng MediaRecorder, bạn cần thực hiện các bước sau:

1. **Lấy luồng media**: Sử dụng `navigator.mediaDevices.getUserMedia()` để lấy luồng video hoặc audio.
2. **Khởi tạo MediaRecorder**: Tạo một instance của MediaRecorder với luồng media đã lấy.
3. **Bắt đầu ghi**: Sử dụng phương thức `start()` để bắt đầu ghi âm hoặc ghi hình.
4. **Dừng ghi**: Sử dụng phương thức `stop()` để dừng ghi và lấy dữ liệu.

### Chi tiết
Dưới đây là cấu trúc cơ bản khi làm việc với MediaRecorder:

```javascript
// Bước 1: Lấy luồng media
navigator.mediaDevices.getUserMedia({ audio: true, video: true })
    .then(function(stream) {
        // Bước 2: Khởi tạo MediaRecorder
        const mediaRecorder = new MediaRecorder(stream);
        const chunks = [];

        // Bước 3: Lắng nghe sự kiện dataavailable để ghi nhận dữ liệu
        mediaRecorder.ondataavailable = function(event) {
            chunks.push(event.data);
        };

        // Bước 4: Lắng nghe sự kiện stop để xử lý dữ liệu ghi được
        mediaRecorder.onstop = function() {
            const blob = new Blob(chunks, { type: 'video/webm' });
            const url = URL.createObjectURL(blob);
            // Xử lý blob, ví dụ là tạo link tải
            console.log(url);
        };

        // Bắt đầu ghi
        mediaRecorder.start();

        // Dừng ghi sau 5 giây
        setTimeout(() => {
            mediaRecorder.stop();
        }, 5000);
    })
    .catch(function(err) {
        console.error("Lỗi: " + err);
    });
```

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng MediaRecorder để ghi âm từ microphone:

```javascript
navigator.mediaDevices.getUserMedia({ audio: true })
    .then(function(stream) {
        const mediaRecorder = new MediaRecorder(stream);
        const chunks = [];

        mediaRecorder.ondataavailable = function(event) {
            chunks.push(event.data);
        };

        mediaRecorder.onstop = function() {
            const blob = new Blob(chunks, { type: 'audio/wav' });
            const url = URL.createObjectURL(blob);
            console.log('Ghi âm hoàn thành. Tải về: ', url);
        };

        mediaRecorder.start();
        console.log("Bắt đầu ghi âm...");

        setTimeout(() => {
            mediaRecorder.stop();
            console.log("Dừng ghi âm.");
        }, 3000);
    })
    .catch(function(err) {
        console.error("Lỗi: " + err);
    });
```

## Giải thích
Khi làm việc với MediaRecorder, có một số điểm cần lưu ý:

- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ MediaRecorder. Kiểm tra khả năng tương thích trước khi sử dụng.
- **Kiểm soát quyền truy cập**: Người dùng cần cung cấp quyền truy cập cho microphone và camera. Nếu không, sẽ gặp lỗi.
- **Định dạng video/audio**: Chọn định dạng phù hợp với loại media bạn muốn ghi. Một số định dạng có thể không được hỗ trợ trên tất cả các trình duyệt.

## Tóm tắt một dòng
MediaRecorder trong JavaScript là một API mạnh mẽ giúp ghi âm và ghi hình từ các nguồn media trên web.