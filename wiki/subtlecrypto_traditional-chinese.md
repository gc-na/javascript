<!--
Meta Description: # SubtleCrypto：JavaScript 中的安全加密 API ## 概述 SubtleCrypto 是一個在 Web Cryptography API 中提供的 JavaScript 接口，旨在為開發者提供加密、解密和數據簽名的功能，從而在網頁應用程序中增強安全性。 ## 文檔 Subt...
Meta Keywords: subtlecrypto, const, javascript, data, encodeddata
-->

# SubtleCrypto：JavaScript 中的安全加密 API

## 概述
SubtleCrypto 是一個在 Web Cryptography API 中提供的 JavaScript 接口，旨在為開發者提供加密、解密和數據簽名的功能，從而在網頁應用程序中增強安全性。

## 文檔
SubtleCrypto 的主要目的是提供低級別的加密操作，這些操作通常用於保護敏感數據或實現身份驗證。它允許開發者利用瀏覽器的加密功能，而不需要依賴外部庫。

### 主要功能
- **加密和解密**：支持多種加密算法，包括對稱和非對稱加密。
- **數據簽名和驗證**：能夠生成數據簽名並驗證其有效性。
- **鍵生成和管理**：提供生成和存儲加密密鑰的功能。

### 使用方法
SubtleCrypto 通常通過 `window.crypto.subtle` 獲取。以下是一些基本操作的使用示例：

```javascript
// 獲取 SubtleCrypto 實例
const subtleCrypto = window.crypto.subtle;
```

## 示例
### 1. 數據的加密與解密
```javascript
async function encryptData(data, key) {
    const encodedData = new TextEncoder().encode(data);
    const encryptedData = await subtleCrypto.encrypt(
        { name: "AES-GCM", iv: crypto.getRandomValues(new Uint8Array(12)) },
        key,
        encodedData
    );
    return encryptedData;
}

async function decryptData(encryptedData, key, iv) {
    const decryptedData = await subtleCrypto.decrypt(
        { name: "AES-GCM", iv: iv },
        key,
        encryptedData
    );
    return new TextDecoder().decode(decryptedData);
}
```

### 2. 數據簽名
```javascript
async function signData(data, privateKey) {
    const encodedData = new TextEncoder().encode(data);
    const signature = await subtleCrypto.sign(
        { name: "RSASSA-PKCS1-v1_5" },
        privateKey,
        encodedData
    );
    return signature;
}

async function verifySignature(signature, data, publicKey) {
    const encodedData = new TextEncoder().encode(data);
    const isValid = await subtleCrypto.verify(
        { name: "RSASSA-PKCS1-v1_5" },
        publicKey,
        signature,
        encodedData
    );
    return isValid;
}
```

## 解釋
使用 SubtleCrypto 時，有幾個常見的陷阱和注意事項：
- **錯誤的參數**：許多方法需要特定格式的參數，提供錯誤的數據結構會導致運行時錯誤。
- **非同步操作**：大多數 SubtleCrypto 操作都是異步的，必須使用 `async/await` 或 `Promise` 來處理結果。
- **兼容性問題**：並非所有瀏覽器都支持所有的加密算法，開發者應該查閱相應的兼容性表格。

## 總結
SubtleCrypto 提供了一組強大且靈活的加密工具，能有效增強 JavaScript 應用程序的安全性。