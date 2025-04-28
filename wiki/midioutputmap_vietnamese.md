<!--
Meta Description: # MIDIOutputMap trong JavaScript: Hướng dẫn chi tiết và đầy đủ ## Tóm tắt MIDIOutputMap là một đối tượng trong JavaScript cho phép lập trình viên truy...
Meta Keywords: các, midi, đầu, outputs, midioutputmap
-->

# MIDIOutputMap trong JavaScript: Hướng dẫn chi tiết và đầy đủ

## Tóm tắt
MIDIOutputMap là một đối tượng trong JavaScript cho phép lập trình viên truy cập và quản lý các đầu ra MIDI (Musical Instrument Digital Interface), hỗ trợ việc tạo ứng dụng âm nhạc tương tác và điều khiển thiết bị âm nhạc.

## Tài liệu
### Mục đích
MIDIOutputMap là một phần của Web MIDI API, cung cấp một cách đơn giản để giao tiếp với các thiết bị MIDI. Nó cho phép lập trình viên dễ dàng tìm kiếm và quản lý các đầu ra MIDI, từ đó tạo ra các ứng dụng âm nhạc phong phú và hấp dẫn.

### Cách sử dụng
Để sử dụng MIDIOutputMap, bạn cần có quyền truy cập vào API MIDI. Điều này thường được thực hiện thông qua phương thức `navigator.requestMIDIAccess()`. Khi truy cập thành công, bạn có thể lấy danh sách các đầu ra MIDI thông qua thuộc tính `outputs` của đối tượng MIDIAccess.

### Chi tiết
MIDIOutputMap là một `Map` chứa các đối tượng MIDIOutput, mỗi đối tượng đại diện cho một thiết bị đầu ra MIDI. Bạn có thể sử dụng các phương thức của Map, như `get()`, `set()`, và `forEach()`, để quản lý các đầu ra.

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    console.log(outputs); // Hiển thị MIDIOutputMap
});
```

## Ví dụ
### Ví dụ 1: Lấy danh sách đầu ra MIDI
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    outputs.forEach((output) => {
        console.log(`Tên đầu ra: ${output.name}, ID: ${output.id}`);
    });
});
```

### Ví dụ 2: Gửi thông điệp MIDI đến thiết bị đầu ra
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    const firstOutput = outputs.values().next().value; // Lấy thiết bị đầu ra đầu tiên
    if (firstOutput) {
        firstOutput.send([144, 60, 0]); // Gửi một thông điệp Note On cho nốt C4
    }
});
```

## Giải thích
- **Các cạm bẫy phổ biến**: Đảm bảo rằng trình duyệt của bạn hỗ trợ Web MIDI API. Nếu không, bạn sẽ không thể truy cập MIDIOutputMap.
- **Chú thích**: Không phải tất cả các thiết bị MIDI đều hỗ trợ tất cả các loại thông điệp. Kiểm tra khả năng tương thích của thiết bị trước khi gửi thông điệp.

## Tóm tắt một dòng
MIDIOutputMap trong JavaScript cho phép lập trình viên quản lý và tương tác với các đầu ra MIDI, hỗ trợ phát triển ứng dụng âm nhạc trên web.