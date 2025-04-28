<!--
Meta Description: # DOMRectList trong JavaScript: Danh sách các hình chữ nhật trong DOM ## Tóm tắt DOMRectList là một đối tượng trong JavaScript dùng để lưu trữ một dan...
Meta Keywords: các, một, hình, chữ, nhật
-->

# DOMRectList trong JavaScript: Danh sách các hình chữ nhật trong DOM

## Tóm tắt
DOMRectList là một đối tượng trong JavaScript dùng để lưu trữ một danh sách các hình chữ nhật (DOMRect) mà thường được trả về từ các phương thức của DOM liên quan đến kích thước và vị trí của các phần tử trong trang web.

## Tài liệu
### Mục đích
DOMRectList cung cấp một cách để truy cập và thao tác với một tập hợp các đối tượng DOMRect, cho phép lập trình viên dễ dàng làm việc với nhiều hình chữ nhật trong không gian hai chiều của một trang web.

### Cách sử dụng
DOMRectList thường được sử dụng khi bạn gọi các phương thức như `getClientRects()` hoặc `getBoundingClientRect()`, mà trả về một danh sách các hình chữ nhật cho phần tử HTML. Mỗi đối tượng DOMRect trong danh sách này chứa thông tin về vị trí và kích thước của một phần tử trong cửa sổ trình duyệt.

### Chi tiết
- **Phương thức**: 
  - `getClientRects()`: Trả về một đối tượng DOMRectList đại diện cho tất cả các hình chữ nhật của phần tử.
  - `getBoundingClientRect()`: Trả về một đối tượng DOMRect duy nhất đại diện cho hình chữ nhật bao quanh phần tử.

- **Thuộc tính**: 
  - DOMRectList không có thuộc tính cụ thể nào; nó chỉ là một danh sách các đối tượng DOMRect.

## Ví dụ
```javascript
// Lấy phần tử từ DOM
const element = document.getElementById('myElement');

// Lấy danh sách các hình chữ nhật
const rects = element.getClientRects();

// Duyệt qua các hình chữ nhật và in ra thông tin
for (let rect of rects) {
    console.log(`X: ${rect.x}, Y: ${rect.y}, Width: ${rect.width}, Height: ${rect.height}`);
}
```

## Giải thích
- **Lỗi thường gặp**: Một số lập trình viên có thể nhầm lẫn giữa `getClientRects()` và `getBoundingClientRect()`. Trong khi `getClientRects()` trả về một danh sách nhiều hình chữ nhật, `getBoundingClientRect()` chỉ trả về một hình chữ nhật duy nhất cho phần tử.
- **Lưu ý bổ sung**: DOMRectList là một đối tượng giống như mảng, vì vậy bạn có thể sử dụng các phương thức mảng như `forEach`, `map`, v.v. để thao tác với các hình chữ nhật trong danh sách.

## Tóm tắt một dòng
DOMRectList là danh sách các hình chữ nhật được trả về từ các phương thức DOM, giúp lập trình viên dễ dàng quản lý vị trí và kích thước của các phần tử trên trang web.