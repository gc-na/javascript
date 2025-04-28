<!--
Meta Description: # TrustedHTML：JavaScript中的安全HTML處理 ## 概述 TrustedHTML 是一種用於 JavaScript 的安全 HTML 處理機制。它旨在防止跨站腳本攻擊（XSS），通過確保僅允許信任的 HTML 內容被插入到網頁中。 ## 文檔 ### 目的 TrustedHT...
Meta Keywords: trustedhtml, html, javascript, trustedtypepolicy, createhtml
-->

# TrustedHTML：JavaScript中的安全HTML處理

## 概述
TrustedHTML 是一種用於 JavaScript 的安全 HTML 處理機制。它旨在防止跨站腳本攻擊（XSS），通過確保僅允許信任的 HTML 內容被插入到網頁中。

## 文檔
### 目的
TrustedHTML 的主要目的是提供一種安全的方式來處理和插入 HTML，特別是在動態生成內容時。它防止未經授權的代碼執行，從而提升網頁的安全性。

### 使用方法
TrustedHTML 可以通過特定的 API 來創建和驗證 HTML。這通常涉及到使用 `TrustedTypePolicy` 來定義一個策略，然後使用這個策略來創建 TrustedHTML 物件。

### 詳細信息
1. **創建 TrustedTypePolicy**:
   使用 `TrustedTypes.createPolicy()` 方法來創建一個新的 TrustedTypePolicy。
   
   ```javascript
   const policy = TrustedTypes.createPolicy('myPolicy', {
       createHTML: (input) => {
           // 可以在這裡進行輸入的驗證和轉義
           return input; // 返回經過處理的 HTML
       }
   });
   ```

2. **生成 TrustedHTML**:
   使用創建的策略來生成 TrustedHTML 物件。
   
   ```javascript
   const trustedHTML = policy.createHTML('<div>安全的內容</div>');
   ```

3. **插入 TrustedHTML**:
   將生成的 TrustedHTML 插入到 DOM 中。
   
   ```javascript
   document.body.innerHTML = trustedHTML;
   ```

## 範例
以下是一個基本的使用範例：

```javascript
// 創建 TrustedTypePolicy
const policy = TrustedTypes.createPolicy('examplePolicy', {
    createHTML: (input) => {
        return input; // 假設這裡已經進行了正確的處理
    }
});

// 使用 TrustedTypePolicy 生成 TrustedHTML
const safeHTML = policy.createHTML('<h1>這是一個安全的標題</h1>');

// 將 TrustedHTML 插入到網頁中
document.getElementById('content').innerHTML = safeHTML;
```

## 解釋
- **常見問題**:
  - 未經妥善處理的用戶輸入可能仍然存在 XSS 漏洞。因此，在 `createHTML` 方法中，應該始終對輸入進行適當的清理和驗證。
  - 確保在使用 TrustedTypes 時，所有插入的 HTML 都要通過創建的政策進行處理。

- **注意事項**:
  - TrustedHTML 只是一種防護措施，並不替代其他安全實踐，如對用戶輸入的驗證和轉義。
  - 目前並非所有瀏覽器都支持 Trusted Types，因此在使用時需要考慮向後兼容性。

## 一句總結
TrustedHTML 是一種用於 JavaScript 的安全 HTML 處理機制，旨在防止 XSS 攻擊，確保僅插入信任的 HTML 內容。