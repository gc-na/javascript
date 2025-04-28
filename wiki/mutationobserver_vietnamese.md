<!--
Meta Description: # MutationObserver trong JavaScript: Theo dõi sự thay đổi DOM ## Tóm tắt MutationObserver là một API trong JavaScript cho phép theo dõi và phản ứng vớ...
Meta Keywords: theo, dõi, đổi, các, thay
-->

# MutationObserver trong JavaScript: Theo dõi sự thay đổi DOM

## Tóm tắt
MutationObserver là một API trong JavaScript cho phép theo dõi và phản ứng với những thay đổi trong cấu trúc DOM. Nó cung cấp một cách hiệu quả hơn để theo dõi các biến đổi so với việc sử dụng các sự kiện như `DOMSubtreeModified`.

## Tài liệu
### Mục đích
MutationObserver được sử dụng để phát hiện các thay đổi trong DOM, bao gồm thêm, xóa, hoặc thay đổi thuộc tính của các phần tử. Điều này rất hữu ích trong các trường hợp cần cập nhật giao diện người dùng hoặc xử lý dữ liệu khi có sự thay đổi trong cấu trúc của trang.

### Cách sử dụng
Để sử dụng MutationObserver, bạn cần thực hiện các bước sau:

1. **Tạo một đối tượng MutationObserver**: Bạn tạo một đối tượng mới bằng cách truyền vào một callback function, hàm này sẽ được gọi khi có sự thay đổi xảy ra.
2. **Chỉ định các tùy chọn theo dõi**: Bạn cần xác định những thay đổi nào mà bạn muốn theo dõi thông qua một đối tượng tùy chọn.
3. **Bắt đầu theo dõi**: Sử dụng phương thức `observe()` để bắt đầu theo dõi một phần tử DOM cụ thể.
4. **Ngừng theo dõi**: Khi không còn cần theo dõi nữa, bạn có thể gọi `disconnect()` để ngừng theo dõi.

### Cú pháp
```javascript
const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
observer.disconnect();
```

- **callback**: Hàm sẽ được gọi khi có sự thay đổi.
- **targetNode**: Phần tử DOM mà bạn muốn theo dõi.
- **config**: Đối tượng chứa các tùy chọn theo dõi, ví dụ như `childList`, `attributes`, `subtree`, v.v.

## Ví dụ
### Ví dụ 1: Theo dõi sự thay đổi thuộc tính
```javascript
const targetNode = document.getElementById('myElement');
const config = { attributes: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'attributes') {
            console.log('Attribute changed:', mutation.attributeName);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// Thay đổi thuộc tính để kiểm tra
targetNode.setAttribute('data-test', 'newValue');
```

### Ví dụ 2: Theo dõi các phần tử con được thêm hoặc xóa
```javascript
const targetNode = document.getElementById('myList');
const config = { childList: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('A child node has been added or removed.');
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// Thêm phần tử mới vào danh sách
const newItem = document.createElement('li');
newItem.textContent = 'New Item';
targetNode.appendChild(newItem);
```

## Giải thích
- **Hiệu suất**: MutationObserver tối ưu hơn so với các sự kiện DOM truyền thống bởi nó không gây ra nhiều overhead khi theo dõi. Nó chỉ phản hồi khi có sự thay đổi thực sự xảy ra.
- **Ngừng theo dõi**: Đảm bảo gọi `disconnect()` khi không còn cần theo dõi để giải phóng tài nguyên và tránh rò rỉ bộ nhớ.
- **Không theo dõi các sự kiện**: MutationObserver không theo dõi các sự kiện như `click` hay `input`. Nó chỉ theo dõi các thay đổi trong DOM.

## Tóm tắt một dòng
MutationObserver là một API trong JavaScript cho phép theo dõi và phản ứng với các thay đổi trong cấu trúc DOM một cách hiệu quả.