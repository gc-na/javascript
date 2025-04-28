<!--
Meta Description: # CSSTransition trong JavaScript: Hiệu ứng chuyển đổi CSS dễ dàng ## Tóm tắt `CSSTransition` là một thành phần trong thư viện React Transition Group, ...
Meta Keywords: csstransition, ứng, hiệu, css, phần
-->

# CSSTransition trong JavaScript: Hiệu ứng chuyển đổi CSS dễ dàng

## Tóm tắt
`CSSTransition` là một thành phần trong thư viện React Transition Group, cho phép lập trình viên dễ dàng thêm hiệu ứng chuyển đổi CSS cho các phần tử trong ứng dụng React. Nó giúp tạo ra những trải nghiệm người dùng mượt mà hơn bằng cách kết hợp sự thay đổi trạng thái và hiệu ứng chuyển tiếp.

## Tài liệu
### Mục đích
`CSSTransition` được thiết kế để đơn giản hóa việc áp dụng các hiệu ứng CSS khi một phần tử thay đổi trạng thái. Khi trạng thái của phần tử thay đổi (ví dụ như xuất hiện hoặc biến mất), `CSSTransition` sẽ tự động thêm và gỡ bỏ các lớp CSS tương ứng để thực hiện hiệu ứng.

### Cách sử dụng
Để sử dụng `CSSTransition`, bạn cần cài đặt thư viện `react-transition-group`:

```bash
npm install react-transition-group
```

Sau đó, bạn có thể import `CSSTransition` vào trong component của bạn:

```javascript
import { CSSTransition } from 'react-transition-group';
```

### Cấu trúc
`CSSTransition` nhận vào một số props quan trọng:

- `in`: Xác định liệu phần tử có nên hiển thị hay không.
- `timeout`: Thời gian cho hiệu ứng chuyển tiếp.
- `classNames`: Tên của các lớp CSS sẽ được áp dụng trong suốt quá trình chuyển tiếp.
- `unmountOnExit`: Nếu được thiết lập, phần tử sẽ được gỡ bỏ khỏi DOM khi không còn hiển thị.

### Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng `CSSTransition` để tạo hiệu ứng chuyển đổi khi một phần tử xuất hiện và biến mất:

```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css'; // File chứa định nghĩa CSS cho hiệu ứng

const Example = () => {
    const [show, setShow] = useState(false);

    return (
        <div>
            <button onClick={() => setShow(!show)}>
                {show ? 'Ẩn' : 'Hiện'}
            </button>
            <CSSTransition
                in={show}
                timeout={300}
                classNames="fade"
                unmountOnExit
            >
                <div className="fade">Nội dung sẽ chuyển đổi!</div>
            </CSSTransition>
        </div>
    );
};

export default Example;
```

### Giải thích
Khi sử dụng `CSSTransition`, có một số điều cần lưu ý:

- **Thời gian timeout**: Thời gian chuyển tiếp (`timeout`) phải khớp với thời gian trong định nghĩa CSS của bạn để đảm bảo hiệu ứng hoạt động mượt mà.
- **Tên lớp CSS**: Tên lớp (`classNames`) phải được định nghĩa trong CSS của bạn. Chúng thường có dạng `classNames-enter`, `classNames-enter-active`, `classNames-exit`, và `classNames-exit-active`.
- **UnmountOnExit**: Việc sử dụng `unmountOnExit` có thể giúp cải thiện hiệu suất cho các ứng dụng lớn bằng cách không giữ các phần tử không cần thiết trong DOM.

## Tóm tắt một dòng
`CSSTransition` là một thành phần giúp dễ dàng áp dụng hiệu ứng chuyển đổi CSS cho các phần tử trong React, tạo ra trải nghiệm người dùng mượt mà hơn.