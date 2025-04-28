<!--
Meta Description: # Tìm Hiểu về "self" trong JavaScript: Khái Niệm, Cách Sử Dụng và Ví Dụ ## Tóm Tắt Trong JavaScript, "self" không phải là một từ khóa chính thức mà là...
Meta Keywords: self, trong, dụng, một, các
-->

# Tìm Hiểu về "self" trong JavaScript: Khái Niệm, Cách Sử Dụng và Ví Dụ

## Tóm Tắt
Trong JavaScript, "self" không phải là một từ khóa chính thức mà là một tham chiếu đến đối tượng toàn cục trong môi trường trình duyệt. Nó thường được sử dụng để truy cập các thuộc tính và phương thức của đối tượng Window trong ngữ cảnh toàn cục.

## Tài Liệu
### Mục Đích
"self" được sử dụng để tham chiếu đến đối tượng Window toàn cục, cho phép bạn truy cập các thuộc tính và phương thức mà không cần phải dùng từ khóa "window". Điều này có thể hữu ích trong các tình huống mà bạn muốn đảm bảo tính rõ ràng trong mã của mình.

### Cách Sử Dụng
- Trong môi trường trình duyệt, "self" tương đương với "window".
- Nó có thể được sử dụng trong các hàm hoặc callback để đảm bảo rằng bạn vẫn đang tham chiếu đến đối tượng Window, ngay cả khi ngữ cảnh thay đổi.

### Chi Tiết
- "self" có thể được sử dụng trong các tình huống như:
  - Khi bạn cần truy cập các thuộc tính như `self.location` để lấy URL của trang hiện tại.
  - Khi bạn cần gọi các phương thức như `self.alert()` để hiển thị hộp thoại cảnh báo.
  
Lưu ý rằng "self" không được sử dụng nhiều trong mã JavaScript hiện đại, nhưng nó vẫn có thể gặp trong một số mã kế thừa hoặc mã cũ.

## Ví Dụ
```javascript
// Sử dụng self để truy cập URL hiện tại
console.log(self.location.href);

// Sử dụng self để hiển thị một thông báo
self.alert("Đây là một thông báo!");
```

## Giải Thích
Mặc dù "self" có thể hữu ích, nhưng có một số điều cần lưu ý:
- Nên sử dụng "window" thay vì "self" trong mã hiện đại, vì "window" là từ khóa rõ ràng hơn và ít gây nhầm lẫn.
- Trong các tình huống như callback hoặc hàm nội bộ, bạn có thể dễ dàng bị mất ngữ cảnh của đối tượng (vì từ khóa "this" có thể không tham chiếu đến đối tượng bạn mong muốn), vì vậy việc sử dụng "self" để giữ tham chiếu đến đối tượng Window có thể hữu ích.

## Tóm Tắt Một Dòng
"self" trong JavaScript là một tham chiếu đến đối tượng Window, cho phép truy cập các thuộc tính và phương thức toàn cục một cách rõ ràng.