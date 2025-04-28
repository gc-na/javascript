<!--
Meta Description: # Đối Tượng Trong JavaScript: Tính Năng Cơ Bản và Cách Sử Dụng ## Tóm tắt Đối tượng trong JavaScript là một kiểu dữ liệu phức tạp cho phép lưu trữ các...
Meta Keywords: đối, tượng, dụng, javascript, name
-->

# Đối Tượng Trong JavaScript: Tính Năng Cơ Bản và Cách Sử Dụng

## Tóm tắt
Đối tượng trong JavaScript là một kiểu dữ liệu phức tạp cho phép lưu trữ các giá trị dưới dạng cặp khóa-giá trị, hỗ trợ tổ chức và quản lý dữ liệu một cách hiệu quả.

## Tài liệu
### Mục đích
Đối tượng là một trong những kiểu dữ liệu cơ bản và quan trọng nhất trong JavaScript. Chúng cho phép lập trình viên lưu trữ thông tin dưới dạng các thuộc tính và phương thức, giúp tổ chức mã nguồn một cách rõ ràng và dễ dàng hơn.

### Cách sử dụng
Đối tượng có thể được tạo ra bằng nhiều cách khác nhau, bao gồm:
- Sử dụng cú pháp đối tượng (Object Literal)
- Sử dụng hàm tạo (Constructor Function)
- Sử dụng lớp (Class)

### Chi tiết
1. **Cú pháp đối tượng (Object Literal)**
   ```javascript
   const person = {
       name: "Nguyễn Văn A",
       age: 30,
       greet: function() {
           console.log("Xin chào, tôi là " + this.name);
       }
   };
   ```

2. **Hàm tạo (Constructor Function)**
   ```javascript
   function Person(name, age) {
       this.name = name;
       this.age = age;
       this.greet = function() {
           console.log("Xin chào, tôi là " + this.name);
       };
   }

   const person1 = new Person("Nguyễn Văn B", 25);
   ```

3. **Lớp (Class)**
   ```javascript
   class Person {
       constructor(name, age) {
           this.name = name;
           this.age = age;
       }

       greet() {
           console.log("Xin chào, tôi là " + this.name);
       }
   }

   const person2 = new Person("Nguyễn Văn C", 28);
   ```

## Ví dụ
### Ví dụ 1: Tạo và sử dụng đối tượng
```javascript
const car = {
    brand: "Toyota",
    model: "Camry",
    year: 2020,
    displayInfo: function() {
        console.log(`${this.brand} ${this.model} (${this.year})`);
    }
};

car.displayInfo(); // Outputs: Toyota Camry (2020)
```

### Ví dụ 2: Thêm thuộc tính vào đối tượng
```javascript
car.color = "Đỏ";
console.log(car.color); // Outputs: Đỏ
```

## Giải thích
- **Cách truy cập và cập nhật thuộc tính:** Bạn có thể truy cập và cập nhật thuộc tính của đối tượng bằng cách sử dụng ký hiệu chấm (.) hoặc ký hiệu dấu ngoặc vuông ([]).
  ```javascript
  console.log(car.brand); // Outputs: Toyota
  car.model = "Corolla";   // Cập nhật thuộc tính model
  ```

- **Những lỗi thường gặp:** Một số lập trình viên có thể nhầm lẫn giữa đối tượng và mảng. Đối tượng sử dụng cặp khóa-giá trị, trong khi mảng sử dụng chỉ số. Ngoài ra, việc sử dụng `this` trong các phương thức có thể gây nhầm lẫn nếu không được sử dụng đúng cách.

## Tóm tắt một dòng
Đối tượng trong JavaScript là một kiểu dữ liệu cho phép lưu trữ và quản lý thông tin dưới dạng cặp khóa-giá trị, rất hữu ích trong lập trình.