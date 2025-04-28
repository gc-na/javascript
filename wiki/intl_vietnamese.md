<!--
Meta Description: # Intl trong JavaScript: Hướng Dẫn Toàn Diện về Đối Tượng Quốc Tế Hóa ## Tóm tắt Intl là một đối tượng trong JavaScript giúp thực hiện các thao tác qu...
Meta Keywords: intl, định, dạng, ngôn, ngữ
-->

# Intl trong JavaScript: Hướng Dẫn Toàn Diện về Đối Tượng Quốc Tế Hóa

## Tóm tắt
Intl là một đối tượng trong JavaScript giúp thực hiện các thao tác quốc tế hóa, bao gồm định dạng số, ngày tháng và chuỗi. Nó cho phép lập trình viên xây dựng các ứng dụng đa ngôn ngữ và phù hợp với quy tắc định dạng của từng khu vực.

## Tài liệu
### Mục đích
Intl cung cấp các API để hỗ trợ quốc tế hóa trong JavaScript. Điều này rất hữu ích khi phát triển ứng dụng cần xử lý dữ liệu theo ngôn ngữ và văn hóa khác nhau.

### Cách sử dụng
Đối tượng Intl bao gồm một số thành phần chính:

1. **Intl.NumberFormat**: Định dạng số dựa trên ngôn ngữ và quy tắc địa phương.
2. **Intl.DateTimeFormat**: Định dạng ngày tháng theo ngôn ngữ và quy tắc địa phương.
3. **Intl.Collator**: So sánh và sắp xếp chuỗi dựa trên ngôn ngữ.
4. **Intl.PluralRules**: Xác định quy tắc số nhiều dựa trên ngôn ngữ.

### Chi tiết
- **Intl.NumberFormat**: Được sử dụng để định dạng số với các tùy chọn như kiểu định dạng (tiền tệ, phần trăm, v.v.).
- **Intl.DateTimeFormat**: Cho phép tùy chỉnh định dạng ngày tháng như ngày/tháng/năm hoặc tháng/ngày/năm.
- **Intl.Collator**: Hỗ trợ sắp xếp chuỗi theo thứ tự ngôn ngữ cụ thể, ví dụ như sắp xếp theo thứ tự chữ cái trong tiếng Việt.
- **Intl.PluralRules**: Hỗ trợ xác định cách sử dụng số nhiều trong các ngôn ngữ khác nhau.

## Ví dụ
### Ví dụ 1: Định dạng số
```javascript
const number = 1234567.89;
const formatter = new Intl.NumberFormat('vi-VN', { style: 'currency', currency: 'VND' });
console.log(formatter.format(number)); // "₫1.234.567,89"
```

### Ví dụ 2: Định dạng ngày tháng
```javascript
const date = new Date('2023-10-05');
const dateFormatter = new Intl.DateTimeFormat('vi-VN');
console.log(dateFormatter.format(date)); // "05/10/2023"
```

### Ví dụ 3: So sánh chuỗi
```javascript
const collator = new Intl.Collator('vi-VN');
const arr = ['c', 'b', 'a'];
arr.sort(collator.compare);
console.log(arr); // ["a", "b", "c"]
```

## Giải thích
- **Cạm bẫy thường gặp**: Một số lập trình viên có thể quên rằng các định dạng có thể thay đổi tùy thuộc vào ngôn ngữ và khu vực. Hãy đảm bảo sử dụng đúng mã ngôn ngữ khi gọi các API của Intl.
- **Lưu ý thêm**: Các trình duyệt có thể hỗ trợ khác nhau cho các tính năng của Intl, vì vậy hãy kiểm tra tính tương thích trước khi triển khai trong ứng dụng thực tế.

## Tóm tắt một dòng
Intl trong JavaScript là công cụ mạnh mẽ cho phép lập trình viên thực hiện các thao tác quốc tế hóa, giúp định dạng số, ngày tháng và chuỗi theo ngôn ngữ và quy tắc địa phương.