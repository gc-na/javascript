<!--
Meta Description: # Sự kiện ontransitionend trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt Sự kiện `ontransitionend` trong JavaScript cho phép lập trình viên ...
Meta Keywords: tiếp, chuyển, kiện, ontransitionend, khi
-->

# Sự kiện ontransitionend trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
Sự kiện `ontransitionend` trong JavaScript cho phép lập trình viên theo dõi khi một hiệu ứng chuyển tiếp CSS hoàn thành, giúp cải thiện trải nghiệm người dùng và tương tác với giao diện.

## Tài liệu
Sự kiện `ontransitionend` được kích hoạt khi một chuyển tiếp CSS kết thúc. Điều này rất hữu ích trong việc thực hiện các hành động hoặc thay đổi trạng thái DOM sau khi hiệu ứng chuyển tiếp hoàn tất, chẳng hạn như ẩn hoặc hiển thị các phần tử. Sự kiện này có thể được sử dụng để cải thiện khả năng tương tác của giao diện bằng cách đồng bộ hóa các thay đổi với hiệu ứng chuyển tiếp.

### Cú pháp
Để sử dụng sự kiện `ontransitionend`, bạn có thể gán một hàm xử lý sự kiện cho phần tử DOM. Ví dụ:

```javascript
element.addEventListener('transitionend', function(event) {
    // Xử lý sự kiện khi chuyển tiếp kết thúc
});
```

### Tham số
- `event`: Đối tượng sự kiện chứa thông tin về sự kiện vừa xảy ra, bao gồm tên thuộc tính CSS đã chuyển tiếp, thời gian chuyển tiếp, và phần tử DOM liên quan.

## Ví dụ
Dưới đây là một ví dụ đơn giản về việc sử dụng `ontransitionend`:

```html
<div id="box" style="width: 100px; height: 100px; background-color: red; transition: width 2s;"></div>
<button id="toggle">Thay đổi kích thước</button>

<script>
    const box = document.getElementById('box');
    const button = document.getElementById('toggle');

    button.addEventListener('click', () => {
        box.style.width = box.style.width === '100px' ? '200px' : '100px';
    });

    box.addEventListener('transitionend', (event) => {
        console.log('Chuyển tiếp hoàn tất cho: ' + event.propertyName);
    });
</script>
```

Khi bạn nhấn nút, chiều rộng của hộp sẽ thay đổi và khi chuyển tiếp hoàn tất, một thông báo sẽ được ghi vào console.

## Giải thích
Một số điều cần lưu ý khi làm việc với `ontransitionend`:

1. **Nhiều chuyển tiếp**: Nếu một phần tử có nhiều hiệu ứng chuyển tiếp, sự kiện `ontransitionend` sẽ được kích hoạt cho mỗi hiệu ứng khi chúng hoàn tất. Bạn có thể kiểm tra thuộc tính `event.propertyName` để xác định thuộc tính nào đã hoàn thành.

2. **Chuyển tiếp không kích hoạt**: Nếu một hiệu ứng CSS không được áp dụng, hoặc nếu bạn thay đổi thuộc tính CSS trực tiếp mà không có chuyển tiếp, sự kiện `ontransitionend` sẽ không được gọi.

3. **Thời gian chuyển tiếp**: Đảm bảo rằng bạn đặt thời gian chuyển tiếp hợp lý trong CSS; nếu thời gian quá ngắn, có thể bạn sẽ không thấy sự kiện `ontransitionend` được kích hoạt trong các tình huống nhất định.

## Tóm tắt một dòng
Sự kiện `ontransitionend` trong JavaScript cho phép theo dõi và xử lý các hành động khi hiệu ứng chuyển tiếp CSS hoàn thành.