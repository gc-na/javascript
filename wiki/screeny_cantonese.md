<!--
Meta Description: # JavaScript 中的 screenY 屬性：了解螢幕上 Y 軸的位移 ## 簡介 `screenY` 是一個 JavaScript 屬性，用於獲取當前視窗或文檔相對於使用者螢幕的垂直位置。此屬性常用於處理滑鼠事件，特別是在需要知道滑鼠位置時。 ## 文件說明 `screenY` 屬性屬於 ...
Meta Keywords: screeny, event, javascript, 軸位置, document
-->

# JavaScript 中的 screenY 屬性：了解螢幕上 Y 軸的位移

## 簡介
`screenY` 是一個 JavaScript 屬性，用於獲取當前視窗或文檔相對於使用者螢幕的垂直位置。此屬性常用於處理滑鼠事件，特別是在需要知道滑鼠位置時。

## 文件說明
`screenY` 屬性屬於 `MouseEvent` 物件，提供了滑鼠指標相對於螢幕的 Y 軸位置。這個值是從螢幕的頂部開始計算的，單位為像素。使用這個屬性，可以輕鬆地追蹤滑鼠的垂直位置，這在許多交互式應用程式中非常有用。

### 用法
`screenY` 屬性通常在滑鼠事件的回調函數中使用。以下是其基本語法：

```javascript
event.screenY
```

在這裡，`event` 是觸發的滑鼠事件物件，`screenY` 將返回一個整數，表示滑鼠相對於螢幕的 Y 軸位置。

### 詳細資訊
- **類型**：Number
- **可讀性**：只讀
- **適用版本**：所有現代瀏覽器均支持此屬性。

## 示例
以下是一些基本示例，顯示如何使用 `screenY` 屬性：

### 示例 1：獲取滑鼠 Y 軸位置
```javascript
document.addEventListener('mousemove', function(event) {
    console.log('滑鼠 Y 軸位置: ' + event.screenY);
});
```

### 示例 2：在滑鼠點擊時顯示位置
```javascript
document.addEventListener('click', function(event) {
    alert('滑鼠點擊的位置 Y 軸: ' + event.screenY);
});
```

## 解釋
在使用 `screenY` 時，有幾個常見的陷阱和注意事項：

1. **螢幕解析度**：`screenY` 的數值會受到使用者螢幕解析度的影響，因此在不同設備上可能會得到不同的結果。
2. **滾動條**：如果頁面有滾動條，`screenY` 的值不會受到影響，因為它是基於整個螢幕的位置，而不是視窗的可見範圍。
3. **跨瀏覽器兼容性**：雖然大多數現代瀏覽器都支持 `screenY`，但在某些舊版本或特定環境中可能存在不一致。

## 總結
`screenY` 是一個非常有用的屬性，能夠提供滑鼠在螢幕上的垂直位置，對於需要精確控制滑鼠事件的應用程式來說，這是一個重要的工具。