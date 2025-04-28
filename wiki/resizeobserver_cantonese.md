<!--
Meta Description: # ResizeObserver：JavaScript 中的動態元素大小監測器 ## 簡介 `ResizeObserver` 是一個 JavaScript API，用於監測 DOM 元素的大小變化。當元素的寬度或高度改變時，`ResizeObserver` 會觸發回調函數，讓開發者可以根據大小變化進...
Meta Keywords: resizeobserver, observer, box, javascript, const
-->

# ResizeObserver：JavaScript 中的動態元素大小監測器

## 簡介
`ResizeObserver` 是一個 JavaScript API，用於監測 DOM 元素的大小變化。當元素的寬度或高度改變時，`ResizeObserver` 會觸發回調函數，讓開發者可以根據大小變化進行相應的操作。

## 文檔
### 目的
`ResizeObserver` 的主要目的是提供一種高效的方式來監測和響應元素的尺寸變化，特別是在需要根據元素大小調整布局或樣式的情況下。

### 用法
`ResizeObserver` 的使用非常簡單，以下是基本的使用步驟：

1. **創建一個 `ResizeObserver` 實例**：
   ```javascript
   const observer = new ResizeObserver((entries) => {
       for (let entry of entries) {
           console.log('Size changed:', entry.contentRect.width, entry.contentRect.height);
       }
   });
   ```

2. **觀察一個或多個 DOM 元素**：
   ```javascript
   const element = document.querySelector('#myElement');
   observer.observe(element);
   ```

3. **停止觀察**：
   ```javascript
   observer.unobserve(element);
   ```

### 詳細說明
- **entries**: 當元素大小改變時，`ResizeObserver` 會傳遞一個 `ResizeObserverEntry` 的列表給回調函數。每個條目都包含了元素的最新尺寸信息。
- **contentRect**: 每個 `ResizeObserverEntry` 物件都有一個 `contentRect` 屬性，這是一個 `DOMRectReadOnly` 物件，包含元素的寬度和高度。
- **性能考量**: `ResizeObserver` 是基於事件驅動的，能有效減少因為頻繁的 DOM 操作而引起的性能問題。

## 範例
以下是一些基本的使用示例：

### 例子 1：監測元素大小
```javascript
const box = document.querySelector('.box');
const observer = new ResizeObserver(entries => {
    entries.forEach(entry => {
        console.log(`元素大小變化為：寬度 ${entry.contentRect.width}, 高度 ${entry.contentRect.height}`);
    });
});
observer.observe(box);
```

### 例子 2：停止監測
```javascript
const box = document.querySelector('.box');
const observer = new ResizeObserver(() => {
    console.log('Box size changed');
});
observer.observe(box);

// 停止監測
observer.unobserve(box);
```

## 解釋
- **常見陷阱**：`ResizeObserver` 不會在元素的尺寸變化未實際影響到其可見範圍時觸發。這意味著如果你只是改變了內容而未改變元素的外部尺寸，則不會調用回調。
- **回調頻率**：在短時間內多次改變元素大小可能會導致回調被多次調用，開發者需注意性能問題。
- **瀏覽器兼容性**：在使用 `ResizeObserver` 前，請確認目標瀏覽器的兼容性，儘管大多數現代瀏覽器已經支持。

## 一句總結
`ResizeObserver` 是一個強大的工具，可以用來即時監測和響應 DOM 元素的尺寸變化，提升用戶體驗和界面動態性。