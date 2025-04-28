<!--
Meta Description: # TouchList trong JavaScript: Hướng Dẫn Chi Tiết và Cách Sử Dụng ## Tóm tắt TouchList là một đối tượng trong JavaScript được sử dụng để quản lý và tươ...
Meta Keywords: touchlist, chạm, các, điểm, targettouches
-->

# TouchList trong JavaScript: Hướng Dẫn Chi Tiết và Cách Sử Dụng

## Tóm tắt
TouchList là một đối tượng trong JavaScript được sử dụng để quản lý và tương tác với các điểm chạm (touch points) trên màn hình cảm ứng. Nó cung cấp thông tin chi tiết về vị trí và trạng thái của từng điểm chạm, giúp lập trình viên phát triển các ứng dụng tương tác mượt mà và hiệu quả.

## Tài liệu
### Mục đích
TouchList cho phép bạn truy cập và làm việc với tất cả các điểm chạm đang hoạt động trên màn hình cảm ứng. Đối tượng này thường được sử dụng trong các sự kiện như `touchstart`, `touchmove`, và `touchend` để theo dõi các hành động chạm của người dùng.

### Cách sử dụng
TouchList được truy cập thông qua thuộc tính `touches`, `targetTouches`, hoặc `changedTouches` của sự kiện chạm. Mỗi thuộc tính này đều trả về một TouchList, chứa thông tin về các điểm chạm tương ứng.

### Chi tiết
- **touches**: Trả về một danh sách các điểm chạm hiện tại trên màn hình.
- **targetTouches**: Trả về danh sách các điểm chạm đang tương tác với một phần tử cụ thể.
- **changedTouches**: Chứa các điểm chạm đã thay đổi trạng thái (như bắt đầu hoặc kết thúc).

Mỗi đối tượng trong TouchList cung cấp các thuộc tính như `clientX`, `clientY`, `identifier`, và `target`, giúp bạn xác định vị trí và trạng thái của điểm chạm.

## Ví dụ
### Ví dụ cơ bản
```javascript
document.addEventListener('touchstart', function(event) {
    let touchList = event.touches;
    for (let i = 0; i < touchList.length; i++) {
        console.log(`Touch ${i}: X=${touchList[i].clientX}, Y=${touchList[i].clientY}`);
    }
});
```

### Ví dụ với targetTouches
```javascript
document.addEventListener('touchmove', function(event) {
    let targetTouches = event.targetTouches;
    for (let i = 0; i < targetTouches.length; i++) {
        console.log(`Target Touch ${i}: X=${targetTouches[i].clientX}, Y=${targetTouches[i].clientY}`);
    }
});
```

## Giải thích
### Những cạm bẫy phổ biến
- **Không có điểm chạm**: Nếu không có điểm chạm nào, TouchList sẽ có độ dài bằng 0. Lập trình viên cần kiểm tra trước khi truy cập vào các thuộc tính.
- **Trình duyệt không hỗ trợ**: Một số trình duyệt cũ có thể không hỗ trợ các sự kiện chạm, gây ra lỗi khi cố gắng truy cập TouchList.
- **Chỉ đọc**: TouchList là chỉ đọc; bạn không thể thay đổi nội dung của nó trực tiếp.

## Tóm tắt một dòng
TouchList trong JavaScript là đối tượng cho phép truy cập và quản lý các điểm chạm trên màn hình cảm ứng, cung cấp thông tin cần thiết cho việc phát triển ứng dụng tương tác.