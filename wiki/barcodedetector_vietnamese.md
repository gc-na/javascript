<!--
Meta Description: # BarcodeDetector trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể ## Tóm tắt BarcodeDetector là một API JavaScript cho phép lập trình viên nhận d...
Meta Keywords: barcodedetector, vạch, hiện, video, phát
-->

# BarcodeDetector trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể

## Tóm tắt
BarcodeDetector là một API JavaScript cho phép lập trình viên nhận diện và xử lý mã vạch từ hình ảnh hoặc video. Nó giúp xây dựng các ứng dụng quét mã vạch dễ dàng và hiệu quả.

## Tài liệu
### Mục đích
BarcodeDetector được thiết kế để phát hiện các loại mã vạch như QR Code, Code 128, và nhiều loại khác. API này hữu ích trong các ứng dụng thương mại điện tử, quản lý kho, và bất kỳ lĩnh vực nào cần nhận diện sản phẩm nhanh chóng.

### Cách sử dụng
Để sử dụng BarcodeDetector, bạn cần tạo một đối tượng BarcodeDetector và sau đó gọi phương thức `detect()`. Dưới đây là cú pháp cơ bản:

```javascript
const barcodeDetector = new BarcodeDetector({ formats: ['qr_code', 'code_128'] });
barcodeDetector.detect(imageBitmap)
    .then(barcodes => {
        console.log(barcodes);
    })
    .catch(err => {
        console.error(err);
    });
```

### Thông tin chi tiết
- **Đối số**: `formats` - Một mảng các loại mã vạch mà bạn muốn phát hiện, ví dụ: `['qr_code', 'ean_13']`.
- **Phương thức**:
  - `detect(imageBitmap)`: Nhận diện mã vạch trong hình ảnh đã cho và trả về một Promise với danh sách mã vạch phát hiện được.

### Ví dụ
#### Ví dụ 1: Nhận diện QR Code từ hình ảnh
```javascript
const image = document.querySelector('img');
const barcodeDetector = new BarcodeDetector({ formats: ['qr_code'] });

barcodeDetector.detect(image)
    .then(barcodes => {
        barcodes.forEach(barcode => {
            console.log(`Mã vạch phát hiện: ${barcode.rawValue}`);
        });
    })
    .catch(err => {
        console.error('Không thể phát hiện mã vạch:', err);
    });
```

#### Ví dụ 2: Nhận diện mã vạch từ video
```javascript
const video = document.querySelector('video');
const barcodeDetector = new BarcodeDetector({ formats: ['code_128'] });

video.addEventListener('play', () => {
    const detectBarcode = () => {
        if (!video.paused && !video.ended) {
            const imageBitmap = ... // Chuyển đổi khung video thành ImageBitmap
            barcodeDetector.detect(imageBitmap)
                .then(barcodes => {
                    barcodes.forEach(barcode => {
                        console.log(`Mã vạch phát hiện: ${barcode.rawValue}`);
                    });
                })
                .catch(err => {
                    console.error('Không thể phát hiện mã vạch:', err);
                });
            requestAnimationFrame(detectBarcode);
        }
    };
    detectBarcode();
});
```

## Giải thích
### Những điều cần lưu ý
- **Hỗ trợ trình duyệt**: BarcodeDetector hiện chỉ hỗ trợ một số trình duyệt nhất định, vì vậy hãy kiểm tra khả năng tương thích trước khi triển khai.
- **Chất lượng hình ảnh**: Để đạt được kết quả tốt nhất, hình ảnh hoặc video cần có độ phân giải cao và mã vạch phải rõ ràng.
- **Thất bại trong việc phát hiện**: Trong một số trường hợp, nếu mã vạch bị hỏng hoặc không rõ ràng, việc phát hiện có thể không thành công.

## Tóm tắt một dòng
BarcodeDetector trong JavaScript là một API tiện ích giúp phát hiện và xử lý mã vạch từ hình ảnh và video một cách dễ dàng.