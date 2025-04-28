<!--
Meta Description: # webkitRTCPeerConnection: Kết Nối P2P Trong JavaScript ## Tóm Tắt `webkitRTCPeerConnection` là một giao diện trong WebRTC (Web Real-Time Communicatio...
Meta Keywords: các, kết, nối, webkitrtcpeerconnection, error
-->

# webkitRTCPeerConnection: Kết Nối P2P Trong JavaScript

## Tóm Tắt
`webkitRTCPeerConnection` là một giao diện trong WebRTC (Web Real-Time Communication) cho phép các trình duyệt thực hiện kết nối âm thanh và video trực tiếp giữa các thiết bị mà không cần đến một máy chủ trung gian.

## Tài Liệu
`webkitRTCPeerConnection` là phần mở rộng của `RTCPeerConnection` trong các trình duyệt dựa trên WebKit, như Safari. Nó cho phép người dùng thiết lập các kết nối P2P, quản lý các luồng media và xử lý tín hiệu mạng. 

### Mục Đích
- **Kết Nối Trực Tiếp**: Cho phép các thiết bị giao tiếp trực tiếp với nhau.
- **Hỗ Trợ Media**: Chuyển giao âm thanh và video trong thời gian thực.
- **Bảo Mật**: Sử dụng các giao thức mã hóa để bảo vệ dữ liệu.

### Cách Sử Dụng
Để sử dụng `webkitRTCPeerConnection`, bạn cần khởi tạo một đối tượng và thiết lập các cấu hình cần thiết. Dưới đây là cú pháp cơ bản:

```javascript
var configuration = {
    iceServers: [{ urls: 'stun:stun.l.google.com:19302' }]
};

var peerConnection = new webkitRTCPeerConnection(configuration);
```

### Các Phương Thức Chính
- **createOffer()**: Tạo một đề xuất kết nối.
- **createAnswer()**: Tạo phản hồi cho một đề xuất kết nối.
- **addIceCandidate()**: Thêm một ICE candidate cho kết nối.

## Ví Dụ
### Ví Dụ 1: Tạo Kết Nối
```javascript
var configuration = { iceServers: [{ urls: 'stun:stun.l.google.com:19302' }] };
var peerConnection = new webkitRTCPeerConnection(configuration);

// Lắng nghe sự kiện ICE candidate
peerConnection.onicecandidate = function(event) {
    if (event.candidate) {
        console.log('New ICE candidate: ' + event.candidate);
    }
};

// Tạo offer
peerConnection.createOffer()
    .then(offer => peerConnection.setLocalDescription(offer))
    .catch(error => console.error('Error creating offer: ', error));
```

### Ví Dụ 2: Thêm Luồng Media
```javascript
navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        // Thêm luồng media vào peer connection
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    })
    .catch(error => console.error('Error accessing media devices.', error));
```

## Giải Thích
- **Trình Duyệt Hỗ Trợ**: `webkitRTCPeerConnection` không được hỗ trợ trên tất cả các trình duyệt. Kiểm tra tính tương thích trước khi sử dụng.
- **Cấu Hình ICE Servers**: Đảm bảo rằng bạn cung cấp thông tin ICE servers chính xác để thiết lập kết nối thành công.
- **Quyền Truy Cập**: Bạn cần yêu cầu quyền truy cập vào camera và microphone từ người dùng trước khi sử dụng `getUserMedia()`.

## Tóm Tắt Một Dòng
`webkitRTCPeerConnection` cho phép thiết lập kết nối âm thanh và video trực tiếp giữa các trình duyệt bằng cách sử dụng WebRTC.