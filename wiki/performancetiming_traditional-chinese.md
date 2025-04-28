<!--
Meta Description: # PerformanceTiming：JavaScript 性能測試的關鍵工具 ## 概述 `PerformanceTiming` 是一個 Web API，提供了有關一個網頁從開始載入到完全呈現過程中的各項時間數據，幫助開發者分析和優化網頁性能。 ## 文檔 `PerformanceTiming`...
Meta Keywords: performancetiming, dom, timing, window, http
-->

# PerformanceTiming：JavaScript 性能測試的關鍵工具

## 概述
`PerformanceTiming` 是一個 Web API，提供了有關一個網頁從開始載入到完全呈現過程中的各項時間數據，幫助開發者分析和優化網頁性能。

## 文檔
`PerformanceTiming` 接口提供了許多屬性，這些屬性反映了不同階段的時間戳，例如網頁開始載入的時間、DOM 樹生成的時間以及所有資源加載完成的時間等。這些數據對於性能優化至關重要。

### 目的
`PerformanceTiming` 的主要目的是讓開發者能夠獲取網頁性能數據，進而分析載入時間、資源加載時間及其他性能指標，以提升用戶體驗。

### 使用方式
開發者可以通過 `window.performance.timing` 來存取這些性能數據。以下是主要屬性：

- `navigationStart`：導航開始的時間戳。
- `unloadEventStart`：卸載事件開始時間。
- `unloadEventEnd`：卸載事件結束時間。
- `redirectStart`：重定向開始時間。
- `redirectEnd`：重定向結束時間。
- `fetchStart`：HTTP 請求開始時間。
- `domainLookupStart`：DNS 查詢開始時間。
- `domainLookupEnd`：DNS 查詢結束時間。
- `connectStart`：TCP 連接開始時間。
- `connectEnd`：TCP 連接結束時間。
- `requestStart`：HTTP 請求開始時間。
- `responseEnd`：HTTP 響應結束時間。
- `domLoading`：DOM 載入開始時間。
- `domInteractive`：DOM 互動時間。
- `domContentLoadedEventStart`：DOM 內容加載事件開始時間。
- `domContentLoadedEventEnd`：DOM 內容加載事件結束時間。
- `loadEventStart`：載入事件開始時間。
- `loadEventEnd`：載入事件結束時間。

### 例子
以下是如何使用 `PerformanceTiming` 獲取性能數據的範例：

```javascript
window.onload = function() {
  var timing = window.performance.timing;
  var pageLoadTime = timing.loadEventEnd - timing.navigationStart;
  console.log('頁面加載時間: ' + pageLoadTime + ' 毫秒');
};
```

這段程式碼在頁面加載完成時計算從導航開始到載入事件結束的時間，並顯示在控制台。

## 解釋
使用 `PerformanceTiming` 時，有幾個常見的陷阱需要注意：

1. **時間戳的精確度**：所有時間戳都是相對於1970年1月1日的UTC時間。確保在計算時間時使用正確的單位（毫秒）。
2. **跨域影響**：如果你的網頁從其他域載入資源，某些屬性可能無法獲取，這會影響性能數據的完整性。
3. **非連續載入**：在單頁應用中，某些性能指標可能無法反映真正的載入時間，因為頁面並不是完全重新加載。

## 總結
`PerformanceTiming` 是一個強大的工具，讓開發者能夠深入分析網頁性能，從而優化用戶體驗。透過獲取和分析性能數據，可以有效提升網站的載入速度和響應時間。