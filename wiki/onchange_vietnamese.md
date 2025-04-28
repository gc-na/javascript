<!--
Meta Description: # Sự kiện onchange trong JavaScript: Hướng dẫn chi tiết và ví dụ ## Tóm tắt Sự kiện `onchange` trong JavaScript được sử dụng để phát hiện và xử lý sự ...
Meta Keywords: kiện, onchange, input, khi, dụng
-->

# Sự kiện onchange trong JavaScript: Hướng dẫn chi tiết và ví dụ

## Tóm tắt
Sự kiện `onchange` trong JavaScript được sử dụng để phát hiện và xử lý sự thay đổi giá trị của các phần tử form như `<input>`, `<select>`, và `<textarea>`. Đây là một sự kiện quan trọng trong lập trình web giúp cải thiện trải nghiệm người dùng.

## Tài liệu
### Mục đích
Sự kiện `onchange` được kích hoạt khi một phần tử form mất tiêu điểm và giá trị của nó đã thay đổi. Sự kiện này thường được sử dụng để thực hiện các hành động như xác thực dữ liệu, cập nhật giao diện người dùng hoặc thực hiện các yêu cầu AJAX.

### Cách sử dụng
Để sử dụng sự kiện `onchange`, bạn có thể thêm nó trực tiếp vào thẻ HTML hoặc thông qua JavaScript. Dưới đây là cú pháp cơ bản:

#### HTML
```html
<input type="text" onchange="myFunction()">
```

#### JavaScript
```javascript
const element = document.getElementById("myInput");
element.onchange = function() {
    myFunction();
};
```

### Chi tiết
- **Tham số**: Sự kiện `onchange` không có tham số đầu vào nào, nhưng nó có thể truy cập đối tượng sự kiện thông qua `this` trong hàm xử lý sự kiện.
- **Trình duyệt hỗ trợ**: Hầu hết các trình duyệt hiện đại đều hỗ trợ sự kiện này.
- **Lưu ý**: Đối với các phần tử `<select>`, sự kiện `onchange` sẽ được kích hoạt khi người dùng chọn một tùy chọn khác, trong khi đó đối với `<input>` và `<textarea>`, sự kiện chỉ được kích hoạt khi người dùng rời khỏi trường sau khi thay đổi giá trị.

## Ví dụ
### Ví dụ 1: Sử dụng onchange với input text
```html
<input type="text" id="myInput" onchange="alert('Giá trị đã thay đổi!')">
```

### Ví dụ 2: Sử dụng onchange với select
```html
<select id="mySelect" onchange="alert('Bạn đã chọn: ' + this.value)">
    <option value="1">Tùy chọn 1</option>
    <option value="2">Tùy chọn 2</option>
    <option value="3">Tùy chọn 3</option>
</select>
```

### Ví dụ 3: Sử dụng onchange với JavaScript
```html
<input type="text" id="myInput">
<script>
document.getElementById("myInput").onchange = function() {
    console.log("Giá trị input là: " + this.value);
};
</script>
```

## Giải thích
- **Nhầm lẫn với sự kiện input**: Sự kiện `onchange` khác với sự kiện `input`, sự kiện `input` được kích hoạt ngay khi người dùng nhập dữ liệu, trong khi `onchange` chỉ xảy ra khi trường mất tiêu điểm.
- **Hiệu suất**: Sử dụng `onchange` có thể giúp giảm thiểu số lần gọi hàm so với việc sử dụng sự kiện `input` trong một số tình huống, đặc biệt là khi xử lý các thao tác nặng nề.
- **Hỗ trợ trình duyệt**: Đảm bảo kiểm tra tính tương thích của sự kiện này trên các trình duyệt cũ nếu bạn đang phát triển cho một đối tượng người dùng rộng.

## Tóm tắt một dòng
Sự kiện `onchange` trong JavaScript cho phép phát hiện và xử lý sự thay đổi giá trị của các phần tử form khi chúng mất tiêu điểm.