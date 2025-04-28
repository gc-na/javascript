<!--
Meta Description: # Trusted Types trong JavaScript: Bảo vệ Ứng Dụng Web khỏi Tấn Công XSS ## Tóm tắt Trusted Types là một API mới trong JavaScript nhằm giúp ngăn chặn c...
Meta Keywords: dụng, trusted, types, các, thực
-->

# Trusted Types trong JavaScript: Bảo vệ Ứng Dụng Web khỏi Tấn Công XSS

## Tóm tắt
Trusted Types là một API mới trong JavaScript nhằm giúp ngăn chặn các tấn công Cross-Site Scripting (XSS) bằng cách định nghĩa các loại giá trị tin cậy mà ứng dụng có thể sử dụng để xây dựng nội dung HTML hoặc JavaScript.

## Tài liệu
### Mục đích
Trusted Types được thiết kế để bảo vệ ứng dụng web khỏi tấn công XSS bằng cách yêu cầu các giá trị được sử dụng trong các phép tạo nội dung (như innerHTML hoặc eval) phải là các đối tượng Trusted Type. Điều này giúp đảm bảo rằng chỉ những giá trị đã được xác thực và an toàn mới được phép đi vào DOM.

### Cách sử dụng
Để sử dụng Trusted Types, bạn cần:
1. Kích hoạt Trusted Types trên ứng dụng của mình bằng cách bật chính sách trên trình duyệt.
2. Định nghĩa các Trusted Types bằng cách sử dụng `TrustedTypePolicy`.
3. Sử dụng các Trusted Types trong mã của bạn thay vì các chuỗi bất kỳ.

### Chi tiết
- **Tạo Trusted Type Policy**:
  ```javascript
  const policy = trustedTypes.createPolicy('myPolicy', {
      createHTML: (input) => {
          // Xử lý và xác thực input ở đây
          return input; // Trả về giá trị đã xác thực
      }
  });
  ```

- **Sử dụng Trusted Types**:
  ```javascript
  const safeHTML = policy.createHTML('<div>Hello, World!</div>');
  document.body.innerHTML = safeHTML; // Sử dụng giá trị tin cậy
  ```

## Ví dụ
```javascript
// Tạo một chính sách Trusted Type
const policy = trustedTypes.createPolicy('examplePolicy', {
    createHTML: (input) => {
        // Kiểm tra và xác thực input
        if (typeof input !== 'string') {
            throw new Error('Input must be a string');
        }
        return input; // Trả về giá trị đã xác thực
    }
});

// Sử dụng Trusted Type
const safeHTML = policy.createHTML('<p>Đây là nội dung an toàn.</p>');
document.body.innerHTML = safeHTML; // Gán vào DOM
```

## Giải thích
### Các rủi ro và lưu ý
- **Không sử dụng Trusted Types**: Nếu không áp dụng Trusted Types, ứng dụng của bạn có thể dễ bị tấn công XSS.
- **Lỗi không xác thực**: Nếu bạn không thực hiện xác thực đúng cách trong phương thức `createHTML`, bạn có thể vô tình cho phép mã độc vào ứng dụng.
- **Hỗ trợ trình duyệt**: Không phải tất cả các trình duyệt đều hỗ trợ Trusted Types. Hãy kiểm tra trước khi triển khai.

## Tóm tắt một dòng
Trusted Types là API trong JavaScript giúp ngăn chặn tấn công XSS bằng cách yêu cầu sử dụng các giá trị đã được xác thực trước khi thêm vào DOM.