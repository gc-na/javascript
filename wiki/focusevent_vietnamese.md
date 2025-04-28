<!--
Meta Description: # Sự kiện FocusEvent trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt Sự kiện FocusEvent trong JavaScript cho phép bạn theo dõi và xử lý các t...
Meta Keywords: kiện, tập, trung, các, phần
-->

# Sự kiện FocusEvent trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
Sự kiện FocusEvent trong JavaScript cho phép bạn theo dõi và xử lý các thay đổi khi một phần tử nhận được hoặc mất tập trung, điều này rất hữu ích trong việc cải thiện trải nghiệm người dùng trên các trang web.

## Tài liệu
### Mục đích
FocusEvent là một sự kiện trong JavaScript được kích hoạt khi một phần tử nhận được hoặc mất tập trung. Điều này thường xảy ra với các phần tử như `<input>`, `<textarea>`, hoặc các phần tử tương tác khác. Sự kiện này có thể được sử dụng để thực hiện các hành động như xác thực đầu vào, thay đổi giao diện người dùng hoặc thông báo cho người dùng.

### Cú pháp
Để lắng nghe sự kiện FocusEvent, bạn có thể sử dụng các phương thức như `addEventListener`. Sự kiện này có hai loại chính:
- `focus`: khi phần tử nhận được tập trung.
- `blur`: khi phần tử mất tập trung.

### Sử dụng
```javascript
// Lắng nghe sự kiện focus
document.getElementById('myInput').addEventListener('focus', function() {
    console.log('Input đang được tập trung');
});

// Lắng nghe sự kiện blur
document.getElementById('myInput').addEventListener('blur', function() {
    console.log('Input đã mất tập trung');
});
```

## Ví dụ
### Ví dụ 1: Sử dụng sự kiện focus
```html
<input type="text" id="myInput" placeholder="Nhập tên của bạn">
<script>
    document.getElementById('myInput').addEventListener('focus', function() {
        this.style.borderColor = 'blue'; // Thay đổi màu viền khi được tập trung
    });
</script>
```

### Ví dụ 2: Sử dụng sự kiện blur
```html
<input type="text" id="myInput" placeholder="Nhập tên của bạn">
<script>
    document.getElementById('myInput').addEventListener('blur', function() {
        this.style.borderColor = 'red'; // Thay đổi màu viền khi mất tập trung
    });
</script>
```

## Giải thích
Một số điều cần lưu ý khi làm việc với FocusEvent:
- Sự kiện focus không thể được kích hoạt bằng JavaScript. Bạn chỉ có thể sử dụng phương thức `.focus()` để tập trung vào một phần tử.
- Tương tự, sự kiện blur cũng không thể được kích hoạt bằng JavaScript; bạn chỉ có thể sử dụng `.blur()` để làm mất tập trung.
- Hãy cẩn thận với các phần tử có thể nhận tập trung, vì không phải tất cả các phần tử đều có thể nhận sự kiện focus (ví dụ: các phần tử `<div>` và `<span>` không thể nhận sự kiện này trừ khi có thuộc tính `tabindex`).

## Tóm tắt một dòng
FocusEvent trong JavaScript giúp theo dõi và xử lý các hành động khi các phần tử nhận hoặc mất tập trung, cải thiện trải nghiệm người dùng.