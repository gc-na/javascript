<!--
Meta Description: # Sự kiện onpointerleave trong JavaScript: Hướng dẫn và Ví dụ ## Tóm tắt Sự kiện `onpointerleave` trong JavaScript được sử dụng để phát hiện khi con t...
Meta Keywords: kiện, phần, con, trong, myelement
-->

# Sự kiện onpointerleave trong JavaScript: Hướng dẫn và Ví dụ

## Tóm tắt
Sự kiện `onpointerleave` trong JavaScript được sử dụng để phát hiện khi con trỏ chuột rời khỏi một phần tử trong trang web. Sự kiện này hỗ trợ việc xây dựng các tương tác phong phú và linh hoạt cho người dùng.

## Tài liệu
### Mục đích
Sự kiện `onpointerleave` được kích hoạt khi con trỏ chuột rời khỏi một phần tử mà nó đang ở bên trong. Điều này có thể hữu ích trong nhiều tình huống, chẳng hạn như khi bạn muốn ẩn một menu hoặc một thông báo khi người dùng không còn tương tác với một phần tử cụ thể.

### Cách sử dụng
Sự kiện `onpointerleave` có thể được sử dụng như một thuộc tính của phần tử HTML hoặc thông qua sự kiện lắng nghe (Event Listener) trong JavaScript.

#### Cú pháp
```javascript
element.onpointerleave = function(event) {
    // Xử lý sự kiện
};
```
Hoặc với Event Listener:
```javascript
element.addEventListener('pointerleave', function(event) {
    // Xử lý sự kiện
});
```

### Thông tin chi tiết
- **Sự kiện:** `pointerleave`
- **Phạm vi:** Bắt đầu từ phần tử mà con trỏ chuột đang nằm trong và kết thúc khi con trỏ rời khỏi phần tử đó.
- **Tham số:** Sự kiện `PointerEvent` sẽ được truyền vào hàm xử lý, cung cấp thông tin chi tiết về sự kiện như vị trí và loại con trỏ.

## Ví dụ
### Ví dụ cơ bản
```html
<div id="myElement" style="width: 200px; height: 200px; background-color: lightblue;">
    Di chuột vào đây rồi rời khỏi
</div>

<script>
    const myElement = document.getElementById('myElement');

    myElement.onpointerleave = function(event) {
        console.log('Con trỏ đã rời khỏi phần tử!');
        myElement.style.backgroundColor = 'lightcoral';
    };
</script>
```

### Ví dụ với Event Listener
```html
<div id="myElement" style="width: 200px; height: 200px; background-color: lightblue;">
    Di chuột vào đây rồi rời khỏi
</div>

<script>
    const myElement = document.getElementById('myElement');

    myElement.addEventListener('pointerleave', function(event) {
        console.log('Con trỏ đã rời khỏi phần tử!');
        myElement.style.backgroundColor = 'lightcoral';
    });
</script>
```

## Giải thích
- **Lưu ý về khả năng tương thích:** Sự kiện `onpointerleave` là một phần của API Pointer Events, vì vậy cần kiểm tra khả năng tương thích với các trình duyệt mà bạn muốn hỗ trợ.
- **Khác biệt với sự kiện mouseleave:** `onpointerleave` không chỉ phản ứng với chuột mà còn với các thiết bị cảm ứng, trong khi `mouseleave` chỉ dành cho chuột.
- **Sự kiện con:** Nếu bạn có phần tử con bên trong phần tử gốc, `pointerleave` sẽ không được kích hoạt cho phần tử gốc nếu con trỏ chỉ đơn giản là di chuyển giữa các phần tử con.

## Tóm tắt một dòng
Sự kiện `onpointerleave` trong JavaScript cho phép phát hiện khi con trỏ chuột rời khỏi một phần tử, hữu ích cho việc cải thiện trải nghiệm người dùng.