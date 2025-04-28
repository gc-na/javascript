<!--
Meta Description: # RTCPeerConnection trong JavaScript: Cách sử dụng và ứng dụng ## Tóm tắt RTCPeerConnection là một đối tượng trong WebRTC, cho phép thiết lập kết nối ...
Meta Keywords: kết, nối, các, một, đối
-->

# RTCPeerConnection trong JavaScript: Cách sử dụng và ứng dụng

## Tóm tắt
RTCPeerConnection là một đối tượng trong WebRTC, cho phép thiết lập kết nối âm thanh và video trực tiếp giữa các trình duyệt mà không cần máy chủ trung gian.

## Tài liệu
### Mục đích
RTCPeerConnection là một phần quan trọng của WebRTC (Web Real-Time Communication), cho phép người dùng gửi và nhận dữ liệu âm thanh, video và dữ liệu theo thời gian thực trong các ứng dụng web. Đối tượng này giúp thiết lập các kết nối ngang hàng (peer-to-peer) giữa các trình duyệt, hỗ trợ truyền tải dữ liệu một cách hiệu quả và an toàn.

### Cách sử dụng
Để sử dụng RTCPeerConnection, bạn cần làm theo các bước sau:

1. **Khởi tạo**: Tạo một thể hiện mới của RTCPeerConnection.
2. **Thêm MediaStream**: Kết nối các nguồn âm thanh và video.
3. **Gửi Offer**: Gửi yêu cầu kết nối đến đối tác bằng cách tạo một SDP offer.
4. **Nhận Answer**: Nhận và xử lý SDP answer từ đối tác.
5. **Quản lý ICE Candidates**: Xử lý các ICE candidates để thiết lập kết nối.

### Chi tiết
```javascript
const configuration = {
    iceServers: [
        { urls: 'stun:stun.l.google.com:19302' }
    ]
};

const peerConnection = new RTCPeerConnection(configuration);
```

- **iceServers**: Là một mảng các máy chủ STUN hoặc TURN để hỗ trợ trong quá trình thiết lập kết nối.
- **addTrack()**: Phương thức để thêm track âm thanh hoặc video vào peer connection.
- **createOffer()**: Tạo SDP offer để bắt đầu kết nối.
- **setLocalDescription()**: Đặt mô tả địa phương cho peer connection.
- **setRemoteDescription()**: Đặt mô tả từ xa nhận được từ đối tác.

## Ví dụ
### Tạo một kết nối đơn giản
```javascript
const peerConnection = new RTCPeerConnection();

navigator.mediaDevices.getUserMedia({ video: true, audio: true })
    .then(stream => {
        stream.getTracks().forEach(track => peerConnection.addTrack(track, stream));
    });

peerConnection.createOffer()
    .then(offer => peerConnection.setLocalDescription(offer))
    .then(() => {
        // Gửi offer đến đối tác
    });
```

### Nhận Answer từ đối tác
```javascript
// Nhận answer từ đối tác
peerConnection.setRemoteDescription(new RTCSessionDescription(answer));
```

## Giải thích
### Những lưu ý thường gặp
- **CORS**: Đảm bảo rằng máy chủ của bạn hỗ trợ CORS nếu bạn đang truy cập từ một nguồn khác.
- **STUN/TURN**: Nếu bạn không thể kết nối, hãy kiểm tra cấu hình ICE servers của mình.
- **HTTPS**: WebRTC yêu cầu trang web phải chạy trên HTTPS trừ khi sử dụng localhost.

### Các vấn đề thường gặp
- **Không có âm thanh hoặc video**: Kiểm tra quyền truy cập media và đảm bảo rằng các track đã được thêm đúng cách.
- **Kết nối bị ngắt**: Có thể do NAT hoặc firewall ngăn chặn kết nối ngang hàng.

## Tóm tắt một dòng
RTCPeerConnection là một đối tượng WebRTC trong JavaScript giúp thiết lập kết nối âm thanh và video trực tiếp giữa các trình duyệt.