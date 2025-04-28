<!--
Meta Description: # MIDIOutput trong JavaScript: Tương tác với Thiết Bị MIDI ## Tóm Tắt MIDIOutput là một phần của Web MIDI API trong JavaScript, cho phép các nhà phát ...
Meta Keywords: midi, thiết, gửi, outputs, note
-->

# MIDIOutput trong JavaScript: Tương tác với Thiết Bị MIDI

## Tóm Tắt
MIDIOutput là một phần của Web MIDI API trong JavaScript, cho phép các nhà phát triển tương tác với thiết bị MIDI để gửi dữ liệu âm thanh số. Tính năng này hỗ trợ việc tạo ra âm nhạc và hiệu ứng âm thanh trong ứng dụng web.

## Tài Liệu
### Mục Đích
MIDIOutput cho phép các ứng dụng web gửi thông điệp MIDI đến thiết bị MIDI. Điều này mở ra khả năng tương tác với các nhạc cụ điện tử, phần mềm tạo nhạc và các thiết bị âm thanh khác.

### Cách Sử Dụng
Để sử dụng MIDIOutput, trước tiên bạn cần truy cập vào danh sách các thiết bị MIDI bằng Web MIDI API. Sau đó, bạn có thể gửi các thông điệp MIDI đến thiết bị đã chọn.

#### Cú Pháp
```javascript
navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
    const outputs = midiAccess.outputs;
    outputs.forEach(output => {
        output.send([0x90, 60, 0x7f]); // Gửi tín hiệu "note on"
    });
}

function onMIDIFailure() {
    console.error("Không thể truy cập thiết bị MIDI.");
}
```

### Chi Tiết
- `navigator.requestMIDIAccess()`: Phương thức này yêu cầu quyền truy cập vào thiết bị MIDI của người dùng.
- `midiAccess.outputs`: Trả về danh sách các thiết bị MIDI xuất hiện trên hệ thống.
- `output.send(data)`: Phương thức này được sử dụng để gửi dữ liệu MIDI. Dữ liệu phải là một mảng số nguyên (byte), trong đó:
  - Byte đầu tiên là loại thông điệp (ví dụ: `0x90` cho "note on").
  - Byte thứ hai là nốt nhạc (ví dụ: `60` cho nốt C4).
  - Byte thứ ba là độ mạnh của nốt (0-127).

## Ví Dụ
### Ví Dụ Cơ Bản
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const outputs = midiAccess.outputs;
    if (outputs.size > 0) {
        const output = outputs.values().next().value;
        output.send([0x90, 60, 0x7f]); // Gửi tín hiệu "note on" cho nốt C4
        output.send([0x80, 60, 0x40]); // Gửi tín hiệu "note off" cho nốt C4
    }
});
```

### Ví Dụ Gửi Nhiều Nốt
```javascript
const notes = [60, 62, 64, 65, 67]; // Các nốt C4, D4, E4, F4, G4
notes.forEach(note => {
    output.send([0x90, note, 0x7f]); // Gửi tín hiệu "note on"
    output.send([0x80, note, 0x40]); // Gửi tín hiệu "note off"
});
```

## Giải Thích
Một số vấn đề thường gặp khi làm việc với MIDIOutput:
- **Quyền Truy Cập**: Người dùng cần cấp quyền truy cập cho trình duyệt để sử dụng MIDI. Nếu không, bạn sẽ không thể kết nối với thiết bị MIDI.
- **Thiết Bị Không Có Kết Nối**: Kiểm tra xem thiết bị MIDI có được kết nối và nhận diện đúng cách không. Nếu không, bạn sẽ không nhận được bất kỳ thông tin nào từ `midiAccess.outputs`.
- **Gửi thông điệp sai**: Đảm bảo rằng thông điệp MIDI được gửi đúng định dạng, vì việc gửi sai byte có thể gây ra lỗi khi thiết bị nhận thông điệp.

## Tóm Tắt Một Dòng
MIDIOutput trong JavaScript cho phép bạn gửi thông điệp MIDI đến thiết bị âm thanh, mở rộng khả năng sáng tạo âm nhạc trong ứng dụng web.