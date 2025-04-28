<!--
Meta Description: # Sự Kiện AnimationEvent trong JavaScript: Hướng Dẫn Chi Tiết ## Tóm Tắt Sự kiện `AnimationEvent` trong JavaScript cho phép các lập trình viên theo dõ...
Meta Keywords: kiện, hoạt, ảnh, các, element
-->

# Sự Kiện AnimationEvent trong JavaScript: Hướng Dẫn Chi Tiết

## Tóm Tắt
Sự kiện `AnimationEvent` trong JavaScript cho phép các lập trình viên theo dõi và xử lý các sự kiện liên quan đến hoạt ảnh trong DOM, giúp tạo ra trải nghiệm người dùng mượt mà và tương tác hơn.

## Tài Liệu
### Mục Đích
`AnimationEvent` là một đối tượng sự kiện trong JavaScript được phát sinh khi một hoạt ảnh CSS bắt đầu, kết thúc hoặc bị gián đoạn. Những sự kiện này bao gồm `animationstart`, `animationend`, và `animationiteration`, cho phép lập trình viên thực hiện các hành động cụ thể khi các sự kiện này xảy ra.

### Cách Sử Dụng
Để sử dụng `AnimationEvent`, bạn cần lắng nghe các sự kiện liên quan trên phần tử DOM mà bạn muốn theo dõi. Bạn có thể thêm các trình xử lý sự kiện bằng cách sử dụng phương thức `addEventListener()`.

#### Cú Pháp
```javascript
element.addEventListener('animationstart', function(event) {
    // Xử lý sự kiện bắt đầu hoạt ảnh
});

element.addEventListener('animationend', function(event) {
    // Xử lý sự kiện kết thúc hoạt ảnh
});

element.addEventListener('animationiteration', function(event) {
    // Xử lý sự kiện lặp lại hoạt ảnh
});
```

### Thông Tin Chi Tiết
`AnimationEvent` cung cấp các thuộc tính hữu ích như:
- `animationName`: Tên của hoạt ảnh đã được định nghĩa trong CSS.
- `elapsedTime`: Thời gian đã trôi qua từ khi hoạt ảnh bắt đầu (tính bằng giây).
- `pseudoElement`: Nếu hoạt ảnh áp dụng cho một pseudo-element, thuộc tính này sẽ chứa tên của pseudo-element đó.

### Ví Dụ
#### Ví Dụ 1: Theo Dõi Sự Kiện Kết Thúc Hoạt Ảnh
```html
<div id="myElement" class="myAnimation">Hello World</div>

<style>
.myAnimation {
    animation: fadeIn 2s;
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}
</style>

<script>
const element = document.getElementById('myElement');

element.addEventListener('animationend', function(event) {
    console.log('Hoạt ảnh đã kết thúc: ' + event.animationName);
});
</script>
```

#### Ví Dụ 2: Theo Dõi Sự Kiện Lặp Lại Hoạt Ảnh
```html
<div id="myElement" class="myAnimation">Hello Again</div>

<style>
.myAnimation {
    animation: bounce 1s infinite;
}

@keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-30px); }
}
</style>

<script>
const element = document.getElementById('myElement');

element.addEventListener('animationiteration', function(event) {
    console.log('Hoạt ảnh đã lặp lại: ' + event.animationName);
});
</script>
```

## Giải Thích
Một số cạm bẫy thường gặp khi làm việc với `AnimationEvent` bao gồm:
- Không chú ý đến tên hoạt ảnh trong CSS. Nếu tên không khớp, sự kiện sẽ không được kích hoạt.
- Lỗi trong việc lắng nghe sự kiện. Đảm bảo rằng bạn đã thêm trình xử lý sự kiện đúng cách và trên phần tử phù hợp.
- Các trình duyệt khác nhau có thể có cách triển khai khác nhau, vì vậy hãy kiểm tra tính tương thích và thử nghiệm trên nhiều trình duyệt.

## Tóm Tắt Một Dòng
`AnimationEvent` trong JavaScript cho phép theo dõi và xử lý các sự kiện liên quan đến hoạt ảnh CSS, mang đến trải nghiệm người dùng tốt hơn.