<!--
Meta Description: # onprogress trong JavaScript: Theo dõi Tiến Trình Tải Dữ Liệu ## Tóm tắt `onprogress` là một sự kiện trong JavaScript được sử dụng để theo dõi tiến t...
Meta Keywords: tải, liệu, onprogress, dụng, trình
-->

# onprogress trong JavaScript: Theo dõi Tiến Trình Tải Dữ Liệu 

## Tóm tắt
`onprogress` là một sự kiện trong JavaScript được sử dụng để theo dõi tiến trình tải dữ liệu, đặc biệt là khi thực hiện các yêu cầu mạng như tải file hoặc dữ liệu từ một API. 

## Tài liệu
### Mục đích
Sự kiện `onprogress` cho phép lập trình viên nhận biết được tiến trình của các hoạt động tải dữ liệu. Nó rất hữu ích trong việc cải thiện trải nghiệm người dùng bằng cách cung cấp thông tin về quá trình tải, giúp người dùng nắm bắt được tình trạng hiện tại của các yêu cầu bất đồng bộ.

### Cách sử dụng
Sự kiện `onprogress` thường được sử dụng với các đối tượng như `XMLHttpRequest` hoặc `Fetch API`. Để sử dụng, bạn cần gán một hàm xử lý sự kiện cho thuộc tính `onprogress` của đối tượng.

### Chi tiết
- **XMLHttpRequest**: Khi sử dụng `XMLHttpRequest`, bạn có thể thêm một hàm để xử lý sự kiện `onprogress`. Hàm này được gọi mỗi khi có dữ liệu mới được tải.
  
- **Fetch API**: Mặc dù `Fetch API` không hỗ trợ trực tiếp sự kiện `onprogress`, bạn có thể sử dụng `ReadableStream` để theo dõi tiến trình tải dữ liệu.

## Ví dụ
### Ví dụ 1: Sử dụng `XMLHttpRequest`
```javascript
let xhr = new XMLHttpRequest();
xhr.open('GET', 'file.txt', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        let percentComplete = (event.loaded / event.total) * 100;
        console.log('Đã tải: ' + percentComplete + '%');
    }
};

xhr.onload = function() {
    console.log('Tải hoàn tất!');
};

xhr.send();
```

### Ví dụ 2: Sử dụng `Fetch API` với `ReadableStream`
```javascript
fetch('file.txt')
    .then(response => {
        const reader = response.body.getReader();
        let receivedLength = 0; // Tổng số byte đã nhận
        let chunks = []; // Mảng chứa các chunk dữ liệu

        return new Promise((resolve, reject) => {
            function pump() {
                reader.read().then(({ done, value }) => {
                    if (done) {
                        resolve(new TextDecoder("utf-8").decode(new Uint8Array(chunks)));
                        return;
                    }
                    receivedLength += value.length; // Cập nhật số byte đã nhận
                    chunks.push(value); // Lưu chunk dữ liệu
                    console.log('Đã tải: ' + (receivedLength / response.contentLength) * 100 + '%');
                    pump();
                }).catch(reject);
            }
            pump();
        });
    })
    .then(result => {
        console.log('Tải hoàn tất!');
    });
```

## Giải thích
- **Khó khăn thường gặp**: Một số lập trình viên có thể gặp khó khăn trong việc tính toán phần trăm dữ liệu đã tải nếu không kiểm tra xem `event.lengthComputable` có phải là `true` hay không.
- **Chú ý**: Cần lưu ý rằng không phải tất cả các yêu cầu đều cung cấp thông tin về tổng số byte, đặc biệt là khi sử dụng `Fetch API`. Do đó, việc xác định một cách chính xác phần trăm tải là không khả thi trong một số trường hợp.

## Tóm tắt một câu
Sự kiện `onprogress` trong JavaScript cho phép theo dõi tiến trình tải dữ liệu trong các yêu cầu mạng, cải thiện trải nghiệm người dùng.