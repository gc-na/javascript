<!--
Meta Description: # HashChangeEvent：JavaScript 中的 URL 哈希變更事件 ## 簡介 HashChangeEvent 是一個 JavaScript 事件，當 URL 的哈希部分（即 # 之後的部分）發生變更時觸發。這個事件對於單頁應用程序（SPA）特別有用，因為它可以在不重新加載頁面的情...
Meta Keywords: hashchangeevent, url, javascript, location, hash
-->

# HashChangeEvent：JavaScript 中的 URL 哈希變更事件

## 簡介
HashChangeEvent 是一個 JavaScript 事件，當 URL 的哈希部分（即 # 之後的部分）發生變更時觸發。這個事件對於單頁應用程序（SPA）特別有用，因為它可以在不重新加載頁面的情況下更新內容。

## 文檔
### 目的
HashChangeEvent 允許開發者在用戶瀏覽器的 URL 哈希變更時執行特定的 JavaScript 代碼。這使得應用程序能夠根據 URL 的不同狀態更新視圖或數據。

### 用法
要使用 HashChangeEvent，首先需要添加事件監聽器，然後在 URL 哈希變更時執行相應的邏輯。以下是基本的使用步驟：

1. 使用 `window.addEventListener` 註冊事件監聽器。
2. 在事件處理函數中，使用 `location.hash` 獲取當前的哈希值。

### 詳細信息
- **事件名稱**：`hashchange`
- **屬性**：
  - `newURL`：新哈希的完整 URL。
  - `oldURL`：舊哈希的完整 URL。

## 範例
以下是一個簡單的範例，展示如何使用 HashChangeEvent：

```javascript
window.addEventListener("hashchange", function() {
    console.log("新哈希值為：" + location.hash);
    // 在這裡可以根據新的哈希值更新內容
});

// 更改哈希值以觸發事件
location.hash = "new-section";
```

在上面的範例中，當哈希值改變時，控制台將輸出新的哈希值。

## 解釋
- **常見問題**：
  - **不支持的瀏覽器**：HashChangeEvent 在某些舊版瀏覽器上可能不被支持。請確保你的應用程序能夠處理這些情況。
  - **多次觸發**：在快速連續改變哈希值時，可能會導致事件多次觸發，因此在事件處理函數中應謹慎處理狀態。

- **注意事項**：在使用 HashChangeEvent 時，請確保對所有可能的哈希值變更進行完整的處理，以避免應用程序狀態不一致的問題。

## 總結
HashChangeEvent 是一個有用的事件，允許開發者在單頁應用中對 URL 哈希變更進行監聽和響應。