<!--
Meta Description: # RTCIceTransport: Quản lý Giao Thông ICE trong JavaScript ## Tóm tắt RTCIceTransport là một phần của WebRTC API, cho phép các ứng dụng JavaScript thi...
Meta Keywords: rtcicetransport, thông, ice, các, giao
-->

# RTCIceTransport: Quản lý Giao Thông ICE trong JavaScript

## Tóm tắt
RTCIceTransport là một phần của WebRTC API, cho phép các ứng dụng JavaScript thiết lập và quản lý giao thông ICE (Interactive Connectivity Establishment) cho các kết nối truyền thông thời gian thực, giúp đảm bảo truyền tải dữ liệu hiệu quả giữa các điểm cuối.

## Tài liệu
### Mục đích
RTCIceTransport được sử dụng để quản lý quá trình thiết lập kết nối giữa hai thiết bị trong môi trường mạng có thể thay đổi. Nó chịu trách nhiệm cho việc lựa chọn và sử dụng các địa chỉ IP và cổng thích hợp để truyền tải dữ liệu.

### Cách sử dụng
Để sử dụng RTCIceTransport, bạn cần tạo một đối tượng RTCIceTransport thông qua RTCIceGatherer hoặc RTCIceCandidate. Một đối tượng RTCIceTransport sẽ tự động được tạo ra khi bạn thiết lập một kết nối peer-to-peer thông qua RTCPeerConnection.

### Chi tiết
- **Thuộc tính**:
  - `state`: Trạng thái hiện tại của RTCIceTransport (new, checking, connected, completed, failed, closed).
  - `iceRole`: Vai trò của ICE, có thể là "controlling" hoặc "controlled".
  
- **Phương thức**:
  - `start()`: Bắt đầu quá trình ICE.
  - `stop()`: Dừng quá trình giao thông ICE.
  - `getLocalCandidates()`: Lấy danh sách các ứng viên ICE địa phương.

## Ví dụ
```javascript
// Khởi tạo một kết nối Peer
const peerConnection = new RTCPeerConnection();

// Lấy đối tượng RTCIceTransport từ peerConnection
const iceTransport = peerConnection.iceTransport;

// Bắt đầu giao thông ICE
iceTransport.start();

// Dừng giao thông ICE
iceTransport.stop();
```

## Giải thích
- **Các vấn đề thường gặp**:
  - Kết nối không thành công có thể xảy ra do cấu hình ICE không đúng hoặc do sự khác biệt về mạng giữa các thiết bị.
  - Nếu không khởi động RTCIceTransport đúng cách, bạn có thể không truyền tải được dữ liệu.

- **Ghi chú thêm**:
  - Hãy chắc chắn rằng bạn đã thiết lập các ứng viên ICE trước khi bắt đầu giao thông.
  - Theo dõi trạng thái của RTCIceTransport để xử lý các tình huống kết nối không thành công hoặc bị ngắt.

## Tóm tắt một dòng
RTCIceTransport là một thành phần quan trọng trong WebRTC, hỗ trợ quản lý giao thông ICE cho kết nối truyền thông thời gian thực trong JavaScript.