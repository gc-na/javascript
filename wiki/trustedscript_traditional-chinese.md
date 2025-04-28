<!--
Meta Description: # TrustedScript：JavaScript中的安全腳本概念 ## 摘要 TrustedScript 是一種安全機制，旨在防止在 JavaScript 應用程序中執行潛在危險的腳本代碼。它通過限制可執行的代碼範圍來提高應用程序的安全性。 ## 文檔 ### 目的 TrustedScript ...
Meta Keywords: trustedscript, javascript, api, trusted, types
-->

# TrustedScript：JavaScript中的安全腳本概念

## 摘要
TrustedScript 是一種安全機制，旨在防止在 JavaScript 應用程序中執行潛在危險的腳本代碼。它通過限制可執行的代碼範圍來提高應用程序的安全性。

## 文檔
### 目的
TrustedScript 主要用於保護應用程序不受跨站腳本攻擊（XSS）影響。它確保只有被信任的腳本可以執行，從而降低不安全代碼的風險。

### 使用方法
在 JavaScript 中，TrustedScript 通常與其他安全 API 共同使用，例如 Trusted Types。這些 API 提供了一種機制來創建和管理受信任的腳本對象，並在應用程序中有效地使用它們。

### 詳細信息
- **創建 TrustedScript**: 通常使用 Trusted Types API 的 `createPolicy` 方法來創建一個新的政策。該政策能夠生成 TrustedScript 對象。
- **執行 TrustedScript**: 只有通過受信任的策略創建的 TrustedScript 才能被執行，這樣可以防止不受信任的內容進入應用程序的執行環境。

## 示例
以下是 TrustedScript 的基本用法示例：

```javascript
// 創建一個 Trusted Types 政策
const policy = trustedTypes.createPolicy("default", {
    createScript: (script) => {
        return script; // 返回受信任的腳本
    }
});

// 使用政策創建 TrustedScript
const trustedScript = policy.createScript("alert('Hello, World!');");

// 安全執行 TrustedScript
eval(trustedScript); // 這樣執行是安全的
```

## 解釋
- **常見陷阱**: 在使用 TrustedScript 時，開發人員應注意確保所有創建的腳本都來自可信來源。若未經驗證的內容被傳遞給 TrustedScript，則可能導致安全漏洞。
- **注意事項**: 當使用 `eval` 或其他執行方法時，應小心操作，因為若處理不當，仍可能導致 XSS 攻擊。

## 一句話總結
TrustedScript 是一種保護 JavaScript 應用程序免受不安全代碼影響的安全機制，通過限制可執行腳本的來源以提高安全性。