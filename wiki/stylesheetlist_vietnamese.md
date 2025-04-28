<!--
Meta Description: # Danh sách StyleSheet (StyleSheetList) trong JavaScript: Tìm Hiểu và Sử Dụng ## Tóm tắt Danh sách StyleSheet (StyleSheetList) là một đối tượng trong ...
Meta Keywords: stylesheet, các, một, stylesheets, sách
-->

# Danh sách StyleSheet (StyleSheetList) trong JavaScript: Tìm Hiểu và Sử Dụng

## Tóm tắt
Danh sách StyleSheet (StyleSheetList) là một đối tượng trong JavaScript cho phép truy cập và quản lý danh sách các stylesheet được áp dụng cho một tài liệu HTML. Nó cung cấp các phương thức và thuộc tính để tương tác với các stylesheet này.

## Tài liệu
### Mục đích
StyleSheetList được sử dụng để lấy danh sách các stylesheet hiện có trong một tài liệu HTML. Nó có thể giúp lập trình viên kiểm tra, thêm, hoặc thay đổi các stylesheet của trang web, từ đó điều chỉnh giao diện người dùng.

### Cách sử dụng
Để truy cập StyleSheetList, bạn có thể sử dụng thuộc tính `document.styleSheets`. Thuộc tính này trả về một đối tượng StyleSheetList, chứa tất cả các stylesheet liên quan đến tài liệu.

### Chi tiết
- **Thuộc tính**:
  - `length`: Trả về số lượng stylesheet trong danh sách.
  
- **Phương thức**:
  - `item(index)`: Trả về một đối tượng StyleSheet tại vị trí chỉ định trong danh sách.

### Cú pháp
```javascript
let styleSheets = document.styleSheets;
```

## Ví dụ
### Ví dụ 1: Lấy danh sách các stylesheet
```javascript
let styleSheets = document.styleSheets;
console.log("Số lượng stylesheet: " + styleSheets.length);
```

### Ví dụ 2: Truy cập một stylesheet cụ thể
```javascript
let firstStyleSheet = document.styleSheets.item(0);
console.log(firstStyleSheet.href); // In ra URL của stylesheet đầu tiên
```

### Ví dụ 3: Duyệt qua tất cả các stylesheet
```javascript
for (let i = 0; i < document.styleSheets.length; i++) {
    console.log("Stylesheet #" + i + ": " + document.styleSheets[i].href);
}
```

## Giải thích
- **Lưu ý về trình duyệt**: Một số trình duyệt có thể không cho phép truy cập vào các stylesheet từ các nguồn khác nhau do chính sách Same-Origin. Điều này có thể gây ra lỗi khi cố gắng truy cập các thuộc tính của một stylesheet từ miền khác.
- **Không có stylesheet**: Nếu không có stylesheet nào được thêm vào tài liệu, `document.styleSheets.length` sẽ trả về 0.
- **Thay đổi stylesheet**: Bạn có thể thay đổi các thuộc tính của một stylesheet đã tồn tại, nhưng không thể thêm hoặc xóa stylesheet trực tiếp từ đối tượng StyleSheetList.

## Tóm tắt một dòng
StyleSheetList trong JavaScript cho phép lập trình viên truy cập và quản lý danh sách các stylesheet trong tài liệu HTML, hỗ trợ việc điều chỉnh giao diện người dùng.