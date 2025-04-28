<!--
Meta Description: # JavaScript 中的 CryptoKey：加密與安全性 ## 簡介 CryptoKey 是一個在 Web Cryptography API 中使用的接口，主要用於處理加密密鑰。這個接口使開發者能夠有效地生成、保存和使用加密密鑰，從而增強網頁應用程序的安全性。 ## 文件說明 ### 目的 ...
Meta Keywords: cryptokey, key, window, crypto, subtle
-->

# JavaScript 中的 CryptoKey：加密與安全性

## 簡介
CryptoKey 是一個在 Web Cryptography API 中使用的接口，主要用於處理加密密鑰。這個接口使開發者能夠有效地生成、保存和使用加密密鑰，從而增強網頁應用程序的安全性。

## 文件說明
### 目的
CryptoKey 接口的主要目的在於提供一種安全的方式來管理加密密鑰，支持對稱和非對稱加密。這使得開發者能夠在應用程序中實現數據加密和解密功能，確保敏感信息的保護。

### 使用方法
要使用 CryptoKey，開發者通常需要利用 `SubtleCrypto` API 來生成或導入密鑰。使用 `window.crypto.subtle` 的方法可以創建或導入 CryptoKey 對象，並在需要時進行加密和解密操作。

### 詳細說明
- **生成密鑰**：使用 `generateKey` 方法來創建新的加密密鑰。
- **導入密鑰**：可以從外部數據導入密鑰，使用 `importKey` 方法。
- **導出密鑰**：可以使用 `exportKey` 方法來將密鑰導出為可以存儲或傳輸的格式。
- **加密與解密**：使用 `encrypt` 和 `decrypt` 方法來對數據進行加密和解密操作。

## 範例
以下是使用 CryptoKey 進行基本加密和解密的範例：

```javascript
async function generateKey() {
    const key = await window.crypto.subtle.generateKey(
        {
            name: "AES-GCM",
            length: 256,
        },
        true, // 是否可以導出密鑰
        ["encrypt", "decrypt"] // 允許的用途
    );
    return key;
}

async function encryptData(key, data) {
    const iv = window.crypto.getRandomValues(new Uint8Array(12)); // 初始化向量
    const encryptedData = await window.crypto.subtle.encrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        data // 要加密的數據
    );
    return { encryptedData, iv };
}

async function decryptData(key, encryptedData, iv) {
    const decryptedData = await window.crypto.subtle.decrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        encryptedData // 要解密的數據
    );
    return decryptedData;
}
```

## 解釋
使用 CryptoKey 時，開發者需要注意以下幾點：
- **密鑰的可導出性**：生成的密鑰如果設置為不可導出，則無法通過 `exportKey` 方法導出。
- **初始化向量（IV）**：在使用某些加密算法（如 AES-GCM）時，必須提供隨機生成的初始化向量以確保安全性。
- **錯誤處理**：加密和解密過程中可能會出現錯誤，例如密鑰不匹配或數據格式不正確，因此應包括適當的錯誤處理邏輯。

## 總結
CryptoKey 是 JavaScript 中 Web Cryptography API 的核心部分，提供了一種安全且靈活的方式來處理加密密鑰，對於提升應用程序的安全性至關重要。