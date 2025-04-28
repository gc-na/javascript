<!--
Meta Description: # SubtleCrypto：JavaScript 的安全加密 API ## 概要 SubtleCrypto 是一個在 Web Cryptography API 中提供的接口，允許開發者使用現代加密演算法來保護數據。這個接口提供了加密、解密、簽名和驗證等功能，對於需要高安全性的應用程序特別重要。 #...
Meta Keywords: const, key, subtlecrypto, subtle, await
-->

# SubtleCrypto：JavaScript 的安全加密 API

## 概要
SubtleCrypto 是一個在 Web Cryptography API 中提供的接口，允許開發者使用現代加密演算法來保護數據。這個接口提供了加密、解密、簽名和驗證等功能，對於需要高安全性的應用程序特別重要。

## 文檔

### 目的
SubtleCrypto 旨在幫助開發者輕鬆實現加密和解密操作，保護用戶數據的隱私和安全。它支持多種加密演算法，並且可以在不依賴外部庫的情況下進行操作。

### 用法
SubtleCrypto 是通過 `crypto.subtle` 屬性訪問的。這個接口提供了多個方法來執行加密相關的操作，例如：

- `encrypt()`: 用於加密數據。
- `decrypt()`: 用於解密數據。
- `sign()`: 用於生成數據的數位簽名。
- `verify()`: 用於驗證數位簽名的有效性。
- `generateKey()`: 用於生成加密密鑰。

以下是一個基本的用法示例：

```javascript
// 獲取 SubtleCrypto 接口
const subtle = window.crypto.subtle;

// 生成密鑰
const generateKey = async () => {
    const key = await subtle.generateKey(
        {
            name: "AES-GCM",
            length: 256,
        },
        true,
        ["encrypt", "decrypt"]
    );
    return key;
};

// 加密數據
const encryptData = async (key, data) => {
    const iv = window.crypto.getRandomValues(new Uint8Array(12)); // 初始化向量
    const encrypted = await subtle.encrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        data
    );
    return { encrypted, iv };
};

// 解密數據
const decryptData = async (key, encryptedData, iv) => {
    const decrypted = await subtle.decrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        encryptedData
    );
    return decrypted;
};
```

## 示例
以下是一個完整的示例，展示如何生成密鑰、加密和解密數據：

```javascript
(async () => {
    const key = await generateKey();
    const data = new TextEncoder().encode("Hello, World!");

    const { encrypted, iv } = await encryptData(key, data);
    console.log("加密後的數據:", new Uint8Array(encrypted));

    const decrypted = await decryptData(key, encrypted, iv);
    console.log("解密後的數據:", new TextDecoder().decode(decrypted));
})();
```

## 解釋
使用 SubtleCrypto 進行加密時，有幾個常見的注意事項：

1. **支持的演算法**：並非所有瀏覽器都支持所有的加密演算法，使用前請確認瀏覽器兼容性。
2. **密鑰管理**：生成的密鑰應妥善保存和使用，避免密鑰洩露。
3. **初始化向量 (IV)**：在加密過程中，使用隨機生成的 IV 是很重要的，避免重複使用相同的 IV 會增加被破解的風險。
4. **錯誤處理**：要妥善處理加密和解密過程中的錯誤，確保應用的健壯性。

## 一句總結
SubtleCrypto 是一個強大的 JavaScript API，為開發者提供了進行安全數據加密和解密的簡便方法。