<!--
Meta Description: # Tạo phần tử tùy chỉnh trong JavaScript với customElements ## Tóm tắt `customElements` là một API trong JavaScript cho phép lập trình viên tạo ra các...
Meta Keywords: phần, tùy, chỉnh, các, customelements
-->

# Tạo phần tử tùy chỉnh trong JavaScript với customElements

## Tóm tắt
`customElements` là một API trong JavaScript cho phép lập trình viên tạo ra các phần tử HTML tùy chỉnh, giúp mở rộng khả năng của DOM và cải thiện khả năng tái sử dụng của mã.

## Tài liệu
`customElements` là một phần của Web Components, cho phép bạn định nghĩa các phần tử HTML mới với hành vi và thuộc tính riêng. API này giúp bạn tạo ra các phần tử có thể tái sử dụng, dễ dàng quản lý và tích hợp vào các ứng dụng web.

### Mục đích
- Tạo các phần tử HTML tùy chỉnh.
- Cải thiện khả năng tái sử dụng mã.
- Tích hợp các phần tử tùy chỉnh vào DOM như các phần tử HTML tiêu chuẩn.

### Cách sử dụng
Để sử dụng `customElements`, bạn cần định nghĩa một lớp kế thừa từ `HTMLElement` và sau đó đăng ký lớp này với một tên phần tử tùy chỉnh thông qua `customElements.define()`.

### Cú pháp
```javascript
class MyElement extends HTMLElement {
    constructor() {
        super();
        // Khởi tạo các thuộc tính và phương thức
    }

    connectedCallback() {
        // Code chạy khi phần tử được thêm vào DOM
    }

    disconnectedCallback() {
        // Code chạy khi phần tử bị xóa khỏi DOM
    }
}

// Đăng ký phần tử tùy chỉnh
customElements.define('my-element', MyElement);
```

## Ví dụ
### Ví dụ cơ bản về phần tử tùy chỉnh
```javascript
class GreetingElement extends HTMLElement {
    constructor() {
        super();
        this.innerHTML = '<p>Hello, World!</p>';
    }
}

customElements.define('greeting-element', GreetingElement);

// Sử dụng phần tử tùy chỉnh trong HTML
document.body.innerHTML = '<greeting-element></greeting-element>';
```

### Ví dụ với thuộc tính
```javascript
class UserCard extends HTMLElement {
    constructor() {
        super();
        this.attachShadow({ mode: 'open' });
        this.shadowRoot.innerHTML = `
            <style>
                .card { border: 1px solid #ccc; padding: 16px; }
            </style>
            <div class="card">
                <h2>${this.getAttribute('name')}</h2>
                <p>${this.getAttribute('email')}</p>
            </div>
        `;
    }
}

customElements.define('user-card', UserCard);

// Sử dụng với thuộc tính
document.body.innerHTML = '<user-card name="John Doe" email="john@example.com"></user-card>';
```

## Giải thích
### Những cạm bẫy phổ biến
1. **Không đăng ký tên phần tử**: Trước khi sử dụng phần tử tùy chỉnh, bạn phải đăng ký nó. Nếu không, trình duyệt sẽ không nhận diện được.
2. **Tên phần tử không hợp lệ**: Tên phần tử tùy chỉnh phải chứa dấu gạch nối (chẳng hạn: `my-element`). Nếu không, trình duyệt sẽ coi đó là một phần tử HTML tiêu chuẩn.
3. **Quên gọi `super()` trong constructor**: Khi kế thừa từ `HTMLElement`, bạn cần gọi `super()` trong constructor để đảm bảo phần tử hoạt động đúng cách.
4. **Thiếu phương thức lifecycle**: Nếu bạn cần thực hiện hành động khi phần tử được thêm hoặc xóa khỏi DOM, hãy chắc chắn định nghĩa các phương thức `connectedCallback` và `disconnectedCallback`.

## Tóm tắt một dòng
`customElements` cho phép bạn tạo và quản lý các phần tử HTML tùy chỉnh, mở rộng khả năng của DOM trong JavaScript.