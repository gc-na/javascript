<!--
Meta Description: # FinalizationRegistry trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể ## Tóm tắt `FinalizationRegistry` là một API trong JavaScript cho phép the...
Meta Keywords: đối, tượng, được, không, obj
-->

# FinalizationRegistry trong JavaScript: Hướng Dẫn Chi Tiết và Ví Dụ Cụ Thể

## Tóm tắt
`FinalizationRegistry` là một API trong JavaScript cho phép theo dõi và phản hồi khi các đối tượng không còn được tham chiếu, giúp quản lý bộ nhớ hiệu quả hơn.

## Tài liệu

### Mục đích
`FinalizationRegistry` được sử dụng để đăng ký một hàm callback sẽ được gọi khi một đối tượng không còn được tham chiếu nữa. Điều này hữu ích trong việc thực hiện các tác vụ dọn dẹp tài nguyên hoặc thông báo khi một đối tượng không còn tồn tại.

### Cách sử dụng
Để sử dụng `FinalizationRegistry`, bạn cần tạo một thể hiện của nó và đăng ký các đối tượng mà bạn muốn theo dõi cùng với một hàm callback. Dưới đây là cú pháp cơ bản:

```javascript
const registry = new FinalizationRegistry((heldValue) => {
    // Callback xử lý khi đối tượng bị thu hồi
});

// Đăng ký đối tượng
const obj = {};
registry.register(obj, 'Giá trị đã giữ');

// Hủy tham chiếu đến đối tượng
obj = null; // Đối tượng sẽ được thu hồi khi không còn tham chiếu
```

### Chi tiết
- **Constructor**: `new FinalizationRegistry(callback)`
  - `callback`: Hàm sẽ được gọi khi đối tượng được thu hồi. Hàm này nhận một tham số - giá trị mà bạn đã đăng ký cùng với đối tượng.
  
- **Phương thức**: `.register(value, heldValue)`
  - `value`: Đối tượng mà bạn muốn theo dõi.
  - `heldValue`: Giá trị mà bạn muốn truyền đến callback khi đối tượng bị thu hồi.

- **Phương thức**: `.unregister(value)`
  - Hủy đăng ký đối tượng đã được đăng ký trước đó.

### Lưu ý
- `FinalizationRegistry` không đảm bảo khi nào callback sẽ được gọi. Việc gọi này phụ thuộc vào bộ thu gom rác (garbage collector).
- Đảm bảo rằng các đối tượng được đăng ký không bị giữ tham chiếu khác, nếu không chúng sẽ không bao giờ bị thu hồi.

## Ví dụ

### Ví dụ cơ bản
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`Đối tượng đã được thu hồi, giá trị: ${heldValue}`);
});

let obj = { name: 'JavaScript' };
registry.register(obj, 'Giá trị của obj');

// Hủy tham chiếu đến obj
obj = null;

// Sau một thời gian, khi garbage collector chạy, bạn sẽ thấy thông báo trong console.
```

### Ví dụ với hủy đăng ký
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`Đối tượng đã được thu hồi, giá trị: ${heldValue}`);
});

let obj = { name: 'JavaScript' };
const heldValue = 'Giá trị của obj';
registry.register(obj, heldValue);

// Hủy đăng ký
registry.unregister(obj);

// Hủy tham chiếu
obj = null;

// Không có thông báo nào xuất hiện do đối tượng đã bị hủy đăng ký.
```

## Giải thích
- Một trong những cạm bẫy phổ biến khi sử dụng `FinalizationRegistry` là kỳ vọng rằng callback sẽ được gọi ngay lập tức khi đối tượng không còn tồn tại. Tuy nhiên, việc này phụ thuộc vào garbage collector và có thể không xảy ra ngay lập tức.
- Ngoài ra, cần lưu ý rằng callback sẽ được gọi trong một ngữ cảnh không đồng bộ, điều này có thể gây ra các vấn đề về đồng bộ hóa nếu không được xử lý đúng cách.

## Tóm tắt một dòng
`FinalizationRegistry` trong JavaScript cho phép theo dõi và xử lý các đối tượng khi chúng không còn được tham chiếu, giúp quản lý bộ nhớ hiệu quả hơn.