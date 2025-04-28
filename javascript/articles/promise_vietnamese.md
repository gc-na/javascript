<!--
Meta Description: # Promise trong JavaScript: Hứa hẹn trong Lập trình Phiên bản Không đồng bộ ## Tóm tắt Promise trong JavaScript là một đối tượng đại diện cho một giá ...
Meta Keywords: promise, một, thành, tác, khi
-->

# Promise trong JavaScript: Hứa hẹn trong Lập trình Phiên bản Không đồng bộ

## Tóm tắt
Promise trong JavaScript là một đối tượng đại diện cho một giá trị có thể có trong tương lai, cho phép xử lý bất đồng bộ một cách dễ dàng và hiệu quả.

## Tài liệu
Promise là một phần quan trọng trong lập trình JavaScript, đặc biệt là khi làm việc với các tác vụ bất đồng bộ như gọi API hoặc đọc tệp. Promise giúp quản lý trạng thái của một tác vụ, bao gồm ba trạng thái chính:

1. **Pending (Chờ)**: Trạng thái ban đầu, nghĩa là tác vụ vẫn đang diễn ra.
2. **Fulfilled (Hoàn thành)**: Trạng thái khi tác vụ thành công và trả về một giá trị.
3. **Rejected (Bị từ chối)**: Trạng thái khi tác vụ thất bại và trả về lý do thất bại.

### Cú pháp
```javascript
let promise = new Promise((resolve, reject) => {
    // Thực hiện một tác vụ bất đồng bộ
    if (/* điều kiện thành công */) {
        resolve(value); // khi thành công
    } else {
        reject(error); // khi thất bại
    }
});
```

### Sử dụng
Để sử dụng Promise, bạn có thể gọi phương thức `then()` để xử lý giá trị khi Promise hoàn thành và `catch()` để xử lý lỗi khi Promise bị từ chối.

```javascript
promise
    .then(value => {
        // Xử lý giá trị thành công
    })
    .catch(error => {
        // Xử lý lỗi
    });
```

## Ví dụ
### Ví dụ 1: Promise đơn giản
```javascript
let myPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve("Tác vụ hoàn thành!");
    }, 2000);
});

myPromise
    .then(result => console.log(result)) // In ra "Tác vụ hoàn thành!" sau 2 giây
    .catch(error => console.error(error));
```

### Ví dụ 2: Xử lý lỗi
```javascript
let myPromise = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("Có lỗi xảy ra!");
    }, 2000);
});

myPromise
    .then(result => console.log(result))
    .catch(error => console.error(error)); // In ra "Có lỗi xảy ra!" sau 2 giây
```

## Giải thích
Khi làm việc với Promise, có một số điều cần lưu ý:

- **Chỉ có thể chuyển từ Pending sang Fulfilled hoặc Rejected**: Một Promise chỉ có thể thay đổi trạng thái một lần, do đó, bạn không thể thay đổi trạng thái từ Fulfilled hoặc Rejected trở về Pending.
- **Chạy bất đồng bộ**: Các Promise không chặn luồng thực thi, vì vậy bạn có thể xử lý các tác vụ khác trong khi chờ đợi Promise hoàn thành.
- **Chaining**: Bạn có thể gọi nhiều `then()` liên tiếp để tạo thành chuỗi xử lý, giúp cải thiện khả năng đọc mã.

## Tóm tắt một dòng
Promise trong JavaScript là một công cụ mạnh mẽ để quản lý các tác vụ bất đồng bộ, cho phép lập trình viên xử lý thành công và lỗi một cách rõ ràng và hiệu quả.