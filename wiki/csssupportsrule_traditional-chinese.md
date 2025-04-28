<!--
Meta Description: # CSSSupportsRule：JavaScript中CSS支援規則的完整指南 ## 摘要 `CSSSupportsRule` 是一個在 JavaScript 中用來表達和檢查CSS特性支援的功能，允許根據瀏覽器對特定CSS功能的支援情況來動態調整樣式。 ## 文檔 `CSSSupportsRu...
Meta Keywords: css, supports, grid, csssupportsrule, javascript
-->

# CSSSupportsRule：JavaScript中CSS支援規則的完整指南

## 摘要
`CSSSupportsRule` 是一個在 JavaScript 中用來表達和檢查CSS特性支援的功能，允許根據瀏覽器對特定CSS功能的支援情況來動態調整樣式。

## 文檔
`CSSSupportsRule` 是 CSS 中的一個規則，主要用於條件性地應用樣式。這個規則可以讓開發者根據瀏覽器是否支持某些CSS特性來選擇性地啟用樣式。這對於需要後向相容性或者針對特定瀏覽器進行優化的情境特別有用。

### 用法
`CSSSupportsRule` 的語法如下：
```javascript
@supports (property: value) {
  /* CSS styles go here */
}
```
在 JavaScript 中，你可以使用 `CSS.supports()` 方法來檢查特定的CSS屬性和其值是否被支持。

### 詳細說明
- **屬性**：可以是任何有效的CSS屬性。
- **值**：應該是對應屬性的有效值。
- **組合**：可以使用 `and`、`or` 和 `not` 進行組合查詢。

例如：
```javascript
if (CSS.supports("display", "grid")) {
  // 瀏覽器支持 CSS Grid
}
```

## 示例
### 基本用法
```javascript
if (CSS.supports("display", "grid")) {
  document.body.classList.add("supports-grid");
} else {
  document.body.classList.add("no-grid");
}
```

### 使用 `@supports` 進行條件樣式
```css
@supports (display: grid) {
  .container {
    display: grid;
  }
}
```

## 解釋
- **常見陷阱**：需要確保使用的屬性和值是正確的，否則 `CSS.supports()` 會返回 `false`。
- **瀏覽器支援**：並非所有瀏覽器都支持所有CSS屬性，開發者應該檢查兼容性。
- **性能考量**：頻繁使用 `CSS.supports()` 可能影響性能，應謹慎使用。

## 一句話總結
`CSSSupportsRule` 是一個強大的工具，幫助開發者根據瀏覽器的CSS支援情況動態應用樣式。