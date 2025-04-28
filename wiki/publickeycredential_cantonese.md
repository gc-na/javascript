<!--
Meta Description: # PublicKeyCredential：JavaScript 中的安全認證標準 ## 概要 PublicKeyCredential 是一個用於 Web 身份驗證的 JavaScript 接口，支持基於公鑰的認證方法，旨在提高網上安全性並改善用戶體驗。 ## 文檔 PublicKeyCredent...
Meta Keywords: publickeycredential, error, javascript, navigator, credentials
-->

# PublicKeyCredential：JavaScript 中的安全認證標準

## 概要
PublicKeyCredential 是一個用於 Web 身份驗證的 JavaScript 接口，支持基於公鑰的認證方法，旨在提高網上安全性並改善用戶體驗。

## 文檔
PublicKeyCredential 是一個 Web API，主要用於實現以公鑰為基礎的身份驗證。它是 WebAuthn 標準的一部分，允許用戶使用生物識別技術或硬體安全密鑰進行安全登錄。這個接口的主要目的是提供一種安全的方式來驗證用戶身份，避免傳統的密碼安全漏洞。

### 主要用途：
- **提高安全性**：使用公鑰加密技術，減少密碼被竊取的風險。
- **增強用戶體驗**：支持生物識別技術，讓用戶更方便地進行身份驗證。

### 使用方法：
要使用 PublicKeyCredential，開發者需要調用 `navigator.credentials.create()` 和 `navigator.credentials.get()` 方法來創建和獲取憑證。

### 詳細說明：
- **PublicKeyCredential.create()**: 用於創建新的公鑰憑證，通常在用戶註冊時呼叫。
- **PublicKeyCredential.get()**: 用於獲取現有的公鑰憑證，通常在用戶登錄時呼叫。

## 例子
### 創建憑證的基本範例：
```javascript
const publicKey = {
  challenge: new Uint8Array(32), // 隨機生成的挑戰
  rp: {
    name: "Demo Site",
  },
  user: {
    id: new Uint8Array(16), // 用戶的唯一標識符
    name: "user@example.com",
    displayName: "User",
  },
  pubKeyCredParams: [{ type: "public-key", alg: -7 }], // 支持的公鑰算法
};

navigator.credentials.create({ publicKey })
  .then((credential) => {
    // 成功創建憑證
    console.log(credential);
  })
  .catch((error) => {
    // 處理錯誤
    console.error(error);
  });
```

### 獲取憑證的基本範例：
```javascript
const publicKeyRequest = {
  challenge: new Uint8Array(32), // 伺服器生成的挑戰
  allowCredentials: [{
    id: new Uint8Array(16), // 用戶的憑證 ID
    type: "public-key",
  }],
};

navigator.credentials.get({ publicKey: publicKeyRequest })
  .then((credential) => {
    // 成功獲取憑證
    console.log(credential);
  })
  .catch((error) => {
    // 處理錯誤
    console.error(error);
  });
```

## 解釋
使用 PublicKeyCredential 時，有幾個常見的陷阱和注意事項：
- **挑戰值**：每次創建憑證時必須使用隨機生成的挑戰值，否則會導致安全漏洞。
- **瀏覽器支持**：並非所有瀏覽器都支持 WebAuthn，因此在使用前需確認兼容性。
- **HTTPS 要求**：此 API 只有在 HTTPS 環境下才可用，以確保通信的安全性。

## 一句總結
PublicKeyCredential 是一個強大的 JavaScript API，用於實現安全的公鑰身份驗證，顯著提高網上安全性和用戶體驗。