<!--
Meta Description: # PerformanceLongTaskTiming：JavaScript 性能量測的關鍵指標 ## 概述 `PerformanceLongTaskTiming` 是 JavaScript 中的一個介面，專門用於測量執行長時間任務的性能，特別是在瀏覽器執行 JavaScript 代碼時，對於用戶體...
Meta Keywords: performancelongtasktiming, javascript, performanceobserver, entry, longtask
-->

# PerformanceLongTaskTiming：JavaScript 性能量測的關鍵指標

## 概述
`PerformanceLongTaskTiming` 是 JavaScript 中的一個介面，專門用於測量執行長時間任務的性能，特別是在瀏覽器執行 JavaScript 代碼時，對於用戶體驗的影響。它幫助開發者識別出可能影響頁面響應的長任務，從而優化應用程序的性能。

## 文件說明
### 目的
`PerformanceLongTaskTiming` 的主要目的是提供一種有效的方式來追蹤和量測 JavaScript 中的長任務。這些長任務通常是指執行時間超過 50 毫秒的任務，這可能導致頁面卡頓或無法及時響應用戶操作。

### 使用方式
當長任務發生時，`PerformanceLongTaskTiming` 將會收集該任務的性能數據，包括開始時間、結束時間和持續時間。這些性能數據可以通過 `PerformanceObserver` 監聽器來獲取。

### 詳細信息
- **屬性**：
  - `startTime`：任務開始執行的時間。
  - `duration`：任務持續的時間。
  - `name`：任務的名稱。
  - `entryType`：此性能條目的類型，對於長任務來說，將顯示為 'longtask'。

- **API 使用**：
  開發者可以通過 `PerformanceObserver` 來觀察長任務事件。設定觀察器後，當遇到長任務時，將觸發回調函數。

## 範例
以下是如何使用 `PerformanceLongTaskTiming` 的基本範例：

```javascript
// 創建 PerformanceObserver 來觀察長任務
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    console.log(`長任務名稱: ${entry.name}`);
    console.log(`開始時間: ${entry.startTime}`);
    console.log(`持續時間: ${entry.duration}`);
  }
});

// 開始觀察 'longtask' 類型的性能條目
observer.observe({ entryTypes: ['longtask'] });

// 模擬一個長任務
function longRunningTask() {
  const start = performance.now();
  while (performance.now() - start < 100) {
    // 模擬計算
  }
}

longRunningTask();
```

## 解釋
在使用 `PerformanceLongTaskTiming` 時，開發者需要注意以下幾點：

- **長任務的定義**：長任務是指執行時間長於 50 毫秒的任務，因此在設計應用時，應盡量避免這類任務。
- **性能影響**：長任務可能會導致頁面卡頓，影響用戶體驗，因此在開發過程中需定期檢查和優化長任務。
- **監聽器的使用**：確保正確設置 `PerformanceObserver` 以捕獲和處理長任務性能數據，並適當使用回調函數來收集數據。

## 總結
`PerformanceLongTaskTiming` 是一個重要的工具，幫助開發者追蹤和優化 JavaScript 中的長時間任務，以提升網頁性能和用戶體驗。