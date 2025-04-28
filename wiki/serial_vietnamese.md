<!--
Meta Description: # Serial trong JavaScript: Giao tiếp với Thiết bị Ngoại vi ## Tóm tắt Serial trong JavaScript là một API cho phép giao tiếp với các thiết bị ngoại vi ...
Meta Keywords: cổng, port, các, tiếp, liệu
-->

# Serial trong JavaScript: Giao tiếp với Thiết bị Ngoại vi

## Tóm tắt
Serial trong JavaScript là một API cho phép giao tiếp với các thiết bị ngoại vi thông qua cổng nối tiếp. API này thường được sử dụng trong các ứng dụng web để tương tác với các thiết bị như cảm biến, máy in, hoặc các thiết bị IoT.

## Tài liệu
### Mục đích
API Serial cung cấp một cách thức để nhận và gửi dữ liệu đến và từ các thiết bị ngoại vi. Điều này rất hữu ích trong các ứng dụng cần giao tiếp trực tiếp với phần cứng, chẳng hạn như trong lĩnh vực IoT hoặc trong các ứng dụng cần tương tác với các cảm biến.

### Cách sử dụng
Để sử dụng Serial API, bạn cần thực hiện các bước sau:
1. **Yêu cầu quyền truy cập**: Sử dụng phương thức `navigator.serial.requestPort()` để yêu cầu quyền truy cập vào cổng nối tiếp.
2. **Mở cổng**: Sau khi có quyền, sử dụng phương thức `port.open({ baudRate })` để mở cổng, trong đó `baudRate` là tốc độ truyền dữ liệu.
3. **Đọc và ghi dữ liệu**: Sử dụng các phương thức `reader.read()` và `writer.write()` để đọc và ghi dữ liệu từ cổng.

### Chi tiết
- **Khởi tạo**: `const port = await navigator.serial.requestPort();`
- **Mở cổng**: 
  ```javascript
  await port.open({ baudRate: 9600 });
  ```
- **Tạo đối tượng đọc và ghi**: 
  ```javascript
  const reader = port.readable.getReader();
  const writer = port.writable.getWriter();
  ```

## Ví dụ
### Ví dụ 1: Yêu cầu và mở cổng
```javascript
async function connect() {
    const port = await navigator.serial.requestPort();
    await port.open({ baudRate: 9600 });
    console.log("Cổng đã được mở");
}
connect();
```

### Ví dụ 2: Đọc dữ liệu từ cổng
```javascript
async function readData() {
    const port = await navigator.serial.requestPort();
    await port.open({ baudRate: 9600 });
    const reader = port.readable.getReader();
    
    while (true) {
        const { value, done } = await reader.read();
        if (done) {
            break;
        }
        console.log(`Dữ liệu nhận được: ${value}`);
    }
}
readData();
```

### Ví dụ 3: Ghi dữ liệu vào cổng
```javascript
async function writeData(data) {
    const port = await navigator.serial.requestPort();
    await port.open({ baudRate: 9600 });
    const writer = port.writable.getWriter();
    
    await writer.write(data);
    console.log("Dữ liệu đã được gửi");
}
writeData(new Uint8Array([0x01, 0x02, 0x03]));
```

## Giải thích
- **Quyền truy cập**: Trình duyệt sẽ yêu cầu người dùng chọn cổng nối tiếp, vì vậy bạn cần xử lý trường hợp người dùng từ chối.
- **Tốc độ truyền dữ liệu**: Tốc độ truyền dữ liệu (baud rate) cần phải được cấu hình đúng với thiết bị ngoại vi mà bạn đang giao tiếp.
- **Bảo trì kết nối**: Đảm bảo rằng bạn xử lý các tình huống ngắt kết nối và có thể đóng cổng khi không còn cần thiết.

## Tóm tắt một dòng
Serial trong JavaScript cho phép giao tiếp trực tiếp với các thiết bị ngoại vi thông qua cổng nối tiếp, hỗ trợ nhiều ứng dụng trong lĩnh vực IoT.