<!--
Meta Description: # DOMTokenList：JavaScript 中的強大工具 ## 簡介 DOMTokenList 是一個在 JavaScript 中用於操作 DOM 元素的屬性（例如 classList）的對象。它提供了一組方法來添加、移除和檢查一組以空格分隔的字符串，即所謂的「標記」。 ## 文檔 ### ...
Meta Keywords: element, class, domtokenlist, classlist, javascript
-->

# DOMTokenList：JavaScript 中的強大工具

## 簡介
DOMTokenList 是一個在 JavaScript 中用於操作 DOM 元素的屬性（例如 classList）的對象。它提供了一組方法來添加、移除和檢查一組以空格分隔的字符串，即所謂的「標記」。

## 文檔
### 目的
DOMTokenList 主要用於操作元素的類名和其他基於空格的字符串屬性。這使得開發者可以方便地添加、刪除或檢查類名，從而控制元素的樣式和行為。

### 使用方法
DOMTokenList 通常通過以下屬性獲取：
- `element.classList`：返回一個 DOMTokenList，用於操作元素的 class 名稱。

### 主要方法
- `add(token)`：將指定的標記添加到列表中。
- `remove(token)`：從列表中移除指定的標記。
- `toggle(token)`：如果標記存在則移除，否則添加。
- `contains(token)`：檢查列表中是否包含指定的標記。
- `item(index)`：返回列表中指定索引的標記。
- `length`：返回列表中標記的數量。

## 示例
### 基本使用
```javascript
// 獲取元素
const element = document.querySelector('.my-element');

// 添加 class
element.classList.add('active');

// 檢查 class 是否存在
if (element.classList.contains('active')) {
    console.log('Class active 存在');
}

// 切換 class
element.classList.toggle('hidden');

// 移除 class
element.classList.remove('active');
```

## 解釋
在使用 DOMTokenList 時，開發者可能會遇到一些常見的陷阱：
- **大小寫敏感**：標記是大小寫敏感的，因此 `class` 和 `Class` 是不同的。
- **多個標記**：在添加標記時，可以一次添加多個標記，使用逗號分隔，例如 `element.classList.add('class1', 'class2')`。
- **空字符串**：在使用 `add` 或 `remove` 方法時，傳遞空字符串會導致錯誤，因此應避免這樣的情況。

## 總結
DOMTokenList 是 JavaScript 中操作元素標記的高效工具，提供了簡單的接口來增強 web 應用程序的動態交互性。