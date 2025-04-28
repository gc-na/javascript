<!--
Meta Description: # SubtleCrypto: Công Cụ Mã Hóa An Toàn trong JavaScript ## Tóm tắt SubtleCrypto là một giao diện trong Web Crypto API, cho phép thực hiện các thao tác...
Meta Keywords: hóa, các, subtlecrypto, trong, crypto
-->

# SubtleCrypto: Công Cụ Mã Hóa An Toàn trong JavaScript

## Tóm tắt
SubtleCrypto là một giao diện trong Web Crypto API, cho phép thực hiện các thao tác mã hóa và xác thực an toàn trong JavaScript. Nó cung cấp các phương thức để mã hóa, giải mã, tạo khóa, và xác thực dữ liệu.

## Tài liệu
### Mục đích
SubtleCrypto được thiết kế để cung cấp các chức năng mã hóa và xác thực hiện đại, giúp bảo mật thông tin trong ứng dụng web. Nó hỗ trợ nhiều thuật toán mã hóa khác nhau như AES, RSA, và SHA.

### Cách sử dụng
SubtleCrypto có thể được truy cập thông qua đối tượng `crypto.subtle`. Các phương thức phổ biến bao gồm:
- `encrypt()`: Mã hóa dữ liệu.
- `decrypt()`: Giải mã dữ liệu.
- `generateKey()`: Tạo khóa mã hóa.
- `sign()`: Ký dữ liệu.
- `verify()`: Kiểm tra chữ ký.

Cú pháp chung cho các phương thức trong SubtleCrypto như sau:

```javascript
crypto.subtle.methodName(algorithm, key, data);
```

### Chi tiết
Các phương thức trong SubtleCrypto thường trả về một Promise, cho phép xử lý bất đồng bộ. Ví dụ, để mã hóa một chuỗi, bạn cần thực hiện các bước sau:
1. Tạo khóa mã hóa.
2. Chuyển đổi dữ liệu sang định dạng `ArrayBuffer`.
3. Gọi phương thức `encrypt()`.

## Ví dụ
### Mã hóa và Giải mã Dữ liệu
```javascript
async function encryptData(data) {
    const encoder = new TextEncoder();
    const key = await crypto.subtle.generateKey(
        { name: "AES-GCM", length: 256 },
        true,
        ["encrypt", "decrypt"]
    );

    const iv = crypto.getRandomValues(new Uint8Array(12)); // Vector khởi tạo
    const ciphertext = await crypto.subtle.encrypt(
        { name: "AES-GCM", iv: iv },
        key,
        encoder.encode(data)
    );

    return { ciphertext, key, iv };
}

async function decryptData(ciphertext, key, iv) {
    const decrypted = await crypto.subtle.decrypt(
        { name: "AES-GCM", iv: iv },
        key,
        ciphertext
    );

    const decoder = new TextDecoder();
    return decoder.decode(decrypted);
}

// Sử dụng
(async () => {
    const { ciphertext, key, iv } = await encryptData("Hello World");
    const decryptedMessage = await decryptData(ciphertext, key, iv);
    console.log(decryptedMessage); // "Hello World"
})();
```

## Giải thích
- **Lỗi thường gặp**: Khi sử dụng SubtleCrypto, một số lỗi phổ biến bao gồm việc sử dụng sai định dạng dữ liệu đầu vào hoặc không cung cấp đủ thông tin như IV (Vector khởi tạo) cho các thuật toán mã hóa.
- **Lưu ý**: SubtleCrypto chỉ hoạt động trong môi trường an toàn (HTTPS) để đảm bảo tính bảo mật. Ngoài ra, các phương thức của nó là bất đồng bộ, vì vậy bạn cần sử dụng `async/await` hoặc `.then()` để xử lý kết quả.

## Tóm tắt một dòng
SubtleCrypto là một phần của Web Crypto API trong JavaScript, cung cấp các phương thức mã hóa và xác thực an toàn cho ứng dụng web.