<!--
Meta Description: # RadioNodeList trong JavaScript: Hướng dẫn chi tiết ## Tóm tắt RadioNodeList là một đối tượng trong JavaScript đại diện cho danh sách các nút radio (...
Meta Keywords: radio, một, nút, radionodelist, các
-->

# RadioNodeList trong JavaScript: Hướng dẫn chi tiết

## Tóm tắt
RadioNodeList là một đối tượng trong JavaScript đại diện cho danh sách các nút radio (radio buttons) trong một nhóm. Đối tượng này cho phép lập trình viên truy cập và thao tác với các nút radio một cách dễ dàng.

## Tài liệu
### Mục đích
RadioNodeList được tạo ra để giúp lập trình viên xử lý nhóm các nút radio trong HTML. Nó cho phép bạn lấy tất cả các nút radio từ một nhóm cụ thể, từ đó có thể thực hiện các thao tác như kiểm tra trạng thái (checked) của các nút radio.

### Sử dụng
Để tạo một RadioNodeList, bạn có thể sử dụng phương thức `document.getElementsByName()` hoặc truy cập trực tiếp thông qua thuộc tính `form.elements` của một form. Kết quả trả về là một đối tượng RadioNodeList.

### Chi tiết
- **Cú pháp:**
  ```javascript
  const radioButtons = document.getElementsByName('tên-nút-radio');
  ```

- **Thuộc tính:**
  - `length`: Trả về số lượng nút radio trong danh sách.
  
- **Phương thức:**
  - `item(index)`: Trả về nút radio tại chỉ số xác định trong danh sách.

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng RadioNodeList:

```html
<form id="myForm">
  <input type="radio" name="fruit" value="apple"> Táo<br>
  <input type="radio" name="fruit" value="banana"> Chuối<br>
  <input type="radio" name="fruit" value="orange"> Cam<br>
</form>

<script>
  const radios = document.getElementsByName('fruit');
  
  for (let i = 0; i < radios.length; i++) {
    if (radios[i].checked) {
      console.log(`Nút radio đã chọn: ${radios[i].value}`);
    }
  }
</script>
```

## Giải thích
### Những điều cần lưu ý
- RadioNodeList không phải là một mảng thông thường, mặc dù nó có thuộc tính `length` và có thể được lặp qua. Bạn không thể sử dụng các phương thức mảng như `map` hay `filter` trực tiếp trên RadioNodeList.
- Nếu không có nút radio nào được chọn, bạn cần phải kiểm tra kỹ lưỡng để tránh lỗi khi cố gắng truy cập giá trị của các nút.

### Ghi chú bổ sung
- Để thao tác dễ dàng hơn, bạn có thể chuyển đổi RadioNodeList thành một mảng bằng cách sử dụng `Array.from()` hoặc toán tử spread `...`.

```javascript
const radiosArray = Array.from(radios);
```

## Tóm tắt một dòng
RadioNodeList trong JavaScript cho phép lập trình viên truy cập và thao tác với nhóm các nút radio trong một form một cách hiệu quả.