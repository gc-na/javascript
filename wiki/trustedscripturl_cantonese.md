<!--
Meta Description: # TrustedScriptURL: JavaScript 中的安全腳本 URL ## 簡介 `TrustedScriptURL` 是一個安全的 JavaScript 接口，旨在確保只有可信的腳本能夠被執行，進而防範潛在的跨站腳本（XSS）攻擊。 ## 文檔 `TrustedScriptURL` ...
Meta Keywords: trustedscripturl, url, policy, javascript, const
-->

# TrustedScriptURL: JavaScript 中的安全腳本 URL

## 簡介
`TrustedScriptURL` 是一個安全的 JavaScript 接口，旨在確保只有可信的腳本能夠被執行，進而防範潛在的跨站腳本（XSS）攻擊。

## 文檔
`TrustedScriptURL` 的目的是為了提供一個安全的方式來處理和使用腳本 URL。它屬於 Trusted Types API，旨在增強 web 應用程序的安全性，防止不安全的代碼執行。當一個網站使用 `TrustedScriptURL` 時，它能夠驗證和信任特定的 URL，確保不會意外地執行惡意代碼。

### 用法
要使用 `TrustedScriptURL`，首先需要了解如何創建和使用這個接口。以下是基本的用法步驟：

1. **創建 Trusted Types Policy**:
   你需要先創建一個 Trusted Types policy，以便能夠生成 `TrustedScriptURL`。

   ```javascript
   const policy = trustedTypes.createPolicy('default', {
       createScriptURL: (input) => {
           // 驗證輸入 URL
           return input;
       }
   });
   ```

2. **生成 TrustedScriptURL**:
   利用創建的 policy 來生成 `TrustedScriptURL`。

   ```javascript
   const scriptUrl = policy.createScriptURL('https://example.com/script.js');
   ```

3. **使用 TrustedScriptURL**:
   然後可以安全地使用這個 URL 來加載腳本。

   ```javascript
   const scriptElement = document.createElement('script');
   scriptElement.src = scriptUrl;
   document.body.appendChild(scriptElement);
   ```

## 示例
以下是一些 `TrustedScriptURL` 的基本用法示例：

### 示例 1: 基本創建和使用

```javascript
const policy = trustedTypes.createPolicy('myPolicy', {
   createScriptURL: (input) => input
});

const trustedUrl = policy.createScriptURL('https://example.com/script.js');

const script = document.createElement('script');
script.src = trustedUrl;
document.head.appendChild(script);
```

### 示例 2: 防止不安全的 URL

```javascript
const policy = trustedTypes.createPolicy('securePolicy', {
   createScriptURL: (input) => {
       if (!input.startsWith('https://')) {
           throw new Error('不安全的 URL');
       }
       return input;
   }
});

try {
   const unsafeUrl = policy.createScriptURL('http://example.com/script.js'); // 這將會拋出錯誤
} catch (e) {
   console.error(e.message); // 輸出: 不安全的 URL
}
```

## 解釋
使用 `TrustedScriptURL` 時，開發者需要注意以下幾點：

- **信任來源**: 確保傳遞給 `createScriptURL` 的 URL 是來自可信的來源，以防 XSS 攻擊。
- **政策的限制**: 每個 Trusted Types policy 只能在創建時定義一次，無法更改。
- **瀏覽器支持**: 在使用 `TrustedScriptURL` 前，檢查目標瀏覽器的支持情況，以確保功能正常。

## 單行摘要
`TrustedScriptURL` 是一個用於創建安全腳本 URL 的 JavaScript 接口，旨在防止跨站腳本攻擊。