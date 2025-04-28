<!--
Meta Description: # EyeDropper trong JavaScript: Công Cụ Lựa Chọn Màu Sắc Trên Web ## Tóm Tắt EyeDropper là một API trong JavaScript cho phép người dùng chọn màu sắc tr...
Meta Keywords: eyedropper, màu, chọn, người, dùng
-->

# EyeDropper trong JavaScript: Công Cụ Lựa Chọn Màu Sắc Trên Web

## Tóm Tắt
EyeDropper là một API trong JavaScript cho phép người dùng chọn màu sắc trực tiếp từ màn hình. Tính năng này hữu ích trong các ứng dụng web cần thu thập thông tin màu sắc từ giao diện người dùng.

## Tài Liệu
### Mục Đích
EyeDropper API cung cấp một phương thức đơn giản để người dùng có thể chọn màu sắc từ bất kỳ điểm nào trên màn hình, giúp nâng cao trải nghiệm người dùng trong các ứng dụng liên quan đến thiết kế hoặc chỉnh sửa hình ảnh.

### Cách Sử Dụng
Để sử dụng EyeDropper, bạn cần tạo một đối tượng EyeDropper và gọi phương thức `open()` để mở công cụ chọn màu. Một khi người dùng chọn màu, bạn sẽ nhận được thông tin về màu sắc đó.

### Cú Pháp Cơ Bản
```javascript
// Tạo một đối tượng EyeDropper
const eyeDropper = new EyeDropper();

// Mở công cụ chọn màu
eyeDropper.open().then(result => {
    console.log(result.sRGBHex); // In mã màu hex
}).catch(err => {
    console.error(err); // Xử lý lỗi nếu có
});
```

## Ví Dụ
### Ví Dụ 1: Chọn màu sắc đơn giản
```javascript
const eyeDropper = new EyeDropper();

const button = document.getElementById('pick-color');
button.addEventListener('click', () => {
    eyeDropper.open().then(result => {
        document.body.style.backgroundColor = result.sRGBHex; // Đặt màu nền theo màu đã chọn
    }).catch(err => {
        console.error("Lỗi:", err);
    });
});
```

### Ví Dụ 2: Hiển thị mã màu đã chọn
```javascript
const eyeDropper = new EyeDropper();
const colorDisplay = document.getElementById('color-display');

eyeDropper.open().then(result => {
    colorDisplay.textContent = `Màu đã chọn: ${result.sRGBHex}`; // Hiển thị mã màu
}).catch(err => {
    console.error("Lỗi:", err);
});
```

## Giải Thích
- **Hạn Chế Trình Duyệt**: EyeDropper API hiện chỉ được hỗ trợ trên một số trình duyệt nhất định, như Chrome và Edge. Điều này có thể gây khó khăn cho người dùng sử dụng trình duyệt không tương thích.
- **Quyền Truy Cập**: Trước khi mở EyeDropper, ứng dụng cần có quyền truy cập, và người dùng có thể từ chối quyền này.
- **Tương Tác Trực Tiếp**: EyeDropper yêu cầu tương tác trực tiếp từ người dùng (như nhấp chuột) để mở, điều này không thể thực hiện tự động.

## Tóm Tắt Một Câu
EyeDropper là một API trong JavaScript cho phép người dùng chọn màu sắc trực tiếp từ màn hình, cải thiện trải nghiệm người dùng trong các ứng dụng web.