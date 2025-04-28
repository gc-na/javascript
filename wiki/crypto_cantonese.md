<!--
Meta Description: # JavaScript 中的加密技術 (Crypto) ## 概要 本文章將探討 JavaScript 中的加密技術（Crypto），其主要用於數據加密、解密及生成加密哈希。這些功能對於保護用戶數據及提高應用程序安全性至關重要。 ## 文檔 ### 目的 JavaScript 的加密技術（Cryp...
Meta Keywords: crypto, javascript, const, api, encoder
-->

# JavaScript 中的加密技術 (Crypto)

## 概要
本文章將探討 JavaScript 中的加密技術（Crypto），其主要用於數據加密、解密及生成加密哈希。這些功能對於保護用戶數據及提高應用程序安全性至關重要。

## 文檔
### 目的
JavaScript 的加密技術（Crypto）提供了一系列的 API，讓開發人員能夠進行加密、解密和數據哈希運算。這些功能主要用於保障數據的安全性，防止未經授權的訪問。

### 使用
在 JavaScript 中，Crypto API 通常於瀏覽器環境中使用，特別是通過 `window.crypto` 物件訪問。它支持多種加密算法，如 SHA-256、AES 等。

#### 主要功能
1. **哈希生成**：利用 SHA 演算法生成數據的哈希值。
2. **對稱加密**：使用同一把密鑰進行數據的加密及解密。
3. **隨機數生成**：生成安全隨機數以用於密鑰生成或其他加密操作。

## 示例
### 哈希生成示例
```javascript
async function generateHash(message) {
    const encoder = new TextEncoder();
    const data = encoder.encode(message);
    const hash = await crypto.subtle.digest('SHA-256', data);
    return Array.from(new Uint8Array(hash)).map(b => b.toString(16).padStart(2, '0')).join('');
}

generateHash("Hello, World!").then(console.log);
```

### 對稱加密示例
```javascript
async function encryptData(data, key) {
    const iv = crypto.getRandomValues(new Uint8Array(12));
    const encoder = new TextEncoder();
    const encodedData = encoder.encode(data);
    
    const ciphertext = await crypto.subtle.encrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        encodedData
    );

    return { ciphertext, iv };
}
```

## 解釋
### 常見陷阱
1. **密鑰管理**：密鑰的安全存儲及管理至關重要，若密鑰被洩露，數據安全將無法保障。
2. **錯誤的加密算法選擇**：使用不安全或過時的加密算法會導致數據受到威脅，應選擇當前被廣泛認可的加密標準。
3. **異步處理**：Crypto API 的許多操作都是異步的，開發者需確保適當處理 Promise 以避免錯誤。

## 一句總結
JavaScript 的 Crypto API 提供強大的加密功能，幫助開發者確保數據的安全性與隱私。