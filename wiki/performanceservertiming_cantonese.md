<!--
Meta Description: # PerformanceServerTiming：提升JavaScript性能監測的關鍵工具 ## 簡介 PerformanceServerTiming 是一個用於在瀏覽器中測量伺服器響應時間的 API，幫助開發者更好地分析和優化網絡應用程序的性能。 ## 文檔 PerformanceServer...
Meta Keywords: performanceservertiming, http, api, server, timing
-->

# PerformanceServerTiming：提升JavaScript性能監測的關鍵工具

## 簡介
PerformanceServerTiming 是一個用於在瀏覽器中測量伺服器響應時間的 API，幫助開發者更好地分析和優化網絡應用程序的性能。

## 文檔
PerformanceServerTiming 是一個屬於 Performance API 的接口，允許開發者記錄伺服器響應的時間，並將這些數據與瀏覽器的性能計時器相結合。這對於需要優化後端性能的應用程序尤為重要。

### 目的
PerformanceServerTiming 的主要目的是讓開發者能夠捕捉和分析伺服器響應時間的詳細數據，以便進行性能優化。

### 使用方法
使用 PerformanceServerTiming，開發者可以通過在 HTTP 響應標頭中添加 `Server-Timing` 標頭來記錄伺服器的性能指標。每個指標可以包含名稱、持續時間和可選的描述。

#### 標頭格式：
```
Server-Timing: <metric-name>;dur=<duration>;desc="<description>"
```

### 詳細信息
- **metric-name**：指標的名稱，用於標識該性能數據。
- **duration**：指標持續時間，以毫秒為單位。
- **description**（可選）：對指標的描述，幫助開發者理解數據的含義。

當使用者請求資源時，瀏覽器會自動捕捉這些標頭，並將其包含在 Performance API 的性能數據中。

## 示例
以下是一個簡單的例子，展示了如何在 HTTP 響應中使用 PerformanceServerTiming：

```http
HTTP/1.1 200 OK
Content-Type: application/json
Server-Timing: db;dur=53.5;desc="Database query time", cache;dur=22.7;desc="Cache lookup time"

{
  "data": "example"
}
```

在這個例子中，`db` 和 `cache` 是兩個性能指標，分別顯示了數據庫查詢和緩存查找的持續時間。

## 解釋
在使用 PerformanceServerTiming 時，開發者需要注意以下幾點：
- 確保每個指標的名稱是唯一的，避免混淆。
- 適當使用描述來增強指標的可讀性。
- 不要過度使用此功能，因為過多的指標可能會影響性能數據的解析。
- 在某些情況下，可能會出現跨域問題，確保伺服器正確設置 CORS 標頭。

## 一句總結
PerformanceServerTiming 讓開發者能夠輕鬆捕捉伺服器響應時間，以便進行更深入的性能分析和優化。