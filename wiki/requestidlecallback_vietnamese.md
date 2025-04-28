<!--
Meta Description: # requestIdleCallback: Tối ưu hóa hiệu suất trong JavaScript ## Tóm tắt `requestIdleCallback` là một phương thức trong JavaScript cho phép lập trình v...
Meta Keywords: không, thực, hiện, requestidlecallback, trình
-->

# requestIdleCallback: Tối ưu hóa hiệu suất trong JavaScript

## Tóm tắt
`requestIdleCallback` là một phương thức trong JavaScript cho phép lập trình viên thực hiện các tác vụ không khẩn cấp khi trình duyệt đang rảnh rỗi, từ đó giúp cải thiện hiệu suất và trải nghiệm người dùng.

## Tài liệu
Phương thức `requestIdleCallback` được sử dụng để lập lịch các tác vụ không quan trọng trong thời gian mà trình duyệt không bận rộn xử lý các công việc khác. Điều này rất hữu ích trong việc tối ưu hóa việc sử dụng CPU và đảm bảo rằng các tác vụ chính như vẽ lại giao diện người dùng không bị gián đoạn.

### Cú pháp
```javascript
requestIdleCallback(callback[, options]);
```

#### Tham số
- **callback**: Hàm sẽ được gọi khi trình duyệt đang rảnh rỗi.
- **options** (tùy chọn): Một đối tượng chứa các tùy chọn như `timeout`, xác định thời gian tối đa để chờ trước khi thực hiện callback.

#### Trả về
Phương thức `requestIdleCallback` trả về một ID mà bạn có thể sử dụng để hủy callback bằng cách gọi `cancelIdleCallback`.

## Ví dụ
### Ví dụ cơ bản
```javascript
function myIdleCallback(deadline) {
    while (deadline.timeRemaining() > 0) {
        // Thực hiện công việc không khẩn cấp ở đây
        console.log('Thực hiện công việc không khẩn cấp');
    }
}

requestIdleCallback(myIdleCallback);
```

### Ví dụ với tùy chọn timeout
```javascript
function myIdleCallback(deadline) {
    while (deadline.timeRemaining() > 0) {
        // Thực hiện công việc không khẩn cấp ở đây
        console.log('Thực hiện công việc không khẩn cấp');
    }
}

const idleCallbackId = requestIdleCallback(myIdleCallback, { timeout: 1000 });
```

## Giải thích
Mặc dù `requestIdleCallback` rất hữu ích, nhưng có một số điểm cần lưu ý:
- **Thời gian không đảm bảo**: Callback không được thực hiện ngay lập tức. Nếu trình duyệt đang bận, callback có thể bị trì hoãn.
- **Số lần thực hiện**: Nếu nhiều tác vụ được lên lịch, các callback sẽ được thực hiện theo thứ tự và có thể bị trì hoãn nếu trình duyệt bận.
- **Không hỗ trợ trên tất cả trình duyệt**: Hãy kiểm tra tính tương thích của trình duyệt trước khi sử dụng.

## Tóm tắt ngắn gọn
`requestIdleCallback` là phương thức giúp tối ưu hóa hiệu suất bằng cách cho phép thực hiện các tác vụ không khẩn cấp khi trình duyệt không bận rộn.