<!--
Meta Description: # WebGLQuery：在 JavaScript 中的高效渲染查詢 ## 概要 WebGLQuery 是一個用於 WebGL 的查詢對象，允許開發者在 GPU 渲染過程中進行性能測試和計算。這使得開發者可以更精確地測量渲染的時間和性能，從而優化應用程序的效率。 ## 文檔 ### 目的 WebGL...
Meta Keywords: const, query, webglquery, getqueryobject, time_elapsed
-->

# WebGLQuery：在 JavaScript 中的高效渲染查詢

## 概要
WebGLQuery 是一個用於 WebGL 的查詢對象，允許開發者在 GPU 渲染過程中進行性能測試和計算。這使得開發者可以更精確地測量渲染的時間和性能，從而優化應用程序的效率。

## 文檔
### 目的
WebGLQuery 的主要目的是提供一種方式來異步查詢渲染任務的結果，特別是在進行性能測試時。這對於需要高效渲染的應用程序，如遊戲和交互式圖形應用，尤為重要。

### 用法
要使用 WebGLQuery，您首先需要創建一個查詢對象。這可以通過 WebGLRenderingContext 的 `createQuery()` 方法來完成。然後，您可以使用 `beginQuery()` 和 `endQuery()` 方法來標記要測量的渲染過程。最後，使用 `getQueryObject()` 方法來獲取查詢結果。

#### 基本語法：
```javascript
const gl = canvas.getContext("webgl");
const query = gl.createQuery();
gl.beginQuery(gl.TIME_ELAPSED, query);
// 進行渲染操作
gl.endQuery(gl.TIME_ELAPSED);
const result = gl.getQueryObject(query, gl.QUERY_RESULT);
```

### 詳細說明
- **創建查詢對象**：使用 `createQuery()` 方法來創建查詢。
- **開始查詢**：使用 `beginQuery()` 方法開始測量，通常搭配一個查詢類型（如 `gl.TIME_ELAPSED`）。
- **結束查詢**：使用 `endQuery()` 方法結束測量。
- **獲取結果**：使用 `getQueryObject()` 方法獲取查詢結果。可查詢的內容包括渲染所需的時間或其他性能指標。

## 示例
### 基本範例
以下是一個簡單的示例，展示如何使用 WebGLQuery 測量渲染的時間：

```javascript
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

const query = gl.createQuery();

gl.beginQuery(gl.TIME_ELAPSED, query);
// 渲染操作
drawScene();
gl.endQuery(gl.TIME_ELAPSED);

const checkQuery = () => {
    const result = gl.getQueryObject(query, gl.QUERY_RESULT_AVAILABLE);
    if (result) {
        const time = gl.getQueryObject(query, gl.QUERY_RESULT);
        console.log(`渲染時間: ${time} 微秒`);
    } else {
        requestAnimationFrame(checkQuery);
    }
};

checkQuery();
```

## 解釋
### 常見陷阱
- **查詢狀態**：確保在查詢結束之前不嘗試獲取結果，否則將返回無效結果。
- **異步性**：查詢結果是異步的，因此需要在適當的時間檢查結果，以避免獲取到未完成的查詢數據。
- **性能開銷**：頻繁使用查詢可能會影響性能，應根據需求合理使用。

## 一行總結
WebGLQuery 是一個強大的工具，使開發者能夠在 WebGL 中高效地測量和優化渲染性能。