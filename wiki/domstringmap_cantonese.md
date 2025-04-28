<!--
Meta Description: # DOMStringMap：JavaScript中的屬性存取方法 ## 摘要 DOMStringMap 是一種在 JavaScript 中用於操作 HTML 元素的資料結構，能夠存取以自定義資料屬性（data-*）形式儲存的資料。這種結構使開發者能夠方便地管理與操作這些資料屬性。 ## 文檔 DO...
Meta Keywords: data, dataset, domstringmap, javascript, html
-->

# DOMStringMap：JavaScript中的屬性存取方法

## 摘要
DOMStringMap 是一種在 JavaScript 中用於操作 HTML 元素的資料結構，能夠存取以自定義資料屬性（data-*）形式儲存的資料。這種結構使開發者能夠方便地管理與操作這些資料屬性。

## 文檔
DOMStringMap 是一個物件，通常與 HTML 元素的 `dataset` 屬性一起使用。這個物件可以透過 DOM 元素的 `dataset` 來訪問，並且為每一個以 `data-` 開頭的屬性提供一個對應的屬性名稱。它的主要目的是簡化 JavaScript 開發者對自定義資料屬性的訪問和操作。

### 用法
要使用 DOMStringMap，開發者需要在 HTML 中定義一個包含 `data-*` 屬性的元素。然後透過 JavaScript 可以輕鬆訪問這些屬性。

```html
<div id="example" data-name="John" data-age="30"></div>
```

在 JavaScript 中，你可以這樣訪問：

```javascript
const element = document.getElementById('example');
const data = element.dataset;

console.log(data.name); // 輸出: John
console.log(data.age);  // 輸出: 30
```

## 範例
這裡有一些示範如何使用 DOMStringMap 的基本範例：

### 範例 1：簡單的資料訪問
```html
<div id="user" data-role="admin" data-status="active"></div>
<script>
  const userElement = document.getElementById('user');
  console.log(userElement.dataset.role);   // 輸出: admin
  console.log(userElement.dataset.status);  // 輸出: active
</script>
```

### 範例 2：資料屬性更新
```html
<div id="settings" data-volume="50"></div>
<script>
  const settingsElement = document.getElementById('settings');
  settingsElement.dataset.volume = 75; // 更新資料
  console.log(settingsElement.dataset.volume); // 輸出: 75
</script>
```

## 說明
雖然 DOMStringMap 提供了一個方便的方式來管理資料屬性，但開發者在使用時仍需注意以下幾點：

1. **屬性名稱**：在 JavaScript 中，屬性名稱會自動轉換為小寫，並且將連字元（-）替換為駝峰式命名法。例如，`data-user-name` 在 `dataset` 中會變成 `userName`。

2. **數據類型**：DOMStringMap 中的所有值都是字串型別。如果需要其他數據類型（如數字或布林值），開發者需要手動轉換。

3. **瀏覽器相容性**：雖然大多數現代瀏覽器都支持 `dataset`，但在非常舊的瀏覽器中可能不支持，開發者應該考慮這一點。

## 總結
DOMStringMap 是一種方便的 JavaScript 資料結構，用於簡化對 HTML 元素自定義資料屬性的訪問和操作。