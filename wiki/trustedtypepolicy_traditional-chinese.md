<!--
Meta Description: # TrustedTypePolicy：JavaScript中的安全字串處理機制 ## 概述 TrustedTypePolicy 是一項 JavaScript API，旨在防止跨站腳本（XSS）攻擊，通過強制使用安全的字串處理方式來增強 Web 應用的安全性。 ## 文檔 ### 目的 Truste...
Meta Keywords: trustedtypepolicy, trustedtypes, javascript, policy, createhtml
-->

# TrustedTypePolicy：JavaScript中的安全字串處理機制

## 概述
TrustedTypePolicy 是一項 JavaScript API，旨在防止跨站腳本（XSS）攻擊，通過強制使用安全的字串處理方式來增強 Web 應用的安全性。

## 文檔
### 目的
TrustedTypePolicy 的主要目的是提供一種機制，讓開發者能夠定義和使用受信任的字串，確保這些字串在應用中不會被不安全的代碼操控，從而減少潛在的安全風險。

### 使用方法
要使用 TrustedTypePolicy，開發者需要創建一個 TrustedTypePolicy 實例，並定義安全的字串處理規則。以下是創建和使用 TrustedTypePolicy 的基本步驟：

1. **定義 TrustedTypePolicy**：
   使用 `TrustedTypes.createPolicy()` 方法創建一個新的政策，並傳入一個名稱和一個處理函數。

   ```javascript
   const policy = TrustedTypes.createPolicy('default', {
       createHTML: (input) => {
           // 檢查輸入的內容並返回安全的 HTML
           return input; // 這裡應該有更全面的安全檢查
       }
   });
   ```

2. **使用政策**：
   使用創建的政策來生成受信任的字串，然後在應用中使用這些字串。

   ```javascript
   const trustedHTML = policy.createHTML('<div>Hello, World!</div>');
   document.body.innerHTML = trustedHTML;
   ```

3. **註冊政策**：
   一旦政策創建，瀏覽器將自動使用該政策來處理相應的字串，從而保護應用免受 XSS 攻擊。

### 詳細信息
- **API 方法**：
  - `TrustedTypes.createPolicy(name, policy)`：創建一個新的 TrustedTypePolicy。
  - `TrustedTypes.getPolicy(name)`：獲取已創建的政策。
  - `TrustedTypes.getPolicyNames()`：獲取所有已創建政策的名稱。

## 示例
以下是一個簡單的使用範例：

```javascript
// 創建一個 TrustedTypePolicy
const policy = TrustedTypes.createPolicy('example', {
    createHTML: (input) => input // 實際使用中需進行驗證
});

// 使用政策來安全地插入 HTML
const safeHTML = policy.createHTML('<p>安全的內容</p>');
document.getElementById('content').innerHTML = safeHTML;
```

## 解釋
- **常見陷阱**：
  - 確保在 `createHTML` 方法中執行充分的輸入驗證，以避免傳遞不安全的內容。
  - 不要在未經過 TrustedTypes 政策處理的情況下直接使用用戶輸入的資料。

- **注意事項**：
  - TrustedTypePolicy 並不會自動防止所有 XSS 攻擊，開發者仍需謹慎設計應用的其他部分。
  - 不同瀏覽器對 Trusted Types 的支持情況可能會有所不同，請確保在開發過程中進行充分的測試。

## 一句總結
TrustedTypePolicy 是一種 JavaScript 機制，用於通過創建受信任的字串來增強 Web 應用的安全性，防止 XSS 攻擊。