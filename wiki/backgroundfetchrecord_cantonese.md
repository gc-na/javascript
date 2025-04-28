<!--
Meta Description: # BackgroundFetchRecord：JavaScript 背景擷取記錄的全面指南 ## 簡介 BackgroundFetchRecord 是一種 JavaScript API，旨在支持無縫的背景資料擷取，允許開發人員在應用程式運行時進行下載或上傳操作，而不會影響用戶體驗。這項技術特別適合...
Meta Keywords: backgroundfetchrecord, fetch, bgfetchrecord, console, javascript
-->

# BackgroundFetchRecord：JavaScript 背景擷取記錄的全面指南

## 簡介
BackgroundFetchRecord 是一種 JavaScript API，旨在支持無縫的背景資料擷取，允許開發人員在應用程式運行時進行下載或上傳操作，而不會影響用戶體驗。這項技術特別適合用於需要長時間進行資料處理的應用場景，例如大型檔案的下載或上傳。

## 文檔
### 目的
BackgroundFetchRecord 物件用於追蹤背景擷取的狀態和進度。它是 Background Fetch API 的一部分，能夠讓開發者輕鬆管理和監控在背景中進行的資料擷取任務。

### 使用方式
要使用 BackgroundFetchRecord，開發者需要先啟用 Background Fetch API，然後創建一個新的背景擷取請求。以下是創建 BackgroundFetchRecord 的過程：

1. **創建背景擷取請求**：使用 `navigator.backgroundFetch.fetch()` 方法來發起擷取請求。
2. **監控狀態**：使用 BackgroundFetchRecord 物件來檢查擷取的狀態和進度。
3. **處理結果**：根據擷取的結果進行後續處理，例如通知用戶或更新 UI。

### 詳細說明
BackgroundFetchRecord 物件提供了幾個重要的屬性和方法：
- **id**：擷取請求的唯一識別符。
- **status**：顯示擷取的當前狀態，如 "pending"、"in-progress" 或 "completed"。
- **uploadedBytes**：已上傳的字節數。
- **downloadedBytes**：已下載的字節數。
- **failureReason**：如果擷取失敗，則顯示失敗的原因。

## 範例
以下是使用 BackgroundFetchRecord 的基本示範：

```javascript
// 開始背景擷取
navigator.backgroundFetch.fetch("my-fetch", ["https://example.com/large-file.zip"])
  .then((bgFetchRecord) => {
    console.log("背景擷取已開始：", bgFetchRecord.id);

    // 監控擷取進度
    bgFetchRecord.addEventListener("progress", (event) => {
      console.log(`已下載：${bgFetchRecord.downloadedBytes} 字節`);
    });

    // 擷取完成
    bgFetchRecord.addEventListener("success", () => {
      console.log("擷取成功！");
    });

    // 擷取失敗
    bgFetchRecord.addEventListener("failure", (event) => {
      console.log("擷取失敗，原因：", event.reason);
    });
  })
  .catch((error) => {
    console.error("無法開始背景擷取：", error);
  });
```

## 解釋
使用 BackgroundFetchRecord 時，有一些常見的陷阱和注意事項：
- **瀏覽器支持**：並非所有瀏覽器都支持 Background Fetch API，因此在使用前必須檢查兼容性。
- **用戶授權**：背景擷取需獲得用戶的授權，不同的瀏覽器可能有不同的要求。
- **網絡狀態**：擷取任務可能會因為網絡不穩定而中斷，開發者需要考慮這種情況並妥善處理。

## 總結
BackgroundFetchRecord 是一個強大的工具，讓開發者能夠在 JavaScript 應用中輕鬆管理背景資料擷取任務。