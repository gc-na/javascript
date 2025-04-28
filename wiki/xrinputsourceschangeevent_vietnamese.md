<!--
Meta Description: # Sự kiện XRInputSourcesChangeEvent trong JavaScript: Cập nhật trạng thái nguồn đầu vào XR ## Tóm tắt XRInputSourcesChangeEvent là một sự kiện trong J...
Meta Keywords: vào, trong, đầu, kiện, dụng
-->

# Sự kiện XRInputSourcesChangeEvent trong JavaScript: Cập nhật trạng thái nguồn đầu vào XR

## Tóm tắt
XRInputSourcesChangeEvent là một sự kiện trong JavaScript, được sử dụng trong các ứng dụng thực tế ảo (VR) và thực tế tăng cường (AR) để thông báo cho trình duyệt về sự thay đổi trong nguồn đầu vào XR, như tay cầm hoặc thiết bị đầu vào khác.

## Tài liệu
XRInputSourcesChangeEvent cung cấp thông tin về những thay đổi trong nguồn đầu vào XR, giúp các nhà phát triển có thể xử lý sự kiện này để cập nhật giao diện người dùng hoặc tương tác trong ứng dụng của mình. Sự kiện này được kích hoạt khi có sự thay đổi trong danh sách các thiết bị đầu vào XR, chẳng hạn như khi người dùng kết nối hoặc ngắt kết nối một thiết bị.

### Cách sử dụng
Để lắng nghe sự kiện XRInputSourcesChangeEvent, bạn cần sử dụng phương thức `addEventListener` trên đối tượng XRSession. Dưới đây là cú pháp cơ bản:

```javascript
xrSession.addEventListener('inputsourceschange', (event) => {
    // Xử lý sự kiện
});
```

### Chi tiết
- **Trình duyệt hỗ trợ**: XRInputSourcesChangeEvent hoạt động trên các trình duyệt hỗ trợ WebXR.
- **Đối tượng sự kiện**: Đối tượng sự kiện (event) chứa thuộc tính `added` và `removed`, cho phép bạn biết nguồn đầu vào nào đã được thêm vào hoặc loại bỏ.
- **Tính năng**: Sự kiện này là cần thiết cho việc quản lý nguồn đầu vào trong các ứng dụng VR/AR, đảm bảo rằng người dùng có thể tương tác một cách mượt mà với môi trường 3D.

## Ví dụ
### Ví dụ cơ bản
Dưới đây là một ví dụ đơn giản về cách sử dụng XRInputSourcesChangeEvent:

```javascript
const xrSession = await navigator.xr.requestSession('immersive-vr');

xrSession.addEventListener('inputsourceschange', (event) => {
    event.added.forEach((inputSource) => {
        console.log('Thiết bị đầu vào mới:', inputSource);
    });
    event.removed.forEach((inputSource) => {
        console.log('Thiết bị đầu vào đã bị loại bỏ:', inputSource);
    });
});
```

Trong ví dụ này, mỗi khi có thay đổi trong nguồn đầu vào, thông tin về thiết bị mới hoặc đã bị loại bỏ sẽ được in ra console.

## Giải thích
### Cạm bẫy thường gặp
- **Không hỗ trợ trình duyệt**: Đảm bảo rằng trình duyệt bạn đang sử dụng hỗ trợ WebXR. Nếu không, sự kiện sẽ không được kích hoạt.
- **Xử lý không đồng bộ**: Lưu ý rằng việc thêm hoặc loại bỏ thiết bị đầu vào có thể xảy ra đồng thời, do đó cần phải xử lý chúng một cách đồng bộ để tránh lỗi.

## Tóm tắt một dòng
XRInputSourcesChangeEvent là sự kiện trong JavaScript giúp quản lý sự thay đổi nguồn đầu vào trong các ứng dụng VR và AR.