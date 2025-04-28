<!--
Meta Description: # FileReader trong JavaScript: Hướng dẫn chi tiết và đầy đủ ## Tóm tắt FileReader là một API trong JavaScript cho phép bạn đọc nội dung của các tập ti...
Meta Keywords: tin, tập, file, đọc, filereader
-->

# FileReader trong JavaScript: Hướng dẫn chi tiết và đầy đủ

## Tóm tắt
FileReader là một API trong JavaScript cho phép bạn đọc nội dung của các tập tin (file) mà người dùng chọn thông qua một input HTML. Nó hỗ trợ nhiều định dạng dữ liệu và giúp truyền tải thông tin từ tập tin vào ứng dụng web một cách hiệu quả.

## Tài liệu
### Mục đích
FileReader được sử dụng để đọc nội dung của các tập tin mà người dùng chọn, chẳng hạn như hình ảnh, tài liệu văn bản, hoặc bất kỳ loại tập tin nào khác. Nó cho phép bạn xử lý dữ liệu mà không cần phải tải lên máy chủ.

### Cách sử dụng
Để sử dụng FileReader, bạn cần tạo một đối tượng FileReader và sử dụng các phương thức của nó để đọc dữ liệu từ một đối tượng File. Đầu tiên, bạn cần có một input HTML với kiểu `file` để người dùng chọn tập tin.

```html
<input type="file" id="fileInput">
```

Sau đó, bạn có thể sử dụng JavaScript để xử lý sự kiện khi người dùng chọn tập tin:

```javascript
const input = document.getElementById('fileInput');
const reader = new FileReader();

input.addEventListener('change', (event) => {
    const file = event.target.files[0]; // Lấy tập tin đầu tiên
    if (file) {
        reader.readAsText(file); // Đọc nội dung tập tin dưới dạng văn bản
    }
});

// Xử lý khi đọc hoàn tất
reader.onload = (event) => {
    console.log(event.target.result); // In nội dung tập tin ra console
};
```

### Chi tiết
- **Các phương thức chính của FileReader:**
  - `readAsText(file)`: Đọc tập tin dưới dạng văn bản.
  - `readAsDataURL(file)`: Đọc tập tin và trả về một URL chứa nội dung tập tin dưới dạng Data URL.
  - `readAsArrayBuffer(file)`: Đọc tập tin dưới dạng ArrayBuffer.
  - `readAsBinaryString(file)`: Đọc tập tin dưới dạng chuỗi nhị phân (không còn được khuyến nghị sử dụng).

- **Các sự kiện chính của FileReader:**
  - `onload`: Được gọi khi việc đọc tập tin hoàn tất thành công.
  - `onerror`: Được gọi khi có lỗi xảy ra trong quá trình đọc tập tin.
  - `onprogress`: Được gọi để thông báo tiến trình đọc tập tin.

## Ví dụ
### Đọc tập tin văn bản
```javascript
const input = document.getElementById('fileInput');
const reader = new FileReader();

input.addEventListener('change', (event) => {
    const file = event.target.files[0];
    if (file) {
        reader.readAsText(file);
    }
});

reader.onload = (event) => {
    console.log(event.target.result); // Hiển thị nội dung tập tin trong console
};
```

### Đọc tập tin hình ảnh
```javascript
const input = document.getElementById('fileInput');
const reader = new FileReader();

input.addEventListener('change', (event) => {
    const file = event.target.files[0];
    if (file) {
        reader.readAsDataURL(file);
    }
});

reader.onload = (event) => {
    const img = document.createElement('img');
    img.src = event.target.result; // Gán URL hình ảnh cho thẻ img
    document.body.appendChild(img); // Thêm hình ảnh vào trang
};
```

## Giải thích
### Những vấn đề thường gặp
- **Lỗi khi không có tập tin nào được chọn**: Trước khi gọi `reader.readAsText(file)`, bạn nên kiểm tra xem người dùng đã chọn một tập tin hay chưa.
- **Hỗ trợ trình duyệt**: FileReader được hỗ trợ trên hầu hết các trình duyệt hiện đại, nhưng không được hỗ trợ trên Internet Explorer. Đảm bảo kiểm tra tính tương thích trước khi triển khai.
- **Kích thước tập tin lớn**: Đọc tập tin lớn có thể tốn thời gian và làm chậm ứng dụng. Hãy xem xét tối ưu hóa hoặc xử lý bất đồng bộ.

## Tóm tắt một câu
FileReader là một API trong JavaScript cho phép bạn đọc nội dung từ các tập tin mà người dùng chọn, hỗ trợ nhiều định dạng dữ liệu.