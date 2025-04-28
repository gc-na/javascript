<!--
Meta Description: # TrustedScript trong JavaScript: Bảo vệ an toàn cho mã lệnh động ## Tóm tắt TrustedScript là một đối tượng trong JavaScript, được thiết kế để bảo vệ ...
Meta Keywords: trustedscript, lệnh, thực, được, một
-->

# TrustedScript trong JavaScript: Bảo vệ an toàn cho mã lệnh động

## Tóm tắt
TrustedScript là một đối tượng trong JavaScript, được thiết kế để bảo vệ và quản lý mã lệnh động, giúp ngăn chặn các cuộc tấn công XSS (Cross-Site Scripting) bằng cách chỉ cho phép mã lệnh đã được xác thực và đáng tin cậy.

## Tài liệu
### Mục đích
Mục tiêu của TrustedScript là cung cấp một phương pháp an toàn để xử lý mã lệnh động trong môi trường web. Khi sử dụng TrustedScript, các nhà phát triển có thể đảm bảo rằng chỉ những mã lệnh đã được kiểm tra và xác thực mới được thực thi, giảm thiểu nguy cơ gây ra các lỗ hổng bảo mật.

### Cách sử dụng
Để sử dụng TrustedScript, bạn cần phải tạo một đối tượng TrustedScript từ một nguồn đáng tin cậy. Việc này thường được thực hiện thông qua các API bảo mật của trình duyệt, chẳng hạn như `Trusted Types`.

Dưới đây là một đoạn mã ví dụ mô tả cách tạo và sử dụng TrustedScript:

```javascript
// Kiểm tra xem Trusted Types có được hỗ trợ không
if (window.TrustedTypes) {
    // Tạo một TrustedScript
    const trustedScript = TrustedTypes.createPolicy('default', {
        createScript: (input) => {
            // Kiểm tra và xác thực mã lệnh
            return input; // Trả về mã lệnh đã được xác thực
        }
    }).createScript('console.log("Hello, World!")');

    // Thực thi mã lệnh TrustedScript
    eval(trustedScript);
}
```

## Ví dụ
1. **Tạo và thực thi TrustedScript**:
   ```javascript
   const policy = TrustedTypes.createPolicy('example', {
       createScript: (input) => {
           return input; // Chỉ cho phép mã lệnh đã được xác thực
       }
   });

   const script = policy.createScript('alert("Hello, TrustedScript!");');
   eval(script); // Thực thi TrustedScript an toàn
   ```

2. **Ngăn chặn mã lệnh không đáng tin cậy**:
   ```javascript
   const policy = TrustedTypes.createPolicy('secure', {
       createScript: (input) => {
           return input; // Chỉ cho phép mã lệnh đã được xác thực
       }
   });

   try {
       const unsafeScript = '<script>alert("XSS Attack!");</script>';
       const trustedScript = policy.createScript(unsafeScript); // Không thể tạo TrustedScript từ mã không an toàn
   } catch (error) {
       console.error('Mã không an toàn:', error);
   }
   ```

## Giải thích
- **Những cạm bẫy thường gặp**: Một trong những cạm bẫy phổ biến khi sử dụng TrustedScript là việc không xác thực mã lệnh trước khi tạo TrustedScript. Nếu không kiểm tra kỹ lưỡng, có thể vô tình cho phép mã độc chạy trong ứng dụng.
- **Chú ý**: TrustedScript chỉ có hiệu lực trong các môi trường hỗ trợ Trusted Types. Đảm bảo kiểm tra tính khả dụng của nó trước khi triển khai.

## Tóm tắt một dòng
TrustedScript là một đối tượng trong JavaScript giúp bảo vệ an toàn cho mã lệnh động bằng cách chỉ cho phép thực thi mã lệnh đã được xác thực và đáng tin cậy.