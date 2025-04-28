<!--
Meta Description: # DragEvent：JavaScript 拖曳事件詳細說明 ## 概述 DragEvent 是一個 JavaScript 事件，專門用於處理拖曳操作。透過這個事件，開發者可以在網頁上實現拖放功能，提升用戶體驗。 ## 文檔 ### 目的 DragEvent 主要用於監聽和處理用戶在網頁上拖曳物件...
Meta Keywords: event, dragevent, datatransfer, div, dropzone
-->

# DragEvent：JavaScript 拖曳事件詳細說明

## 概述
DragEvent 是一個 JavaScript 事件，專門用於處理拖曳操作。透過這個事件，開發者可以在網頁上實現拖放功能，提升用戶體驗。

## 文檔
### 目的
DragEvent 主要用於監聽和處理用戶在網頁上拖曳物件的操作。當用戶按住滑鼠並移動時，DragEvent 會被觸發，允許開發者執行特定的邏輯，如移動圖像或移動元素。

### 使用方法
DragEvent 主要涉及幾個關鍵事件：
- `dragstart`：當用戶開始拖曳元素時觸發。
- `drag`：在拖曳過程中持續觸發。
- `dragenter`：當拖曳的元素進入另一個可放置的元素時觸發。
- `dragover`：當拖曳的元素在可放置的元素上方時持續觸發。
- `dragleave`：當拖曳的元素離開可放置的元素時觸發。
- `drop`：當拖曳的元素在可放置的元素上放下時觸發。
- `dragend`：拖曳操作結束時觸發。

### 事件屬性
DragEvent 具有以下重要屬性：
- `dataTransfer`：這是一個 DataTransfer 物件，包含與拖曳操作相關的數據。
- `clientX` 和 `clientY`：當前滑鼠指標的位置。
- `screenX` 和 `screenY`：滑鼠指標相對於屏幕的位置。

## 範例
以下是 DragEvent 的基本用法示例：

### 示例 1：基本拖曳
```html
<div id="dragElement" draggable="true">拖曳我！</div>
<div id="dropZone" style="width: 200px; height: 200px; border: 1px solid black;">放置區</div>

<script>
  const dragElement = document.getElementById("dragElement");
  const dropZone = document.getElementById("dropZone");

  dragElement.addEventListener("dragstart", (event) => {
    event.dataTransfer.setData("text/plain", "這是拖曳的內容");
  });

  dropZone.addEventListener("dragover", (event) => {
    event.preventDefault(); // 允許放置
  });

  dropZone.addEventListener("drop", (event) => {
    const data = event.dataTransfer.getData("text/plain");
    dropZone.textContent = data; // 顯示拖曳的內容
  });
</script>
```

### 示例 2：拖曳圖像
```html
<img id="dragImage" src="image.png" draggable="true" alt="可拖曳圖像">
<div id="imageDropZone" style="width: 300px; height: 300px; border: 1px dashed gray;">放置圖像區</div>

<script>
  const dragImage = document.getElementById("dragImage");
  const imageDropZone = document.getElementById("imageDropZone");

  dragImage.addEventListener("dragstart", (event) => {
    event.dataTransfer.setData("text/uri-list", dragImage.src);
  });

  imageDropZone.addEventListener("dragover", (event) => {
    event.preventDefault();
  });

  imageDropZone.addEventListener("drop", (event) => {
    const imageUrl = event.dataTransfer.getData("text/uri-list");
    imageDropZone.innerHTML = `<img src="${imageUrl}" alt="拖曳的圖像">`;
  });
</script>
```

## 解釋
在使用 DragEvent 時，開發者需注意以下幾點：
- 必須在可拖曳的元素上設置 `draggable="true"` 屬性。
- `dragover` 事件的預設行為必須被阻止，才能允許放置操作。
- 在 `drop` 事件中，應使用 `dataTransfer.getData` 來獲取拖曳的數據。

常見的錯誤包括未阻止 `dragover` 事件的預設行為以及在 `drop` 事件中未正確處理數據。

## 一句總結
DragEvent 是一個強大的 JavaScript 事件，用於實現網頁中的拖曳和放置功能。