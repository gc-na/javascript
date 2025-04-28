<!--
Meta Description: # CryptoKey：JavaScript 中的加密密鑰物件 ## 摘要 `CryptoKey` 是 Web Cryptography API 中的一個重要物件，負責管理加密演算法所需的密鑰。它提供了安全的方式來生成、存儲和使用加密密鑰。 ## 文件說明 `CryptoKey` 的主要目的是為了支...
Meta Keywords: cryptokey, key, jwk, generatekey, subtle
-->

# CryptoKey：JavaScript 中的加密密鑰物件

## 摘要
`CryptoKey` 是 Web Cryptography API 中的一個重要物件，負責管理加密演算法所需的密鑰。它提供了安全的方式來生成、存儲和使用加密密鑰。

## 文件說明
`CryptoKey` 的主要目的是為了支持加密操作，如加密、解密、簽名和驗證等。這個物件允許開發者使用各種加密演算法，並確保密鑰的安全性和正確性。

### 主要特性
- **安全性**：`CryptoKey` 物件的設計旨在確保敏感資料的安全，不會被意外地暴露。
- **多樣性**：支持多種加密演算法，包括對稱加密和非對稱加密。
- **互操作性**：與其他 Web Cryptography API 的組件協同工作。

### 使用方法
`CryptoKey` 物件通常由 `SubtleCrypto` 接口的各種方法所返回，例如 `importKey` 和 `generateKey`。開發者不需要直接創建 `CryptoKey` 物件，而是通過這些方法來獲取。

## 範例
以下是一個使用 `CryptoKey` 的基本範例，展示如何生成和導入一個對稱密鑰：

```javascript
// 獲取 SubtleCrypto 物件
const subtle = window.crypto.subtle;

// 生成一個 AES-GCM 密鑰
async function generateKey() {
    const key = await subtle.generateKey(
        {
            name: "AES-GCM",
            length: 256,
        },
        true,  // 是否可導出
        ["encrypt", "decrypt"]  // 可用的操作
    );
    console.log(key); // 輸出 CryptoKey 物件
}

// 導入密鑰
async function importKey(jwk) {
    const key = await subtle.importKey(
        "jwk",  // 密鑰格式
        jwk,    // JWK 物件
        {
            name: "AES-GCM",
        },
        true,   // 是否可導出
        ["encrypt", "decrypt"]
    );
    console.log(key); // 輸出導入的 CryptoKey 物件
}

// 呼叫生成密鑰的函數
generateKey();
```

## 解釋
在使用 `CryptoKey` 時，開發者可能會遇到以下常見問題：

- **密鑰格式**：`CryptoKey` 物件的格式必須正確，如使用 JWK (JSON Web Key) 或 RAW 格式。
- **操作權限**：在生成或導入密鑰時，必須正確指定可用的操作，否則會導致錯誤。
- **導出問題**：如果密鑰標記為不可導出，則無法將其轉換為其他格式。

## 一句總結
`CryptoKey` 是 JavaScript 中用於安全管理加密密鑰的物件，支持多種加密演算法並確保數據安全。