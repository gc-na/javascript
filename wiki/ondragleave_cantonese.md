<!--
Meta Description: # JavaScript 事件：ondragleave 的全面指南 ## 概述 `ondragleave` 是一個用於 JavaScript 的事件，當拖曳的元素離開一個可放置的目標時觸發。此事件通常用於實現拖放功能，幫助用戶在網頁中進行文件上傳或元素移動等操作。 ## 文件 ### 目的 `ond...
Meta Keywords: ondragleave, dropzone, javascript, event, html
-->

# JavaScript 事件：ondragleave 的全面指南

## 概述
`ondragleave` 是一個用於 JavaScript 的事件，當拖曳的元素離開一個可放置的目標時觸發。此事件通常用於實現拖放功能，幫助用戶在網頁中進行文件上傳或元素移動等操作。

## 文件
### 目的
`ondragleave` 事件的主要目的是讓開發者能夠監控用戶在拖曳操作中，當拖曳物件離開目標元素時的行為。

### 用法
這個事件通常與拖曳 API 一起使用，並且可以通過 JavaScript 來監聽。你可以在任何 HTML 元素上設置 `ondragleave` 事件處理程序。

### 詳細信息
- **事件類型**：`DragEvent`
- **取消默認行為**：不需要，因為這個事件本身不會有默認行為要取消。
- **支持的瀏覽器**：現代瀏覽器均支持該事件，包括 Chrome、Firefox、Safari 和 Edge。

## 示例
以下是 `ondragleave` 的基本使用示例：

```html
<div id="dropzone" style="width: 300px; height: 200px; border: 2px dashed #ccc;">
  拖放文件到這裡
</div>

<script>
  const dropzone = document.getElementById('dropzone');

  dropzone.ondragleave = function(event) {
    event.preventDefault();
    console.log('拖曳物件已離開區域');
    dropzone.style.borderColor = '#ff0000'; // 改變邊框顏色
  };
</script>
```

在此示例中，當用戶的拖曳物件離開 `dropzone` 區域時，控制台會顯示信息，同時邊框顏色會變成紅色。

## 解釋
- **常見陷阱**：確保在使用 `ondragleave` 時，已經正確設置了 `draggable` 属性，否則不會觸發相關事件。
- **注意事項**：如果在 `ondragleave` 中不調用 `event.preventDefault()`，某些情況下可能會導致默認行為，影響後續的拖曳事件。

## 總結
`ondragleave` 事件是 JavaScript 中用於監控拖曳操作的重要工具，讓開發者能夠更好地控制用戶體驗。