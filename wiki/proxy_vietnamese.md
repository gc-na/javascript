<!--
Meta Description: # Proxy trong JavaScript: Tạo và Quản lý Đối Tượng Động ## Tóm Tắt Proxy trong JavaScript là một tính năng cho phép bạn tạo ra một đối tượng "proxy" đ...
Meta Keywords: proxy, đối, tượng, các, một
-->

# Proxy trong JavaScript: Tạo và Quản lý Đối Tượng Động

## Tóm Tắt
Proxy trong JavaScript là một tính năng cho phép bạn tạo ra một đối tượng "proxy" để theo dõi và kiểm soát các hoạt động trên các đối tượng khác, như truy cập thuộc tính, gọi hàm, hoặc thay đổi giá trị.

## Tài Liệu
### Mục Đích
Proxy được sử dụng để tạo ra một lớp bao bọc cho một đối tượng, cho phép bạn can thiệp vào các hoạt động của đối tượng đó, chẳng hạn như đọc, ghi hoặc xóa thuộc tính.

### Cách Sử Dụng
Khởi tạo một Proxy bao gồm hai tham số chính:
1. **Đối tượng mục tiêu (target)**: Đối tượng mà bạn muốn theo dõi.
2. **Handler**: Một đối tượng chứa các phương thức (trap) để can thiệp vào các hoạt động trên đối tượng mục tiêu.

Cú pháp:
```javascript
const proxy = new Proxy(target, handler);
```

### Chi Tiết
- **Target**: Đối tượng gốc mà bạn muốn tạo proxy.
- **Handler**: Đối tượng chứa các phương thức "trap" như `get`, `set`, `deleteProperty`, và nhiều hơn nữa. Những phương thức này cho phép bạn can thiệp vào các hành động trên đối tượng.

## Ví Dụ
### Ví dụ Cơ Bản
```javascript
const target = {
    message: "Hello, world!"
};

const handler = {
    get: function(obj, prop) {
        return prop in obj ? obj[prop] : "Property does not exist";
    }
};

const proxy = new Proxy(target, handler);

console.log(proxy.message); // "Hello, world!"
console.log(proxy.nonExistent); // "Property does not exist"
```

### Ví dụ Với Set
```javascript
const target = {};

const handler = {
    set: function(obj, prop, value) {
        console.log(`Setting value '${value}' to '${prop}'`);
        obj[prop] = value;
        return true; // Phải trả về true để xác nhận việc thiết lập
    }
};

const proxy = new Proxy(target, handler);

proxy.a = 10; // "Setting value '10' to 'a'"
console.log(target.a); // 10
```

## Giải Thích
- **Lỗi Thường Gặp**: Một số lập trình viên có thể quên trả về `true` trong các phương thức `set`, dẫn đến việc không thể thiết lập giá trị cho thuộc tính.
- **Khó Khăn Khi Debug**: Việc sử dụng Proxy có thể làm cho mã trở nên khó hiểu hơn do việc can thiệp vào các thao tác cơ bản, khiến cho việc debug trở nên khó khăn.
- **Hỗ Trợ Trình Duyệt**: Proxy không được hỗ trợ trong Internet Explorer, nên cần kiểm tra tính tương thích trước khi sử dụng.

## Tóm Tắt Một Dòng
Proxy trong JavaScript cho phép bạn theo dõi và quản lý các hoạt động trên đối tượng, tạo ra một lớp bao bọc hữu ích cho việc kiểm soát hành vi của đối tượng.