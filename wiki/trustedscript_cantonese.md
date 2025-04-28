<!--
Meta Description: # TrustedScript：JavaScript 中的可信腳本管理 ## 簡介 TrustedScript 是一種 JavaScript 的安全機制，旨在防止跨站腳本（XSS）攻擊，確保在應用程式中執行的腳本是可信的。這個功能特別適合處理動態生成的內容，能夠增強應用程式的安全性。 ## 文檔 #...
Meta Keywords: trustedscript, javascript, xss, 創建一個, createpolicy
-->

# TrustedScript：JavaScript 中的可信腳本管理

## 簡介
TrustedScript 是一種 JavaScript 的安全機制，旨在防止跨站腳本（XSS）攻擊，確保在應用程式中執行的腳本是可信的。這個功能特別適合處理動態生成的內容，能夠增強應用程式的安全性。

## 文檔
### 目的
TrustedScript 主要用於創建和管理被信任的腳本，讓開發者能夠安全地執行來自不安全來源的腳本。它提供了一個明確的界限，將不安全的內容與安全的內容區分開來。

### 使用方法
要使用 TrustedScript，開發者可以利用瀏覽器的 API，創建一個 TrustedScript 物件。以下是基本的創建過程：

1. 使用 `window.trustedTypes.createPolicy` 創建一個 Trusted Types 政策。
2. 使用該政策來生成 TrustedScript 物件。

### 詳細信息
TrustedScript 的使用必須遵循以下步驟：

1. **創建政策：**
   ```javascript
   const policy = trustedTypes.createPolicy('default', {
       createScript: (input) => {
           return input; // 返回一個 TrustedScript 物件
       }
   });
   ```

2. **生成 TrustedScript：**
   ```javascript
   const trustedScript = policy.createScript('console.log("這是一個安全的腳本");');
   ```

3. **執行 TrustedScript：**
   ```javascript
   eval(trustedScript);
   ```

這樣，只有通過 `createPolicy` 創建的 TrustedScript 才能被執行，從而降低 XSS 攻擊的風險。

## 示例
### 基本用法
以下是如何使用 TrustedScript 的一個簡單範例：

```javascript
// 創建一個 Trusted Types 政策
const policy = trustedTypes.createPolicy('examplePolicy', {
    createScript: (input) => {
        return input; // 返回一個 TrustedScript 物件
    }
});

// 創建一個 TrustedScript
const script = policy.createScript('alert("這是一個可信的警告！");');

// 執行 TrustedScript
eval(script);
```

## 解釋
### 常見問題
- **政策未創建：** 如果未創建 Trusted Types 政策，則無法生成 TrustedScript，這會導致錯誤。
- **不安全的輸入：** 直接使用未經處理的字符串來創建 TrustedScript 會引發安全問題，因此務必確保輸入的安全性。
- **瀏覽器支持：** 目前，並非所有瀏覽器都完全支持 Trusted Types，因此開發者應檢查兼容性。

### 附加說明
TrustedScript 是一種針對 XSS 攻擊的防禦措施，但開發者仍需保持警惕，並結合其他安全策略來確保應用程式的安全性。

## 一句話總結
TrustedScript 是一個用於創建和管理可信腳本的 JavaScript 安全機制，旨在防止 XSS 攻擊。