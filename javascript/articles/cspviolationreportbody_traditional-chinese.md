<!--
Meta Description: # CSPViolationReportBody：JavaScript中的內容安全政策違規報告體 ## 摘要 CSPViolationReportBody 是一個在 JavaScript 中用於捕捉和處理內容安全政策 (CSP) 違規報告的接口。它提供了一種安全的方式來接收和處理網站上發生的 CSP...
Meta Keywords: csp, cspviolationreportbody, report, uri, json
-->

# CSPViolationReportBody：JavaScript中的內容安全政策違規報告體

## 摘要
CSPViolationReportBody 是一個在 JavaScript 中用於捕捉和處理內容安全政策 (CSP) 違規報告的接口。它提供了一種安全的方式來接收和處理網站上發生的 CSP 違規事件，以便開發者能夠更好地保護應用程式安全。

## 文檔
CSP (Content Security Policy) 是一種安全功能，旨在防止各種網路攻擊，如跨站腳本攻擊 (XSS) 和數據注入。當 CSP 檢測到違規行為時，瀏覽器會生成一個違規報告，這些報告的內容可以通過 CSPViolationReportBody 接口來訪問。

### 主要用途
- 提供 CSP 違規事件的詳細信息，包括違規的類型、來源和時間戳。
- 允許開發者在後端進行進一步分析和處理，以改善應用程式的安全性。

### 使用方法
CSPViolationReportBody 在瀏覽器接收到 CSP 違規報告時自動被調用。開發者可以通過設置一個 endpoint，來接收這些報告。報告的內容將通過 JSON 格式提供，開發者可以解析這些數據以進行進一步的分析。

#### 接收 CSP 違規報告的範例
1. 在伺服器端設置一個接收 POST 請求的路由：
    ```javascript
    const express = require('express');
    const app = express();

    app.use(express.json());

    app.post('/csp-report', (req, res) => {
        const report = req.body;
        console.log('CSP 違規報告:', report);
        res.sendStatus(204);
    });

    app.listen(3000, () => {
        console.log('伺服器運行在 http://localhost:3000');
    });
    ```

2. 在 HTML 文件中設置 CSP 標頭，並指定報告 URI：
    ```html
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; report-uri /csp-report;">
    ```

## 示例
以下是一個簡單的 CSP 違規報告格式示例：
```json
{
  "csp-report": {
    "document-uri": "https://example.com/",
    "referrer": "",
    "blocked-uri": "https://malicious.example.com/",
    "violated-directive": "script-src 'self'",
    "original-policy": "default-src 'self'; script-src 'self'",
    "source-file": "https://example.com/some-script.js",
    "status-code": 200
  }
}
```

## 解釋
### 常見問題
- **報告未發送**：確保 CSP 標頭正確設置且報告 URI 是可訪問的。若 URI 錯誤或伺服器未運行，報告將無法發送。
- **JSON 解析錯誤**：在處理報告時，請確保使用正確的 JSON 解析方法，以避免解析錯誤。

### 附加注意事項
- CSPViolationReportBody 並非所有瀏覽器均支持，請檢查兼容性。
- 不同的 CSP 違規事件可能會生成不同的報告結構，開發者需根據實際情況進行適當處理。

## 單行摘要
CSPViolationReportBody 是用於接收和處理 JavaScript 中的內容安全政策違規報告的接口。