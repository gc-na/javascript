<!--
Meta Description: # JavaScript 中的加密 (Crypto) 函式庫 ## 概述 JavaScript 的加密 (Crypto) 函式庫提供了一組用於加密和解密數據的功能，主要用於增強網頁應用程式的安全性。這些功能包括生成隨機數、雜湊、對稱加密及非對稱加密等。 ## 文檔 ### 目的 JavaScript...
Meta Keywords: crypto, const, javascript, window, new
-->

# JavaScript 中的加密 (Crypto) 函式庫

## 概述
JavaScript 的加密 (Crypto) 函式庫提供了一組用於加密和解密數據的功能，主要用於增強網頁應用程式的安全性。這些功能包括生成隨機數、雜湊、對稱加密及非對稱加密等。

## 文檔
### 目的
JavaScript 的加密 (Crypto) 函式庫旨在提供安全的加密功能，以保護敏感數據，並確保數據在傳輸過程中的完整性和機密性。

### 使用方法
在瀏覽器中，Crypto 函式庫主要通過 `window.crypto` 物件訪問。在 Node.js 環境中，則使用內建的 `crypto` 模組。

#### 主要功能：
1. **隨機數生成**：用於生成安全隨機數。
2. **雜湊函數**：支援多種雜湊演算法，如 SHA-256。
3. **對稱加密**：提供 AES 等加密演算法。
4. **非對稱加密**：使用 RSA 等演算法進行加密和解密。

### 詳細說明
- **隨機數生成**：使用 `crypto.getRandomValues()` 方法可以生成隨機數位陣列。
- **雜湊**：可以利用 `SubtleCrypto` 介面的 `digest` 方法來計算資料的雜湊值。
- **加密解密**：對於對稱加密，可以使用 `encrypt` 和 `decrypt` 方法進行數據保護。

## 範例
### 隨機數生成
```javascript
const array = new Uint32Array(10);
window.crypto.getRandomValues(array);
console.log(array);
```

### 計算 SHA-256 雜湊
```javascript
async function hashData(data) {
    const encoder = new TextEncoder();
    const dataBuffer = encoder.encode(data);
    const hashBuffer = await window.crypto.subtle.digest('SHA-256', dataBuffer);
    const hashArray = Array.from(new Uint8Array(hashBuffer));
    const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('');
    return hashHex;
}

hashData('Hello, World!').then(console.log);
```

### 對稱加密示例
```javascript
async function encryptData(plainText, key) {
    const encoder = new TextEncoder();
    const iv = window.crypto.getRandomValues(new Uint8Array(12));
    const encryptedBuffer = await window.crypto.subtle.encrypt(
        { name: "AES-GCM", iv: iv },
        key,
        encoder.encode(plainText)
    );
    return { iv, encryptedBuffer };
}
```

## 解釋
常見的問題包括：
- **不支援的瀏覽器**：某些舊版本的瀏覽器可能不支援 Crypto API，開發者應檢查兼容性。
- **密鑰管理**：生成和儲存密鑰的方式至關重要，應避免硬編碼密鑰。
- **異步操作**：大多數加密操作是異步的，開發者應善用 `async/await` 或 Promise 來處理。

## 總結
JavaScript 的 Crypto 函式庫提供了強大的加密功能，對於保護網頁應用程式中的敏感數據至關重要。