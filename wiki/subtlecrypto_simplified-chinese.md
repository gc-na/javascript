<!--
Meta Description: # SubtleCrypto：JavaScript中的加密API详解 ## 概述 SubtleCrypto 是 Web Cryptography API 的一部分，提供了一组加密功能，允许开发者在 JavaScript 中进行加密、解密、签名和验证等操作。该 API 旨在增强 Web 应用程序的安全...
Meta Keywords: subtlecrypto, api, const, window, crypto
-->

# SubtleCrypto：JavaScript中的加密API详解

## 概述
SubtleCrypto 是 Web Cryptography API 的一部分，提供了一组加密功能，允许开发者在 JavaScript 中进行加密、解密、签名和验证等操作。该 API 旨在增强 Web 应用程序的安全性，并提供底层加密原语。

## 文档
### 目的
SubtleCrypto 的主要目的是为 Web 开发者提供安全的加密操作接口，以便在客户端处理敏感数据时，确保数据的机密性和完整性。

### 使用方法
SubtleCrypto API 通过 `window.crypto.subtle` 对象访问。它支持多种加密算法，包括但不限于 AES、RSA 和 HMAC。以下是常用的方法：

- **generateKey()**: 生成加密密钥。
- **encrypt()**: 对数据进行加密。
- **decrypt()**: 对加密数据进行解密。
- **sign()**: 生成数据签名。
- **verify()**: 验证数据签名。
- **importKey()**: 从原始格式导入密钥。
- **exportKey()**: 将密钥导出为可用格式。

### 详细说明
SubtleCrypto API 主要用于处理加密操作，增强数据的安全性。它的使用通常涉及以下步骤：

1. **生成密钥**: 使用 `generateKey()` 方法生成加密密钥。
2. **导入密钥**: 如果你有现成的密钥，可以使用 `importKey()` 方法将其导入。
3. **加密和解密**: 通过 `encrypt()` 和 `decrypt()` 方法处理数据。
4. **签名和验证**: 使用 `sign()` 和 `verify()` 方法确保数据的完整性。

## 示例
以下是 SubtleCrypto 的基本用法示例：

### 生成 AES 密钥并加密数据
```javascript
async function encryptData(data) {
    const encoder = new TextEncoder();
    const key = await window.crypto.subtle.generateKey(
        { name: "AES-GCM", length: 256 },
        true,
        ["encrypt", "decrypt"]
    );

    const iv = window.crypto.getRandomValues(new Uint8Array(12)); // 初始化向量
    const encryptedData = await window.crypto.subtle.encrypt(
        { name: "AES-GCM", iv: iv },
        key,
        encoder.encode(data)
    );

    return { encryptedData, key, iv };
}
```

### 解密数据
```javascript
async function decryptData(encryptedData, key, iv) {
    const decryptedData = await window.crypto.subtle.decrypt(
        { name: "AES-GCM", iv: iv },
        key,
        encryptedData
    );

    const decoder = new TextDecoder();
    return decoder.decode(decryptedData);
}
```

## 说明
使用 SubtleCrypto 时，开发者需要注意以下几点：

- **浏览器支持**: 并非所有浏览器都完全支持 SubtleCrypto API，因此在使用前需检查兼容性。
- **异步操作**: SubtleCrypto 的大多数方法都是异步的，需使用 `async/await` 或者 Promise 处理。
- **错误处理**: 在调用加密或解密操作时，务必添加错误处理逻辑，以防止因密钥不匹配或数据损坏导致的异常。
- **安全性**: 处理敏感数据时，确保遵循最佳实践，例如使用安全的随机数生成器。

## 一句话总结
SubtleCrypto 是一个强大的 JavaScript API，用于实现安全的加密、解密、签名和验证操作，从而保护 Web 应用程序中的敏感数据。