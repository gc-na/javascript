<!--
Meta Description: # Attr trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ ## Tóm tắt Attr là một thuộc tính trong JavaScript cho phép người dùng truy cập và thao tác với c...
Meta Keywords: thuộc, tính, giá, trị, của
-->

# Attr trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ

## Tóm tắt
Attr là một thuộc tính trong JavaScript cho phép người dùng truy cập và thao tác với các thuộc tính của các phần tử DOM. Nó thường được sử dụng để lấy hoặc thiết lập giá trị của các thuộc tính HTML.

## Tài liệu
### Mục đích
Attr giúp lập trình viên tương tác hiệu quả với thuộc tính của các phần tử trong tài liệu HTML. Điều này rất hữu ích khi cần thay đổi giá trị của các thuộc tính như `src`, `href`, `class`, và nhiều thuộc tính khác.

### Cách sử dụng
Để sử dụng thuộc tính attr trong JavaScript, bạn có thể sử dụng phương thức `getAttribute()` để lấy giá trị của một thuộc tính và `setAttribute()` để thiết lập giá trị cho thuộc tính đó. Cú pháp cơ bản như sau:

- **Lấy thuộc tính:**
  ```javascript
  element.getAttribute('tên_thuộc_tính');
  ```

- **Thiết lập thuộc tính:**
  ```javascript
  element.setAttribute('tên_thuộc_tính', 'giá_trị');
  ```

### Chi tiết
- **getAttribute()**: Phương thức này trả về giá trị của thuộc tính xác định của một phần tử. Nếu thuộc tính không tồn tại, nó sẽ trả về `null`.
- **setAttribute()**: Phương thức này thiết lập giá trị cho thuộc tính xác định của một phần tử. Nếu thuộc tính không tồn tại, nó sẽ được tạo ra.

Lưu ý rằng thuộc tính được truy cập với tên chính xác như trong HTML (bao gồm cả chữ hoa và chữ thường).

## Ví dụ
### Ví dụ 1: Lấy giá trị thuộc tính
```javascript
const imgElement = document.querySelector('img');
const imgSrc = imgElement.getAttribute('src');
console.log(imgSrc); // In ra URL của hình ảnh
```

### Ví dụ 2: Thiết lập giá trị thuộc tính
```javascript
const linkElement = document.querySelector('a');
linkElement.setAttribute('href', 'https://www.example.com');
```

## Giải thích
Một số vấn đề thường gặp khi sử dụng attr là:
- **Không tìm thấy thuộc tính**: Nếu bạn cố gắng lấy một thuộc tính không tồn tại, `getAttribute()` sẽ trả về `null`.
- **Cảm nhận về chữ hoa và chữ thường**: Hãy chắc chắn rằng bạn sử dụng tên thuộc tính chính xác vì JavaScript phân biệt chữ hoa và chữ thường.
- **Sự khác biệt giữa thuộc tính và phương thức**: Đôi khi, các phương thức như `element.value` có thể có sự khác biệt với giá trị lấy từ `getAttribute()`. Ví dụ, trong các phần tử form, `value` sẽ trả về giá trị nhập vào của người dùng, trong khi `getAttribute('value')` sẽ trả về giá trị mặc định.

## Tóm tắt một dòng
Attr trong JavaScript cho phép bạn lấy và thiết lập giá trị thuộc tính của các phần tử DOM một cách dễ dàng.