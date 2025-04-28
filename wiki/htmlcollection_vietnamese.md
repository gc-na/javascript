<!--
Meta Description: # HTMLCollection trong JavaScript: Hướng dẫn đầy đủ và chi tiết ## Tóm tắt HTMLCollection là một tập hợp các phần tử HTML được trả về bởi các phương t...
Meta Keywords: htmlcollection, phần, các, trong, một
-->

# HTMLCollection trong JavaScript: Hướng dẫn đầy đủ và chi tiết

## Tóm tắt
HTMLCollection là một tập hợp các phần tử HTML được trả về bởi các phương thức DOM trong JavaScript. Nó cho phép truy cập và thao tác các phần tử HTML trong tài liệu.

## Tài liệu
HTMLCollection là một đối tượng trong JavaScript, được sử dụng để lưu trữ danh sách các phần tử HTML. Đối tượng này được tạo ra khi bạn sử dụng các phương thức như `document.getElementsByTagName()`, `document.getElementsByClassName()`, hoặc `document.forms`. HTMLCollection tương tự như một mảng, nhưng không hoàn toàn giống như một mảng JavaScript thông thường.

### Mục đích
HTMLCollection được sử dụng để dễ dàng truy cập và thao tác các phần tử DOM trong tài liệu HTML mà không cần phải làm việc với từng phần tử một cách riêng lẻ.

### Cách sử dụng
HTMLCollection có thể được truy cập qua chỉ mục như một mảng, nhưng nó không có tất cả các phương thức của mảng. Do đó, bạn có thể sử dụng vòng lặp `for` để lặp qua các phần tử trong HTMLCollection.

### Chi tiết
- **Trả về**: HTMLCollection được trả về từ các phương thức như:
  - `document.getElementsByTagName(tagName)`
  - `document.getElementsByClassName(className)`
  - `document.forms`
- **Đặc điểm**:
  - HTMLCollection là "live" (trực tiếp), nghĩa là nếu tài liệu DOM thay đổi (thêm hoặc xóa phần tử), HTMLCollection sẽ tự động cập nhật.
  - Các thuộc tính và phương thức của HTMLCollection bao gồm:
    - `.length`: Số lượng phần tử trong tập hợp.
    - `[index]`: Truy cập phần tử theo chỉ số.

## Ví dụ
### Ví dụ 1: Sử dụng `getElementsByTagName`
```javascript
const elements = document.getElementsByTagName('div');
console.log(elements.length); // In ra số lượng phần tử <div>
console.log(elements[0]); // In ra phần tử <div> đầu tiên
```

### Ví dụ 2: Sử dụng `getElementsByClassName`
```javascript
const items = document.getElementsByClassName('item');
for (let i = 0; i < items.length; i++) {
    console.log(items[i]); // In ra từng phần tử có class 'item'
}
```

### Ví dụ 3: Sử dụng `document.forms`
```javascript
const forms = document.forms;
console.log(forms.length); // In ra số lượng form trong tài liệu
```

## Giải thích
Một số điểm cần lưu ý khi làm việc với HTMLCollection:
- **Không phải mảng**: Dù HTMLCollection có thể được truy cập thông qua chỉ số, nhưng nó không hỗ trợ các phương thức mảng như `.push()`, `.pop()` hay `.forEach()`.
- **Cập nhật tự động**: Nếu bạn thay đổi DOM (thêm hoặc xóa phần tử), HTMLCollection cũng sẽ phản ánh sự thay đổi đó ngay lập tức.
- **Tránh lỗi thao tác**: Khi lặp qua HTMLCollection, bạn nên sử dụng vòng lặp `for` với chỉ số `length` để tránh lỗi khi có sự thay đổi trong DOM trong quá trình lặp.

## Tóm tắt một dòng
HTMLCollection là một tập hợp các phần tử HTML trong JavaScript, cho phép truy cập và thao tác các phần tử DOM một cách dễ dàng và linh hoạt.