<!--
Meta Description: # ProgressEvent trong JavaScript: Tìm Hiểu và Ứng Dụng ## Tóm tắt ProgressEvent là một sự kiện trong JavaScript được sử dụng để theo dõi tiến trình củ...
Meta Keywords: progressevent, các, trình, tải, tiến
-->

# ProgressEvent trong JavaScript: Tìm Hiểu và Ứng Dụng

## Tóm tắt
ProgressEvent là một sự kiện trong JavaScript được sử dụng để theo dõi tiến trình của các hoạt động như tải tệp hoặc truyền dữ liệu. Nó giúp lập trình viên nắm bắt thông tin về trạng thái tiến trình của các tác vụ bất đồng bộ.

## Tài liệu
### Mục đích
ProgressEvent cung cấp thông tin về tiến trình của một hoạt động, chẳng hạn như tải xuống hoặc gửi dữ liệu qua mạng. Nó giúp người dùng có thể nắm bắt và hiển thị trạng thái của các hoạt động này trong giao diện người dùng.

### Cách sử dụng
ProgressEvent thường được sử dụng trong các tình huống như:
- Tải tệp từ máy chủ.
- Gửi dữ liệu đến máy chủ.
- Theo dõi tiến trình của các hoạt động bất đồng bộ.

Để lắng nghe sự kiện ProgressEvent, bạn có thể sử dụng các phương thức như `addEventListener` trên đối tượng XMLHttpRequest hoặc Fetch API. 

### Chi tiết
ProgressEvent có những thuộc tính quan trọng sau:
- `lengthComputable`: Boolean cho biết liệu tiến trình có thể được tính toán hay không.
- `loaded`: Số byte đã được tải.
- `total`: Tổng số byte dự kiến sẽ được tải.

Khi một sự kiện ProgressEvent xảy ra, bạn có thể truy cập các thuộc tính này để biết thêm thông tin về tiến trình.

## Ví dụ
Dưới đây là một ví dụ đơn giản sử dụng ProgressEvent với XMLHttpRequest:

```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://example.com/file.zip', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Đã tải: ${percentComplete.toFixed(2)}%`);
    } else {
        console.log('Không thể tính toán tiến trình tải.');
    }
};

xhr.onload = function() {
    console.log('Tải hoàn tất!');
};

xhr.send();
```

## Giải thích
Một số điểm cần lưu ý khi làm việc với ProgressEvent:
- Không phải tất cả các hoạt động đều tạo ra sự kiện ProgressEvent; chỉ những hoạt động hỗ trợ tính toán tiến trình mới phát sinh sự kiện này.
- Đảm bảo kiểm tra thuộc tính `lengthComputable` trước khi tính toán phần trăm tải để tránh lỗi.
- Sự kiện này chỉ có thể được sử dụng trong các hoạt động bất đồng bộ, không áp dụng cho các tác vụ đồng bộ.

## Tóm tắt một dòng
ProgressEvent trong JavaScript cho phép theo dõi tiến trình của các hoạt động tải và gửi dữ liệu, giúp cải thiện trải nghiệm người dùng.