<!--
Meta Description: # MutationRecord trong JavaScript: Đặc điểm và Cách Sử Dụng ## Tóm tắt `MutationRecord` là một đối tượng trong JavaScript, thuộc DOM (Document Object ...
Meta Keywords: thay, đổi, nút, dụng, một
-->

# MutationRecord trong JavaScript: Đặc điểm và Cách Sử Dụng

## Tóm tắt
`MutationRecord` là một đối tượng trong JavaScript, thuộc DOM (Document Object Model), được sử dụng để mô tả sự thay đổi xảy ra trong cây DOM. Nó là một phần quan trọng của API MutationObserver, cho phép theo dõi và phản ứng với các thay đổi trong cấu trúc của tài liệu.

## Tài liệu
### Mục đích
`MutationRecord` được sử dụng để lưu trữ thông tin về các thay đổi diễn ra trong DOM. Nó cung cấp chi tiết về loại thay đổi, các nút bị ảnh hưởng, và các thuộc tính liên quan đến sự thay đổi đó.

### Cách sử dụng
Một `MutationRecord` thường được tạo tự động khi một `MutationObserver` theo dõi sự thay đổi trong DOM. Để bắt đầu sử dụng, bạn cần tạo một `MutationObserver`, và sau đó định nghĩa một callback function để xử lý các bản ghi thay đổi.

### Các thuộc tính của MutationRecord
- `type`: Loại thay đổi, có thể là "childList", "attributes", hoặc "characterData".
- `target`: Đối tượng DOM mà thay đổi đã xảy ra.
- `addedNodes`: Danh sách các nút mới được thêm vào (chỉ áp dụng khi `type` là "childList").
- `removedNodes`: Danh sách các nút đã bị xóa (chỉ áp dụng khi `type` là "childList").
- `previousSibling`: Nút trước đó của nút bị thay đổi (chỉ áp dụng khi `type` là "childList").
- `nextSibling`: Nút tiếp theo của nút bị thay đổi (chỉ áp dụng khi `type` là "childList").
- `attributeName`: Tên thuộc tính đã thay đổi (chỉ áp dụng khi `type` là "attributes").
- `oldValue`: Giá trị trước đó của thuộc tính (chỉ áp dụng khi `type` là "attributes" hoặc "characterData").

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng `MutationRecord` trong JavaScript:

```javascript
// Tạo một MutationObserver
const observer = new MutationObserver((mutationsList) => {
    for (const mutation of mutationsList) {
        console.log('Loại thay đổi:', mutation.type);
        if (mutation.type === 'childList') {
            console.log('Nút đã thêm:', mutation.addedNodes);
            console.log('Nút đã xóa:', mutation.removedNodes);
        }
    }
});

// Thiết lập theo dõi cho các thay đổi trong DOM
const targetNode = document.getElementById('myElement');
const config = { childList: true, attributes: true };

observer.observe(targetNode, config);

// Thêm một nút mới vào targetNode
const newNode = document.createElement('div');
newNode.textContent = 'Nút mới';
targetNode.appendChild(newNode);

// Thay đổi thuộc tính của targetNode
targetNode.setAttribute('data-attribute', 'giá trị mới');
```

## Giải thích
Khi làm việc với `MutationRecord`, có một số điều bạn cần lưu ý:
- `MutationRecord` không được tạo ra trực tiếp bởi người dùng; nó được tạo ra bởi `MutationObserver`.
- Phải cẩn thận khi xử lý các nút trong danh sách `addedNodes` và `removedNodes`, vì chúng có thể chứa nhiều nút.
- Việc thực hiện quá nhiều thay đổi đồng thời có thể dẫn đến việc ghi lại nhiều bản ghi, do đó cần phải tối ưu hóa callback để tránh bị lag.

## Tóm tắt một dòng
`MutationRecord` là một đối tượng trong JavaScript giúp theo dõi và mô tả các thay đổi trong DOM thông qua API MutationObserver.