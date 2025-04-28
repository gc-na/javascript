<!--
Meta Description: # Sự kiện FontFaceSetLoadEvent trong JavaScript: Hướng dẫn Chi tiết ## Tóm tắt Sự kiện `FontFaceSetLoadEvent` trong JavaScript cung cấp thông tin về q...
Meta Keywords: font, tải, kiện, các, một
-->

# Sự kiện FontFaceSetLoadEvent trong JavaScript: Hướng dẫn Chi tiết

## Tóm tắt
Sự kiện `FontFaceSetLoadEvent` trong JavaScript cung cấp thông tin về quá trình tải font, cho phép lập trình viên theo dõi và xử lý các sự kiện liên quan đến việc tải font từ một tập hợp font.

## Tài liệu
### Mục đích
`FontFaceSetLoadEvent` là một sự kiện được phát ra khi một hoặc nhiều font trong `FontFaceSet` đã được tải thành công. Điều này rất hữu ích trong việc tối ưu hóa trải nghiệm người dùng, đặc biệt trong các ứng dụng web yêu cầu thời gian tải font chính xác.

### Cách sử dụng
Để sử dụng `FontFaceSetLoadEvent`, bạn cần phải thêm một listener cho sự kiện này trên một đối tượng `FontFaceSet`. Sự kiện này chứa các thông tin như tên của các font được tải và trạng thái tải về.

#### Cú pháp
```javascript
document.fonts.ready.then(() => {
    document.fonts.add(new FontFace('MyFont', 'url(myfont.woff2)'));
    document.fonts.load('1em MyFont').then((fontFaces) => {
        // Font đã được tải thành công
    }).catch((error) => {
        console.error('Font loading failed: ', error);
    });
});

document.fonts.onloadingdone = (event) => {
    console.log('Fonts loaded: ', event.fontfaces);
};
```

### Chi tiết
- **Thuộc tính**: 
  - `fontfaces`: Trả về danh sách các font đã được tải.
  
- **Sự kiện**:
  - Sự kiện này sẽ được kích hoạt khi tất cả các font đã được tải xong. Bạn có thể sử dụng nó để thực hiện các hành động cụ thể, như cập nhật giao diện người dùng hoặc thông báo cho người dùng rằng các font đã sẵn sàng.

## Ví dụ
### Ví dụ 1: Theo dõi tải font
```javascript
document.fonts.ready.then(() => {
    console.log('Tất cả font đã sẵn sàng!');
}).catch((error) => {
    console.error('Có lỗi xảy ra khi tải font: ', error);
});
```

### Ví dụ 2: Thêm sự kiện cho `FontFaceSetLoadEvent`
```javascript
document.fonts.onloadingdone = (event) => {
    console.log('Font đã được tải thành công:', event.fontfaces);
};
```

## Giải thích
Khi làm việc với `FontFaceSetLoadEvent`, có một số điểm cần lưu ý:
- **Thời gian tải**: Thời gian tải font có thể khác nhau phụ thuộc vào kết nối mạng, vì vậy nên sử dụng promise để đảm bảo rằng các hành động như cập nhật UI chỉ diễn ra sau khi font đã tải xong.
- **Thay đổi trình duyệt**: Một số trình duyệt có thể không hỗ trợ tất cả các loại font hoặc sự kiện này, vì vậy hãy kiểm tra khả năng tương thích trước khi triển khai.

## Tóm tắt một câu
`FontFaceSetLoadEvent` trong JavaScript cho phép bạn theo dõi và xử lý sự kiện tải font từ `FontFaceSet`, giúp cải thiện trải nghiệm người dùng trong các ứng dụng web.