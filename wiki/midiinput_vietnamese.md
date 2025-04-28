<!--
Meta Description: # MIDIInput trong JavaScript: Hướng dẫn Chi Tiết ## Tóm tắt MIDIInput là một giao diện trong API Web MIDI, cho phép các ứng dụng JavaScript tương tác ...
Meta Keywords: midi, thiết, các, liệu, dụng
-->

# MIDIInput trong JavaScript: Hướng dẫn Chi Tiết

## Tóm tắt
MIDIInput là một giao diện trong API Web MIDI, cho phép các ứng dụng JavaScript tương tác với thiết bị MIDI để nhận dữ liệu MIDI từ các thiết bị như keyboard, controller, hoặc các thiết bị âm nhạc khác.

## Tài liệu
### Mục đích
MIDIInput cung cấp một cách tiếp cận đơn giản để nhận và xử lý thông tin MIDI trong các ứng dụng web, giúp cho việc phát triển các ứng dụng âm nhạc trực tuyến trở nên dễ dàng hơn.

### Cách sử dụng
Để sử dụng MIDIInput, bạn cần làm theo các bước sau:

1. **Kiểm tra hỗ trợ API Web MIDI**: Trước tiên, bạn cần kiểm tra xem trình duyệt của người dùng có hỗ trợ API Web MIDI hay không.

   ```javascript
   if (navigator.requestMIDIAccess) {
       console.log("Trình duyệt hỗ trợ MIDI!");
   } else {
       console.log("Trình duyệt không hỗ trợ MIDI.");
   }
   ```

2. **Yêu cầu quyền truy cập MIDI**: Sử dụng `navigator.requestMIDIAccess()` để yêu cầu quyền truy cập vào thiết bị MIDI.

   ```javascript
   navigator.requestMIDIAccess()
       .then(onMIDISuccess, onMIDIFailure);
   ```

3. **Xử lý kết quả**: Trong hàm `onMIDISuccess`, bạn sẽ lấy danh sách các thiết bị MIDI và thiết lập các listener để nhận dữ liệu.

   ```javascript
   function onMIDISuccess(midiAccess) {
       const inputs = midiAccess.inputs;
       inputs.forEach((input) => {
           input.onmidimessage = handleMIDIMessage;
       });
   }

   function handleMIDIMessage(message) {
       console.log(`Nhận dữ liệu MIDI: ${message.data}`);
   }
   ```

### Chi tiết
- **onmidimessage**: Thuộc tính của MIDIInput, cho phép bạn chỉ định một hàm để xử lý dữ liệu MIDI khi nó đến.
- **message**: Đối tượng chứa thông tin về sự kiện MIDI, bao gồm loại sự kiện, số lượng, và dữ liệu cụ thể.

## Ví dụ
### Ví dụ cơ bản
Dưới đây là một ví dụ đơn giản về cách nhận và hiển thị dữ liệu MIDI từ một thiết bị:

```javascript
navigator.requestMIDIAccess()
    .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        input.onmidimessage = (message) => {
            console.log(`Dữ liệu MIDI nhận được: ${message.data}`);
        };
    });
}

function onMIDIFailure() {
    console.error("Không thể truy cập thiết bị MIDI.");
}
```

## Giải thích
### Những cạm bẫy thường gặp
- **Thiết bị không được kết nối**: Đảm bảo rằng thiết bị MIDI đã được kết nối đúng cách trước khi yêu cầu quyền truy cập.
- **Trình duyệt không hỗ trợ**: Một số trình duyệt có thể không hỗ trợ API Web MIDI. Hãy kiểm tra tính tương thích trước khi phát triển ứng dụng.
- **Quyền truy cập**: Nếu người dùng từ chối quyền truy cập, bạn sẽ không thể nhận dữ liệu từ thiết bị MIDI.

### Ghi chú bổ sung
- Sử dụng API Web MIDI có thể thay đổi giữa các trình duyệt, do đó, hãy kiểm tra tài liệu chính thức để biết thêm chi tiết.
- Đảm bảo rằng bạn xử lý các lỗi và ngoại lệ một cách hợp lý để nâng cao trải nghiệm người dùng.

## Tóm tắt một dòng
MIDIInput trong JavaScript cho phép nhận dữ liệu từ các thiết bị MIDI, giúp phát triển ứng dụng âm nhạc trực tuyến dễ dàng hơn.