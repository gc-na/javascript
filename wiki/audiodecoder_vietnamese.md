<!--
Meta Description: # AudioDecoder trong JavaScript: Giải mã Âm Thanh Hiệu Quả ## Tóm tắt `AudioDecoder` là một API trong JavaScript cho phép người dùng giải mã âm thanh ...
Meta Keywords: thanh, liệu, giải, audiodecoder, frame
-->

# AudioDecoder trong JavaScript: Giải mã Âm Thanh Hiệu Quả

## Tóm tắt
`AudioDecoder` là một API trong JavaScript cho phép người dùng giải mã âm thanh từ dữ liệu mã hóa, giúp phát lại âm thanh một cách hiệu quả và linh hoạt trong các ứng dụng web.

## Tài liệu
### Mục đích
`AudioDecoder` được sử dụng để giải mã âm thanh từ các định dạng nén như AAC, MP3, OPUS,... giúp các nhà phát triển dễ dàng xử lý và phát lại âm thanh trong các ứng dụng web mà không cần phải dựa vào các thư viện bên ngoài.

### Cách sử dụng
Để sử dụng `AudioDecoder`, bạn cần tạo một instance của nó và chỉ định một callback cho việc xử lý dữ liệu giải mã. Đoạn mã dưới đây là ví dụ về cách khởi tạo và sử dụng `AudioDecoder`.

```javascript
const decoder = new AudioDecoder({
  error: (e) => console.error('Error decoding audio:', e),
  output: (frame) => {
    console.log('Decoded audio frame received:', frame);
    // Tiến hành xử lý frame âm thanh ở đây
  },
});

// Giải mã dữ liệu âm thanh
const config = {
  codec: 'opus',
  sampleRate: 48000,
  numberOfChannels: 2,
};

decoder.configure(config);

// Giải mã dữ liệu âm thanh (ví dụ, từ một ArrayBuffer)
const audioData = new Uint8Array([...]); // Dữ liệu âm thanh mã hóa
decoder.decode(audioData);
```

### Chi tiết
- **Các thuộc tính**:
  - `codec`: Xác định codec âm thanh được sử dụng.
  - `sampleRate`: Tần số mẫu của âm thanh.
  - `numberOfChannels`: Số lượng kênh âm thanh (1 cho mono, 2 cho stereo).
  
- **Các phương thức**:
  - `configure(config)`: Cấu hình bộ giải mã với thông tin về codec và các thuộc tính âm thanh.
  - `decode(data)`: Giải mã dữ liệu âm thanh đã cho.

## Ví dụ
### Ví dụ 1: Giải mã âm thanh Opus
```javascript
const opusDecoder = new AudioDecoder({
  error: (e) => console.error('Error:', e),
  output: (frame) => console.log('Frame:', frame),
});

opusDecoder.configure({
  codec: 'opus',
  sampleRate: 48000,
  numberOfChannels: 2,
});

// Giải mã dữ liệu âm thanh
const opusData = new Uint8Array([...]); // Dữ liệu Opus
opusDecoder.decode(opusData);
```

### Ví dụ 2: Giải mã âm thanh MP3
```javascript
const mp3Decoder = new AudioDecoder({
  error: (e) => console.error('Error:', e),
  output: (frame) => console.log('Frame:', frame),
});

mp3Decoder.configure({
  codec: 'mp3',
  sampleRate: 44100,
  numberOfChannels: 2,
});

// Giải mã dữ liệu âm thanh
const mp3Data = new Uint8Array([...]); // Dữ liệu MP3
mp3Decoder.decode(mp3Data);
```

## Giải thích
Một số vấn đề thường gặp khi làm việc với `AudioDecoder`:
- **Codec không tương thích**: Đảm bảo rằng codec bạn sử dụng được hỗ trợ bởi trình duyệt.
- **Kích thước dữ liệu**: Đảm bảo rằng dữ liệu âm thanh đã được mã hóa đúng cách và phù hợp với cấu hình đã chỉ định.
- **Quá tải dữ liệu**: Đừng gửi quá nhiều dữ liệu cùng một lúc; hãy chia nhỏ dữ liệu để tránh tình trạng quá tải bộ giải mã.

## Tóm tắt một dòng
`AudioDecoder` trong JavaScript là một công cụ mạnh mẽ cho việc giải mã âm thanh, cho phép phát lại âm thanh hiệu quả từ các định dạng nén.