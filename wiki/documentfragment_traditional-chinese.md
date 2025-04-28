<!--
Meta Description: # DocumentFragment：JavaScript 中的虛擬文件片段 ## 概要 `DocumentFragment` 是一個輕量級的容器，用於儲存並操作 HTML 內容，能有效提高 DOM 操作的性能，避免重複渲染。 ## 文檔說明 `DocumentFragment` 是一個特殊的 DO...
Meta Keywords: documentfragment, dom, document, fragment, javascript
-->

# DocumentFragment：JavaScript 中的虛擬文件片段

## 概要
`DocumentFragment` 是一個輕量級的容器，用於儲存並操作 HTML 內容，能有效提高 DOM 操作的性能，避免重複渲染。

## 文檔說明
`DocumentFragment` 是一個特殊的 DOM 節點，允許在內存中構建一個 DOM 樹，然後一次性將其添加到文件中。這樣可以減少對 DOM 的多次訪問，提高性能，特別是在處理大量元素時。

### 目的
使用 `DocumentFragment` 的主要目的是減少 DOM 操作的次數。每次對 DOM 的修改都會導致瀏覽器重繪，這會影響性能。透過 `DocumentFragment`，我們可以將多個元素先添加到虛擬節點中，然後一次性將其添加到實際的 DOM 中。

### 用法
1. 創建一個 `DocumentFragment` 實例：
   ```javascript
   const fragment = document.createDocumentFragment();
   ```

2. 在 `DocumentFragment` 中添加元素：
   ```javascript
   const div = document.createElement('div');
   div.textContent = 'Hello, World!';
   fragment.appendChild(div);
   ```

3. 將 `DocumentFragment` 添加到 DOM 中：
   ```javascript
   document.body.appendChild(fragment);
   ```

## 範例
### 基本用法示例

```javascript
// 創建 DocumentFragment
const fragment = document.createDocumentFragment();

// 創建並添加多個元素
for (let i = 0; i < 5; i++) {
    const p = document.createElement('p');
    p.textContent = `段落 ${i + 1}`;
    fragment.appendChild(p);
}

// 將 DocumentFragment 添加到 DOM
document.body.appendChild(fragment);
```

### 使用 DocumentFragment 提高性能
```javascript
const fragment = document.createDocumentFragment();
const list = document.createElement('ul');

for (let i = 0; i < 100; i++) {
    const li = document.createElement('li');
    li.textContent = `項目 ${i + 1}`;
    list.appendChild(li);
}

fragment.appendChild(list);
document.body.appendChild(fragment);
```

## 解釋
使用 `DocumentFragment` 時，有幾個常見的注意事項：
- `DocumentFragment` 本身不會顯示在 DOM 中，無法直接訪問或操作其內容。
- 一旦將 `DocumentFragment` 添加到 DOM，該片段內的所有子元素將被移動到目標元素中，並且不再存在於 `DocumentFragment` 中。
- 在使用 `DocumentFragment` 時，務必注意其內存使用，因為在處理大量元素時，雖然性能會提高，但仍需考慮瀏覽器的記憶體限制。

## 一句總結
`DocumentFragment` 是 JavaScript 中一個高效的工具，用於在內存中構建和操作 DOM 結構，從而提升性能。