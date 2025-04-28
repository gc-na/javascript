<!--
Meta Description: # FileList trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng ## Tóm tắt `FileList` là một đối tượng trong JavaScript đại diện cho một danh sách các đối t...
Meta Keywords: filelist, tệp, các, trong, dụng
-->

# FileList trong JavaScript: Hiểu Biết Cơ Bản và Ứng Dụng

## Tóm tắt
`FileList` là một đối tượng trong JavaScript đại diện cho một danh sách các đối tượng `File`, thường được sử dụng trong các ứng dụng web để xử lý các tệp được tải lên thông qua các phần tử `<input>` với thuộc tính `type="file"`.

## Tài liệu
### Mục đích
`FileList` được sử dụng để quản lý và xử lý nhiều tệp được chọn bởi người dùng trong các ứng dụng web. Nó cho phép lập trình viên truy cập và thao tác với thông tin của các tệp, như tên tệp, kích thước và loại tệp.

### Cách sử dụng
Để sử dụng `FileList`, bạn cần có một phần tử `<input>` với thuộc tính `type="file"`. Bạn có thể lấy danh sách các tệp đã chọn bằng cách truy cập thuộc tính `files` của phần tử này, thuộc tính này trả về một đối tượng `FileList`.

```html
<input type="file" id="fileInput" multiple>
<button id="uploadBtn">Tải lên</button>
```

### Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng `FileList` trong JavaScript:

```javascript
document.getElementById('uploadBtn').addEventListener('click', function() {
    const input = document.getElementById('fileInput');
    const fileList = input.files;

    for (let i = 0; i < fileList.length; i++) {
        console.log(`Tên tệp: ${fileList[i].name}, Kích thước: ${fileList[i].size} bytes`);
    }
});
```

Trong ví dụ trên, khi người dùng bấm nút "Tải lên", thông tin về từng tệp trong `FileList` sẽ được in ra console.

## Giải thích
### Những điều cần lưu ý
- **Chỉ đọc**: Đối tượng `FileList` là chỉ đọc, nghĩa là bạn không thể thêm hoặc xóa tệp từ danh sách này.
- **Hỗ trợ nhiều tệp**: Nếu phần tử `<input>` có thuộc tính `multiple`, người dùng có thể chọn nhiều tệp cùng một lúc, và `FileList` sẽ chứa tất cả các tệp đã chọn.
- **Trình duyệt hỗ trợ**: Đảm bảo rằng các trình duyệt mà bạn đang nhắm đến hỗ trợ các tính năng liên quan đến đối tượng `FileList`, vì một số trình duyệt cũ có thể không hỗ trợ đầy đủ.

## Tóm tắt một dòng
`FileList` trong JavaScript là một đối tượng dùng để đại diện cho danh sách các tệp được người dùng chọn trong ứng dụng web, cho phép truy cập thông tin chi tiết về từng tệp.