<!--
Meta Description: # Sự Kiện onfocus trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm Tắt Sự kiện `onfocus` trong JavaScript được sử dụng để xác định khi một phần tử...
Meta Keywords: onfocus, kiện, phần, người, dùng
-->

# Sự Kiện onfocus trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm Tắt
Sự kiện `onfocus` trong JavaScript được sử dụng để xác định khi một phần tử giao diện người dùng, như ô nhập liệu, nhận được tiêu điểm từ người dùng. Đây là một sự kiện quan trọng trong việc tạo các trải nghiệm tương tác và thân thiện hơn với người dùng.

## Tài Liệu
### Mục Đích
Sự kiện `onfocus` cho phép lập trình viên thực hiện các hành động nhất định khi một phần tử nhận được tiêu điểm. Điều này hữu ích trong việc tạo các hiệu ứng trực quan hoặc xác nhận đầu vào của người dùng.

### Cách Sử Dụng
Sự kiện `onfocus` có thể được gán cho các phần tử như `<input>`, `<textarea>`, hoặc bất kỳ phần tử nào có thể nhận tiêu điểm. Sự kiện này có thể được sử dụng bằng cách thêm thuộc tính `onfocus` vào phần tử HTML hoặc thông qua JavaScript.

#### Cú Pháp:
```html
<input type="text" onfocus="myFunction()">
```
Hoặc sử dụng JavaScript:
```javascript
const inputElement = document.getElementById("myInput");
inputElement.onfocus = function() {
    // Hành động khi phần tử nhận tiêu điểm
};
```

## Ví Dụ
### Ví Dụ Cơ Bản
```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Ví Dụ onfocus</title>
    <script>
        function highlight() {
            document.getElementById("myInput").style.backgroundColor = "yellow";
        }
        
        function reset() {
            document.getElementById("myInput").style.backgroundColor = "";
        }
    </script>
</head>
<body>
    <input type="text" id="myInput" onfocus="highlight()" onblur="reset()" placeholder="Nhập tên của bạn">
</body>
</html>
```
Trong ví dụ này, khi người dùng nhấp vào ô nhập liệu, nền của ô sẽ chuyển sang màu vàng, và khi ô mất tiêu điểm, màu nền sẽ trở lại bình thường.

## Giải Thích
### Những Lỗi Thường Gặp
- **Không sử dụng `onblur`:** Nếu bạn chỉ sử dụng `onfocus` mà không có sự kiện `onblur`, người dùng có thể không thấy rõ sự trở lại trạng thái ban đầu của phần tử.
- **Thiếu kiểm tra đầu vào:** Khi sử dụng sự kiện `onfocus`, lập trình viên thường quên kiểm tra tính hợp lệ của dữ liệu đầu vào. Điều này có thể dẫn đến trải nghiệm người dùng không tốt.
- **Chỉ định sai phần tử:** Đảm bảo rằng phần tử bạn muốn gán sự kiện `onfocus` là đúng, nếu không, sự kiện sẽ không hoạt động như mong đợi.

## Tóm Tắt Một Dòng
Sự kiện `onfocus` trong JavaScript cho phép bạn thực hiện các hành động khi một phần tử giao diện nhận được tiêu điểm, tạo ra trải nghiệm tương tác tốt hơn cho người dùng.