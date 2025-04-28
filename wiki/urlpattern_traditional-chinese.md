<!--
Meta Description: # URLPattern: JavaScript 中的 URL 模式匹配工具 ## 概述 `URLPattern` 是一個在 JavaScript 中用於匹配和解析 URL 的強大工具，旨在簡化 URL 路由和處理的過程。它提供了一種結構化的方式來匹配 URL，特別適用於 Web 應用開發中的路由功...
Meta Keywords: url, result, urlpattern, pathname, javascript
-->

# URLPattern: JavaScript 中的 URL 模式匹配工具

## 概述
`URLPattern` 是一個在 JavaScript 中用於匹配和解析 URL 的強大工具，旨在簡化 URL 路由和處理的過程。它提供了一種結構化的方式來匹配 URL，特別適用於 Web 應用開發中的路由功能。

## 文檔
`URLPattern` 旨在幫助開發者對 URL 進行模式匹配。這個 API 允許使用者定義一個模式，並檢查特定的 URL 是否符合該模式。這對於需要處理多個 URL 路徑的應用程序特別有用，能夠有效地解析和提取 URL 參數。

### 主要功能
- **模式匹配**：通過定義模式來檢查 URL。
- **參數提取**：自動從匹配的 URL 中提取參數。
- **易於使用**：簡單的 API 設計使其易於集成到現有的 JavaScript 應用中。

### 使用方法
要使用 `URLPattern`，首先需要創建一個模式實例，然後可以使用 `.test()` 方法來檢查 URL 的匹配情況。

```javascript
const pattern = new URLPattern({ pathname: '/users/:id' });
const result = pattern.test('/users/123');

if (result) {
    console.log(result.pathname.groups.id); // 輸出: 123
}
```

## 範例
以下是 `URLPattern` 的基本用法示例：

### 示例 1：基本匹配
```javascript
const pattern = new URLPattern({ pathname: '/products/:category/:id' });
const result = pattern.test('/products/electronics/456');

if (result) {
    console.log(result.pathname.groups.category); // 輸出: electronics
    console.log(result.pathname.groups.id); // 輸出: 456
}
```

### 示例 2：查找多個匹配
```javascript
const pattern = new URLPattern({ pathname: '/blog/:year/:month/:slug' });
const result = pattern.test('/blog/2023/10/my-first-post');

if (result) {
    console.log(result.pathname.groups.year); // 輸出: 2023
    console.log(result.pathname.groups.month); // 輸出: 10
    console.log(result.pathname.groups.slug); // 輸出: my-first-post
}
```

## 說明
使用 `URLPattern` 時需注意以下幾點：
- **匹配不成功**：如果 URL 不符合模式，`test` 方法將返回 `null`，需進行相應的錯誤處理。
- **模式定義**：模式中使用的參數名必須以冒號 `:` 開頭，否則將無法正確提取。
- **可選參數**：可以使用 `?` 來定義可選參數，但需熟悉正則表達式的語法。

## 一句總結
`URLPattern` 是一個用於匹配和解析 URL 的 JavaScript 工具，簡化了路由和參數提取的過程。