<!--
Meta Description: # Sự kiện "onunhandledrejection" trong JavaScript: Xử lý lỗi Promise chưa được bắt ## Tóm tắt Sự kiện `onunhandledrejection` trong JavaScript cho phép...
Meta Keywords: lỗi, promise, kiện, không, onunhandledrejection
-->

# Sự kiện "onunhandledrejection" trong JavaScript: Xử lý lỗi Promise chưa được bắt 

## Tóm tắt
Sự kiện `onunhandledrejection` trong JavaScript cho phép lập trình viên lắng nghe và xử lý các lỗi không được xử lý trong Promise, giúp cải thiện khả năng gỡ lỗi và quản lý lỗi trong ứng dụng.

## Tài liệu
Sự kiện `onunhandledrejection` được kích hoạt khi một Promise bị từ chối (rejected) nhưng không có bất kỳ xử lý nào cho lỗi đó thông qua `.catch()` hoặc bằng cách sử dụng `try/catch` trong async/await. Việc sử dụng sự kiện này giúp phát hiện lỗi chưa được xử lý và thực hiện các biện pháp thích hợp, như ghi lại lỗi hoặc thông báo cho người dùng.

### Cú pháp
```javascript
window.onunhandledrejection = function(event) {
    // Xử lý lỗi tại đây
    console.error('Unhandled promise rejection:', event.reason);
};
```

### Các thuộc tính của sự kiện
- **event.reason**: Chứa thông tin về lý do mà Promise bị từ chối. Đây có thể là một lỗi hoặc bất kỳ giá trị nào mà Promise đã bị từ chối với.

## Ví dụ
### Ví dụ 1: Xử lý lỗi đơn giản
```javascript
window.onunhandledrejection = function(event) {
    console.error('Unhandled promise rejection:', event.reason);
};

const failingPromise = new Promise((_, reject) => {
    reject(new Error('Something went wrong!'));
});

// Không có .catch() để xử lý lỗi
failingPromise;
```

### Ví dụ 2: Sử dụng với async/await
```javascript
window.onunhandledrejection = function(event) {
    console.error('Unhandled promise rejection:', event.reason);
};

async function fetchData() {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
        throw new Error('Network response was not ok');
    }
    return response.json();
}

// Không có try/catch để xử lý lỗi
fetchData();
```

## Giải thích
Một trong những vấn đề phổ biến khi sử dụng Promise là việc quên xử lý lỗi. Nếu bạn không sử dụng `.catch()` hoặc không có `try/catch` cho các hàm async, lỗi sẽ không được bắt và sẽ dẫn đến việc phát sinh sự kiện `onunhandledrejection`. Điều này không chỉ làm cho ứng dụng của bạn gặp khó khăn trong việc gỡ lỗi mà còn có thể gây ra trải nghiệm không tốt cho người dùng. Do đó, việc sử dụng sự kiện này để ghi lại hoặc thông báo lỗi là rất cần thiết.

### Lưu ý
- Đảm bảo rằng bạn đã đăng ký sự kiện `onunhandledrejection` trước khi thực hiện các Promise có khả năng bị từ chối.
- Sự kiện này có thể không được hỗ trợ trên một số trình duyệt cũ. Hãy kiểm tra tính tương thích trước khi triển khai.

## Tóm tắt một dòng
Sự kiện `onunhandledrejection` trong JavaScript giúp xử lý các lỗi Promise chưa được bắt, nâng cao khả năng gỡ lỗi và quản lý lỗi trong ứng dụng.