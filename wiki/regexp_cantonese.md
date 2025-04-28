<!--
Meta Description: # JavaScript 正則表達式 (RegExp) 全面指南 ## 概述 正則表達式（RegExp）是 JavaScript 中一種強大的工具，用於進行字符串模式匹配和文本處理。它們允許開發者檢查字符串中是否存在特定模式、替換字符串中的部分內容，或從字符串中提取信息。 ## 文檔 ### 目的 ...
Meta Keywords: javascript, const, regexp, regex, pattern
-->

# JavaScript 正則表達式 (RegExp) 全面指南

## 概述
正則表達式（RegExp）是 JavaScript 中一種強大的工具，用於進行字符串模式匹配和文本處理。它們允許開發者檢查字符串中是否存在特定模式、替換字符串中的部分內容，或從字符串中提取信息。

## 文檔
### 目的
正則表達式的主要目的是提供一種靈活的方式來匹配、查找和操作字符串。透過正則表達式，開發者可以簡化許多字符串處理的任務。

### 使用方法
在 JavaScript 中，正則表達式可以使用兩種方式創建：
1. 使用字面量語法：
   ```javascript
   const regex = /pattern/flags;
   ```
2. 使用 `RegExp` 構造函數：
   ```javascript
   const regex = new RegExp('pattern', 'flags');
   ```

### 詳細信息
- **模式 (pattern)**：代表要匹配的字符串模式。
- **標誌 (flags)**：用於改變正則表達式的行為，常見的標誌包括：
  - `g`：全局匹配（不只匹配第一個）。
  - `i`：不區分大小寫。
  - `m`：多行匹配。

正則表達式提供了多種元字符和語法來幫助構建模式，例如：
- `.`：匹配任何單個字符。
- `*`：匹配前面的字符零次或多次。
- `+`：匹配前面的字符一次或多次。
- `?`：匹配前面的字符零次或一次。

## 示例
以下是一些基本的正則表達式用法示例：

1. 檢查字符串是否包含數字：
   ```javascript
   const regex = /\d/;
   console.log(regex.test("Hello123")); // true
   ```

2. 替換字符串中的所有空格：
   ```javascript
   const str = "Hello World";
   const newStr = str.replace(/\s/g, '-');
   console.log(newStr); // Hello-World
   ```

3. 提取電子郵件地址：
   ```javascript
   const emailRegex = /\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,7}\b/g;
   const text = "Contact us at support@example.com.";
   const emails = text.match(emailRegex);
   console.log(emails); // ["support@example.com"]
   ```

## 解釋
在使用正則表達式時，開發者經常會遇到以下常見問題：
- **正則表達式的性能問題**：複雜的正則表達式可能會導致性能下降，特別是在處理大型字符串時。盡量避免使用回溯過多的模式。
- **特殊字符的轉義**：某些字符在正則表達式中具有特殊意義（例如 `.` 和 `*`），如果需要匹配這些字符本身，應使用反斜杠（`\`）進行轉義。
- **測試時未使用全局標誌**：在進行多次匹配時，未使用全局標誌會導致只匹配到第一次的結果。

## 一句總結
正則表達式是 JavaScript 中一種靈活且強大的字符串處理工具，可用於模式匹配和文本操作。