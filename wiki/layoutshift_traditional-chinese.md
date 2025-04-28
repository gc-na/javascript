<!--
Meta Description: # LayoutShift：了解 JavaScript 中的佈局偏移 ## 概要 LayoutShift 是一個與用戶體驗密切相關的概念，主要用於衡量網頁元素在載入過程中的變化。它是 Web Vitals 指標之一，旨在幫助開發者優化網頁的穩定性，減少不必要的佈局變更。 ## 文件說明 ### 目的...
Meta Keywords: layoutshift, performanceobserver, javascript, const, observer
-->

# LayoutShift：了解 JavaScript 中的佈局偏移

## 概要
LayoutShift 是一個與用戶體驗密切相關的概念，主要用於衡量網頁元素在載入過程中的變化。它是 Web Vitals 指標之一，旨在幫助開發者優化網頁的穩定性，減少不必要的佈局變更。

## 文件說明
### 目的
LayoutShift 的主要目的是評估在用戶瀏覽網頁時，頁面佈局的穩定性。當頁面內容動態變化，例如圖片延遲加載或廣告插入，這些變化會導致用戶界面的不穩定，進而影響用戶體驗。

### 使用方法
在 JavaScript 中，LayoutShift 一般通過 `LayoutShift` 事件來監測。開發者可以使用 `PerformanceObserver` 來觀察這些事件並記錄佈局偏移的數據。

### 詳細說明
- **PerformanceObserver**：這是一個用於監聽性能變化的 API，包括 LayoutShift 事件。
- **LayoutShift 類別**：每當佈局發生變化時，會生成一個 LayoutShift 實例，該實例包含了偏移量的信息。

```javascript
const observer = new PerformanceObserver((entryList) => {
    for (const entry of entryList.getEntries()) {
        console.log(`佈局偏移量: ${entry.value}`);
    }
});

observer.observe({ type: 'layout-shift', buffered: true });
```

## 例子
以下是如何使用 PerformanceObserver 來觀察 LayoutShift 事件的基本範例：

```javascript
const observer = new PerformanceObserver((list) => {
    list.getEntries().forEach((entry) => {
        console.log(`佈局偏移: ${entry.value}`);
    });
});

observer.observe({ type: 'layout-shift', buffered: true });

// 在網頁中觸發佈局變化，例如延遲加載圖片
setTimeout(() => {
    const img = document.createElement('img');
    img.src = 'path/to/image.jpg';
    document.body.appendChild(img);
}, 2000);
```

## 解釋
### 常見陷阱
- **未考慮用戶行為**：在設計網頁時，開發者應考慮用戶可能的操作，避免不必要的佈局變化。
- **圖片和廣告的延遲加載**：如果這些元素沒有預留空間，則可能導致顯著的佈局偏移。
  
### 其他注意事項
- LayoutShift 指標應與其他 Web Vitals 指標結合使用，例如 LCP（Largest Contentful Paint）和 CLS（Cumulative Layout Shift），以提供全面的性能評估。
- 對於高 LayoutShift 值的頁面，可以考慮使用佔位符或佈局預留技術，以提高用戶體驗。

## 單句總結
LayoutShift 是一個重要的性能指標，用於衡量網頁佈局的穩定性，幫助開發者提升用戶體驗。