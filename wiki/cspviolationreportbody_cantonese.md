<!--
Meta Description: # CSPViolationReportBody - 用於JavaScript的內容安全政策違規報告 ## 概述 CSPViolationReportBody 是一個在 JavaScript 中處理內容安全政策（CSP）違規報告的接口。它提供了有關安全策略違規的信息，幫助開發者診斷和修復安全問題。 ...
Meta Keywords: csp, cspviolationreportbody, uri, referrer, report
-->

# CSPViolationReportBody - 用於JavaScript的內容安全政策違規報告

## 概述
CSPViolationReportBody 是一個在 JavaScript 中處理內容安全政策（CSP）違規報告的接口。它提供了有關安全策略違規的信息，幫助開發者診斷和修復安全問題。

## 文檔
CSP（Content Security Policy）是一種網絡安全標準，用於防止跨站腳本攻擊（XSS）和數據注入攻擊。當緊急情況發生時，瀏覽器會生成 CSP 違規報告，並將其發送到指定的端點。

CSPViolationReportBody 提供了以下屬性來描述違規報告的詳細信息：

- `documentUri`: 觸發違規的文檔的 URI。
- `referrer`: 引用該文檔的來源 URI。
- `violatedDirective`: 違反的 CSP 指令。
- `effectiveDirective`: 生效的 CSP 指令。
- `originalPolicy`: 原始 CSP 政策。
- `blockedUri`: 被阻止的資源的 URI。
- `statusCode`: HTTP 狀態碼（如果適用）。

使用 CSPViolationReportBody 使開發者能夠檢查和分析 CSP 違規，以加強應用的安全性。

## 示例
以下是使用 CSPViolationReportBody 的基本範例：

```javascript
// 假設我們有一個處理 CSP 違規報告的 API
function handleCSPViolation(report) {
    console.log("Document URI: ", report.documentUri);
    console.log("Referrer: ", report.referrer);
    console.log("Violated Directive: ", report.violatedDirective);
    console.log("Blocked URI: ", report.blockedUri);
}

// 模擬 CSP 違規報告
const sampleReport = {
    documentUri: "https://example.com",
    referrer: "https://referrer.com",
    violatedDirective: "script-src",
    effectiveDirective: "script-src 'self'",
    originalPolicy: "default-src 'self'; script-src 'self';",
    blockedUri: "https://malicious.com/script.js",
    statusCode: 200
};

handleCSPViolation(sampleReport);
```

## 解釋
在使用 CSPViolationReportBody 時，開發者可能會遇到以下常見問題：

- **報告格式**: 確保從瀏覽器獲得的報告格式正確，否則解析時可能會出錯。
- **跨域問題**: 當報告來自不同的源時，請檢查 CORS 設置，以確保能夠正確接收和處理報告。
- **性能影響**: 過多的 CSP 違規報告可能會降低服務器性能，因此應合理配置 CSP。

## 一句總結
CSPViolationReportBody 是一個用於處理和分析內容安全政策違規報告的 JavaScript 接口，幫助開發者提升應用安全性。