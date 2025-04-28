<!--
Meta Description: # Sự kiện bàn phím (KeyboardEvent) trong JavaScript ## Tóm tắt Sự kiện bàn phím (KeyboardEvent) trong JavaScript được sử dụng để xử lý các tương tác c...
Meta Keywords: phím, các, kiện, bàn, được
-->

# Sự kiện bàn phím (KeyboardEvent) trong JavaScript

## Tóm tắt
Sự kiện bàn phím (KeyboardEvent) trong JavaScript được sử dụng để xử lý các tương tác của người dùng với bàn phím, cho phép lập trình viên theo dõi và phản hồi các hành động như nhấn, giữ và thả phím.

## Tài liệu
### Mục đích
Sự kiện bàn phím cho phép bạn nhận diện các hành động của người dùng liên quan đến bàn phím, từ đó bạn có thể thực hiện các hành động tương ứng trong ứng dụng web của mình.

### Cách sử dụng
`KeyboardEvent` là một đối tượng sự kiện được tạo ra khi người dùng tương tác với bàn phím. Bạn có thể lắng nghe các sự kiện này bằng cách sử dụng các phương thức như `addEventListener` trên các phần tử DOM. 

```javascript
document.addEventListener('keydown', function(event) {
    console.log('Key pressed: ', event.key);
});
```

### Thông tin chi tiết
- **Các thuộc tính chính**:
  - `key`: chứa giá trị của phím đã được nhấn (ví dụ: 'Enter', 'a', 'ArrowUp').
  - `code`: chứa mã vật lý của phím (ví dụ: 'KeyA', 'ArrowUp').
  - `altKey`, `ctrlKey`, `shiftKey`, `metaKey`: các thuộc tính boolean cho biết các phím modifier (Alt, Ctrl, Shift, Meta) có đang được nhấn hay không.
  
- **Các loại sự kiện**:
  - `keydown`: xảy ra khi một phím được nhấn xuống.
  - `keyup`: xảy ra khi một phím được thả ra.
  - `keypress`: xảy ra khi một phím được nhấn, nhưng đã bị loại bỏ trong các phiên bản mới của JavaScript.

## Ví dụ
### Ví dụ 1: Lắng nghe sự kiện nhấn phím
```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        console.log('Enter key was pressed!');
    }
});
```

### Ví dụ 2: Kiểm tra phím modifier
```javascript
document.addEventListener('keydown', function(event) {
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault(); // Ngăn chặn hành động mặc định
        console.log('Ctrl + S was pressed!');
    }
});
```

## Giải thích
Khi làm việc với sự kiện bàn phím, có một số điều cần lưu ý:
- **Sự kiện `keypress`**: Không còn được khuyến nghị sử dụng trong các phiên bản mới của JavaScript. Nên dùng `keydown` hoặc `keyup`.
- **Ngăn chặn hành động mặc định**: Để ngăn chặn các hành động mặc định (như lưu trang khi nhấn Ctrl + S), bạn cần sử dụng `event.preventDefault()`.
- **Khả năng tương thích**: Một số thuộc tính hoặc phương thức có thể không được hỗ trợ đầy đủ trên tất cả các trình duyệt, vì vậy hãy kiểm tra khả năng tương thích trước khi triển khai.

## Tóm tắt một câu
Sự kiện bàn phím trong JavaScript cho phép theo dõi và xử lý các tương tác của người dùng với bàn phím để cải thiện trải nghiệm người dùng trên ứng dụng web.