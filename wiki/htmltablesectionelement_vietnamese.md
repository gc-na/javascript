<!--
Meta Description: # HTMLTableSectionElement trong JavaScript: Tìm hiểu và Sử dụng ## Tóm tắt `HTMLTableSectionElement` là một giao diện trong JavaScript đại diện cho cá...
Meta Keywords: một, các, hàng, phần, tbody
-->

# HTMLTableSectionElement trong JavaScript: Tìm hiểu và Sử dụng

## Tóm tắt
`HTMLTableSectionElement` là một giao diện trong JavaScript đại diện cho các phần của bảng HTML, bao gồm `<thead>`, `<tbody>`, và `<tfoot>`. Nó cho phép lập trình viên truy cập và thao tác các phần này một cách dễ dàng.

## Tài liệu
`HTMLTableSectionElement` là một phần của DOM (Document Object Model) trong JavaScript, cho phép bạn tương tác với các phần của bảng HTML. Các phần này có thể chứa các hàng của bảng, giúp bạn tổ chức và định dạng dữ liệu một cách hợp lý.

### Mục đích
- Cung cấp một cách để truy cập và thao tác các phần trong bảng HTML.
- Hỗ trợ các thao tác như thêm, xóa hoặc sửa đổi hàng trong bảng.

### Cách sử dụng
Để sử dụng `HTMLTableSectionElement`, bạn cần truy cập đến một phần cụ thể của bảng. Bạn có thể làm điều này thông qua `document.getElementById()`, `document.querySelector()`, hoặc các phương thức truy cập DOM khác.

### Chi tiết
`HTMLTableSectionElement` có một số phương thức và thuộc tính hữu ích:
- `rows`: Trả về một danh sách các hàng trong phần của bảng.
- `insertRow()`: Thêm một hàng mới vào phần.
- `deleteRow()`: Xóa một hàng khỏi phần.

## Ví dụ
### Ví dụ 1: Truy cập và hiển thị số hàng trong `<tbody>`
```javascript
// Giả sử bạn có một bảng HTML với id là "myTable"
const table = document.getElementById('myTable');
const tbody = table.getElementsByTagName('tbody')[0];

console.log(`Số hàng trong tbody: ${tbody.rows.length}`);
```

### Ví dụ 2: Thêm một hàng mới vào `<thead>`
```javascript
const thead = table.getElementsByTagName('thead')[0];
const newRow = thead.insertRow();

const cell1 = newRow.insertCell(0);
cell1.textContent = 'Tiêu đề mới 1';

const cell2 = newRow.insertCell(1);
cell2.textContent = 'Tiêu đề mới 2';
```

### Ví dụ 3: Xóa một hàng từ `<tbody>`
```javascript
const tbody = table.getElementsByTagName('tbody')[0];
tbody.deleteRow(0); // Xóa hàng đầu tiên
```

## Giải thích
Khi làm việc với `HTMLTableSectionElement`, có một số điều cần lưu ý:
- **Chỉ mục hàng**: Khi sử dụng `deleteRow()`, hãy nhớ rằng chỉ mục bắt đầu từ 0. Nếu bạn xóa hàng, các chỉ mục sẽ thay đổi.
- **Thao tác DOM**: Các thao tác DOM có thể làm chậm hiệu năng nếu bạn thực hiện nhiều thay đổi liên tiếp. Hãy xem xét việc gộp các thay đổi lại với nhau nếu có thể.

## Tóm tắt một câu
`HTMLTableSectionElement` trong JavaScript cho phép lập trình viên truy cập và thao tác các phần của bảng HTML, bao gồm `<thead>`, `<tbody>`, và `<tfoot>`.