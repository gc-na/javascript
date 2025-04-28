<!--
Meta Description: # onrejectionhandled: Xử lý Lỗi Promise trong JavaScript ## Tóm tắt Sự kiện `onrejectionhandled` trong JavaScript cho phép lập trình viên theo dõi và ...
Meta Keywords: promise, lỗi, onrejectionhandled, kiện, các
-->

# onrejectionhandled: Xử lý Lỗi Promise trong JavaScript

## Tóm tắt
Sự kiện `onrejectionhandled` trong JavaScript cho phép lập trình viên theo dõi và xử lý các lỗi khi một Promise bị từ chối và được xử lý sau đó. Điều này giúp tăng cường khả năng quản lý lỗi trong các ứng dụng bất đồng bộ.

## Tài liệu

### Mục đích
Sự kiện `onrejectionhandled` được kích hoạt khi một Promise bị từ chối và một handler (trình xử lý) đã được đăng ký để xử lý lỗi đó. Sự kiện này giúp bạn theo dõi các lỗi không được xử lý kịp thời, tăng cường khả năng quản lý lỗi và cải thiện hiệu suất của ứng dụng.

### Cách sử dụng
Để sử dụng sự kiện `onrejectionhandled`, bạn cần định nghĩa một hàm xử lý và gán nó cho thuộc tính `onrejectionhandled` của đối tượng `window`. Hàm này sẽ nhận một đối tượng `PromiseRejectionEvent` làm tham số.

```javascript
window.onrejectionhandled = function(event) {
    console.log('Promise đã được xử lý:', event.promise);
    console.log('Lý do từ chối:', event.reason);
};
```

### Chi tiết
- **Sự kiện**: `onrejectionhandled` là một sự kiện của đối tượng `window`.
- **Tham số**: Hàm xử lý nhận một đối tượng `PromiseRejectionEvent` với các thuộc tính sau:
  - `promise`: Promise đã bị từ chối.
  - `reason`: Lý do từ chối Promise.

## Ví dụ

### Ví dụ cơ bản
```javascript
const myPromise = new Promise((resolve, reject) => {
    reject('Có lỗi xảy ra!');
});

window.onrejectionhandled = function(event) {
    console.log('Promise đã được xử lý:', event.promise);
    console.log('Lý do từ chối:', event.reason);
};

// Kích hoạt sự kiện
myPromise.catch(error => console.error(error));
```

## Giải thích
- **Cạm bẫy phổ biến**: Một số lập trình viên có thể không sử dụng sự kiện này đúng cách, dẫn đến việc bỏ lỡ các lỗi quan trọng. Hãy chắc chắn rằng bạn đã đăng ký sự kiện trước khi bất kỳ Promise nào có khả năng bị từ chối.
- **Ghi chú bổ sung**: `onrejectionhandled` không được gọi cho các Promise đã bị từ chối mà không có bất kỳ handler nào. Do đó, việc sử dụng `.catch()` hoặc `try-catch` là rất quan trọng để đảm bảo bạn không bỏ lỡ các lỗi.

## Tóm tắt một dòng
Sự kiện `onrejectionhandled` trong JavaScript cho phép theo dõi và xử lý các lỗi từ các Promise bị từ chối, nâng cao khả năng quản lý lỗi trong ứng dụng.