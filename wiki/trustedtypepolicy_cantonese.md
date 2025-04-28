<!--
Meta Description: # TrustedTypePolicy：JavaScript 中的安全字串處理 ## 概述 TrustedTypePolicy 是一個 JavaScript API，旨在增強網頁應用程式的安全性，特別是防範跨網站腳本（XSS）攻擊。它通過限制和控制可用於 DOM 操作的字串來實現這一點。 ## 文檔...
Meta Keywords: trustedtypepolicy, javascript, trustedtypes, name, policy
-->

# TrustedTypePolicy：JavaScript 中的安全字串處理

## 概述
TrustedTypePolicy 是一個 JavaScript API，旨在增強網頁應用程式的安全性，特別是防範跨網站腳本（XSS）攻擊。它通過限制和控制可用於 DOM 操作的字串來實現這一點。

## 文檔
### 目的
TrustedTypePolicy 的主要目的是提供一種安全的方式來處理動態字串，確保只有經過驗證的字串可以被用於 DOM 操作，這樣可以減少潛在的安全漏洞。

### 使用方法
1. **創建 TrustedTypePolicy**：使用 `TrustedTypes.createPolicy()` 方法來創建一個新的政策。
2. **使用 TrustedType**：通過政策生成的受信任字串來進行 DOM 操作，如插入 HTML。
3. **禁用 TrustedTypes**（可選）：通過 `TrustedTypes.emptyPolicy` 可以關閉所有的 Trusted Types 政策。

### 詳細說明
- **API 方法**：
  - `createPolicy(name, policy)`：創建一個新的 TrustedTypePolicy。
  - `getPolicy(name)`：獲取已存在的 TrustedTypePolicy。
  - `removePolicy(name)`：移除已存在的 TrustedTypePolicy。

- **政策參數**：
  - `name`：政策的名稱，必須是唯一的。
  - `policy`：一個對象，應包含 `createHTML`、`createScript`、`createScriptURL` 等方法。

## 範例
### 基本用法
```javascript
// 創建一個 TrustedTypePolicy
const policy = trustedTypes.createPolicy('myPolicy', {
    createHTML: (input) => {
        return input; // 在實際應用中，需進行輸入驗證
    }
});

// 使用 TrustedType
const safeHTML = policy.createHTML('<div>Hello World</div>');
document.body.innerHTML = safeHTML; // 安全地插入 HTML
```

## 解釋
### 常見陷阱
- **未進行輸入驗證**：在 `createHTML` 等方法中，必須確保對輸入進行適當的驗證，否則仍可能導致 XSS 漏洞。
- **政策名稱重複**：確保政策名稱不重複，否則會導致錯誤或意外行為。

### 額外說明
- Trusted Types 目前並非所有瀏覽器均支持，開發時應檢查瀏覽器兼容性。
- 使用 Trusted Types 可以與安全最佳實踐相結合，提供更強的防護。

## 一句總結
TrustedTypePolicy 提供了一種安全的方式來處理字串，從而減少 JavaScript 應用中的 XSS 攻擊風險。