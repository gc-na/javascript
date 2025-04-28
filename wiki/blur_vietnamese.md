<!--
Meta Description: # Hiệu ứng Blur trong JavaScript: Tạo Độ Mờ cho Phần Tử ## Tóm Tắt Trong JavaScript, "blur" không chỉ đề cập đến việc làm mờ hình ảnh hay hiệu ứng mà ...
Meta Keywords: kiện, blur, phần, trong, người
-->

# Hiệu ứng Blur trong JavaScript: Tạo Độ Mờ cho Phần Tử

## Tóm Tắt
Trong JavaScript, "blur" không chỉ đề cập đến việc làm mờ hình ảnh hay hiệu ứng mà còn là một sự kiện quan trọng trong việc xử lý tương tác người dùng với các phần tử giao diện. Sự kiện blur xảy ra khi phần tử mất tiêu điểm (focus), thường được sử dụng để thực hiện các hành động cần thiết khi người dùng rời khỏi trường nhập liệu.

## Tài Liệu
### Mục Đích
Sự kiện `blur` trong JavaScript giúp lập trình viên theo dõi khi một phần tử (thường là trường nhập liệu) mất tiêu điểm. Điều này rất hữu ích trong việc xác thực dữ liệu, gợi ý người dùng, hoặc đơn giản là để cải thiện trải nghiệm người dùng.

### Cách Sử Dụng
Để sử dụng sự kiện `blur`, bạn có thể thêm một listener cho sự kiện này trên một phần tử HTML. Dưới đây là cú pháp cơ bản:

```javascript
element.addEventListener('blur', function(event) {
    // Code để xử lý sự kiện blur
});
```

### Chi Tiết
- **Phần Tử**: `element` có thể là bất kỳ phần tử HTML nào hỗ trợ tiêu điểm, chẳng hạn như `<input>`, `<textarea>`, hoặc bất kỳ phần tử nào có thuộc tính `tabindex`.
- **Sự Kiện**: Khi phần tử mất tiêu điểm, hàm callback được gọi và đối tượng `event` chứa thông tin về sự kiện.

## Ví Dụ
### Ví dụ Cơ Bản
```html
<input type="text" id="username" placeholder="Nhập tên người dùng">
<script>
    const usernameInput = document.getElementById('username');

    usernameInput.addEventListener('blur', function() {
        console.log('Trường nhập liệu đã mất tiêu điểm.');
    });
</script>
```

### Ví dụ Xác Thực Dữ Liệu
```html
<input type="email" id="email" placeholder="Nhập email của bạn">
<script>
    const emailInput = document.getElementById('email');

    emailInput.addEventListener('blur', function() {
        if (!this.value.includes('@')) {
            alert('Vui lòng nhập địa chỉ email hợp lệ.');
        }
    });
</script>
```

## Giải Thích
### Những Lưu Ý Chung
- **Sự Kiện Đồng Thời**: Sự kiện `blur` xảy ra sau sự kiện `focusout`, nhưng không giống như `focusout`, sự kiện `blur` chỉ xảy ra trên phần tử hiện tại.
- **Trình Duyệt Hỗ Trợ**: Hầu hết tất cả các trình duyệt hiện đại đều hỗ trợ sự kiện này, nhưng cần kiểm tra khả năng tương thích cho các trình duyệt cũ hơn.
- **Thao Tác Tương Tác**: Đảm bảo rằng hành động trong hàm callback không làm gián đoạn trải nghiệm người dùng, vì điều này có thể gây khó chịu.

## Tóm Tắt Một Dòng
Sự kiện `blur` trong JavaScript cho phép theo dõi khi một phần tử mất tiêu điểm, rất hữu ích cho việc xác thực dữ liệu và cải thiện trải nghiệm người dùng.