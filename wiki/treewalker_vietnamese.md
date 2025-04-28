<!--
Meta Description: # TreeWalker trong JavaScript: Khám Phá Cách Duyệt Cây DOM ## Tóm Tắt TreeWalker là một giao diện trong JavaScript cho phép lập trình viên duyệt qua c...
Meta Keywords: nút, treewalker, các, bạn, một
-->

# TreeWalker trong JavaScript: Khám Phá Cách Duyệt Cây DOM

## Tóm Tắt
TreeWalker là một giao diện trong JavaScript cho phép lập trình viên duyệt qua các nút trong cây DOM một cách linh hoạt và hiệu quả. Với TreeWalker, bạn có thể dễ dàng di chuyển giữa các phần tử của tài liệu HTML mà không cần phải lặp lại các hàm phức tạp.

## Tài Liệu
### Mục Đích
TreeWalker được thiết kế để hỗ trợ việc duyệt cây DOM, cho phép truy cập và thao tác với các nút con, nút cha và các loại nút khác nhau như phần tử, văn bản và chú thích.

### Cách Sử Dụng
Để tạo một TreeWalker, bạn cần sử dụng phương thức `document.createTreeWalker()`. Phương thức này yêu cầu ba tham số chính:

1. **root**: Nút gốc của cây DOM mà bạn muốn bắt đầu duyệt.
2. **whatToShow**: Các loại nút mà TreeWalker sẽ hiển thị. Bạn có thể sử dụng hằng số như `NodeFilter.SHOW_ELEMENT` để chỉ định chỉ hiển thị các phần tử.
3. **filter**: (Tùy chọn) Một hàm lọc cho phép bạn kiểm soát các nút nào sẽ được bao gồm trong TreeWalker.

### Cú Pháp
```javascript
const treeWalker = document.createTreeWalker(
    root,
    whatToShow,
    filter,
    entityReferenceExpansion
);
```

### Các Thuộc Tính và Phương Thức Chính
- **currentNode**: Thuộc tính này cho phép bạn lấy hoặc thiết lập nút hiện tại mà TreeWalker đang tham chiếu tới.
- **nextNode()**: Phương thức này di chuyển đến nút tiếp theo trong cây DOM.
- **previousNode()**: Di chuyển đến nút trước đó.
- **parentNode()**: Lấy nút cha của nút hiện tại.
- **firstChild()**: Lấy nút con đầu tiên của nút hiện tại.
- **lastChild()**: Lấy nút con cuối cùng của nút hiện tại.

## Ví Dụ
### Ví Dụ Cơ Bản
Dưới đây là một ví dụ đơn giản để sử dụng TreeWalker để duyệt qua tất cả các phần tử trong một danh sách:

```javascript
const list = document.getElementById('myList');
const treeWalker = document.createTreeWalker(
    list,
    NodeFilter.SHOW_ELEMENT,
    null,
    false
);

let currentNode;
while (currentNode = treeWalker.nextNode()) {
    console.log(currentNode.tagName); // In ra tên thẻ của phần tử
}
```

## Giải Thích
### Những Điều Cần Lưu Ý
- **Hiệu suất**: Sử dụng TreeWalker có thể cải thiện hiệu suất khi bạn cần duyệt qua một cây DOM lớn, vì nó cho phép bạn truy cập trực tiếp vào các nút mà không cần phải lặp lại qua tất cả các nút.
- **Khả năng tương thích**: Đảm bảo rằng các trình duyệt mà bạn đang hỗ trợ có tính năng này, mặc dù TreeWalker hiện đã được hỗ trợ rộng rãi.
- **Cách thức hoạt động của filter**: Nếu bạn sử dụng filter, hãy chắc chắn rằng hàm của bạn trả về đúng giá trị (NodeFilter.FILTER_ACCEPT, NodeFilter.FILTER_REJECT, hoặc NodeFilter.FILTER_SKIP) để có được kết quả mong muốn.

## Tóm Tắt Một Dòng
TreeWalker trong JavaScript là một công cụ mạnh mẽ giúp duyệt cây DOM một cách hiệu quả và linh hoạt.