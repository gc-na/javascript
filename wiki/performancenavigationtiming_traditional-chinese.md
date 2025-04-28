<!--
Meta Description: # PerformanceNavigationTiming：JavaScript 性能導航時間 API ## 摘要 `PerformanceNavigationTiming` 是一個用於獲取有關網頁導航性能的詳細信息的 JavaScript API。它提供了有關頁面加載時間、重定向次數和導航類型等關...
Meta Keywords: performancenavigationtiming, navtiming, javascript, api, performance
-->

# PerformanceNavigationTiming：JavaScript 性能導航時間 API

## 摘要
`PerformanceNavigationTiming` 是一個用於獲取有關網頁導航性能的詳細信息的 JavaScript API。它提供了有關頁面加載時間、重定向次數和導航類型等關鍵性能指標的數據，幫助開發者優化網站性能。

## 文件說明
`PerformanceNavigationTiming` 是 `Performance` API 的一部分，主要用於評估和分析用戶的導航體驗。這個接口提供的數據可以幫助開發者理解頁面加載的速度和效率，從而做出相應的優化措施。

### 目的
`PerformanceNavigationTiming` 旨在提供一種方法，以便開發者可以獲得詳細的導航性能數據。這些數據包括：
- 瀏覽器重定向次數
- 網頁加載的總時間
- 解析 DOM 樹所需的時間
- 使用者的導航類型（例如，直接訪問、重載、後退等）

### 使用方法
使用 `PerformanceNavigationTiming` 非常簡單。以下是獲取該數據的基本步驟：

```javascript
const performanceData = performance.getEntriesByType("navigation")[0];
const navigationTiming = new PerformanceNavigationTiming(performanceData);
```

### 重要屬性
- `connectStart`：連接開始的時間戳。
- `connectEnd`：連接結束的時間戳。
- `domComplete`：DOM 完成的時間戳。
- `loadEventEnd`：加載事件結束的時間戳。
- `redirectCount`：重定向的次數。

## 示例
以下是如何使用 `PerformanceNavigationTiming` 來獲取導航性能數據的簡單示例：

```javascript
window.onload = function() {
    const navTiming = performance.getEntriesByType("navigation")[0];
    
    console.log("總加載時間: " + navTiming.loadEventEnd - navTiming.startTime + " 毫秒");
    console.log("重定向次數: " + navTiming.redirectCount);
    console.log("網頁類型: " + navTiming.type);
}
```

## 解釋
在使用 `PerformanceNavigationTiming` 時，有幾個常見的陷阱需要注意：
- 確保在頁面完全加載後再訪問性能數據，以免獲得不完整的數據。
- 不同瀏覽器對於性能測量的支持可能存在差異，需進行跨瀏覽器的測試。
- `PerformanceNavigationTiming` 只能在支持該 API 的瀏覽器中使用，如 Chrome、Firefox 和 Edge 等。

## 一句總結
`PerformanceNavigationTiming` 是一個強大的工具，用於分析和優化網頁的導航性能，幫助開發者提升用戶體驗。