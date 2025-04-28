<!--
Meta Description: # JavaScript onreset 事件：用於表單重置的詳細指南 ## 簡介 `onreset` 是一個 JavaScript 事件處理器，用於捕捉表單重置事件。當用戶點擊表單中的重置按鈕時，該事件會被觸發。這個功能在處理用戶輸入和表單狀態管理時非常有用。 ## 文檔 ### 目的 `onre...
Meta Keywords: onreset, javascript, input, type, form
-->

# JavaScript onreset 事件：用於表單重置的詳細指南

## 簡介
`onreset` 是一個 JavaScript 事件處理器，用於捕捉表單重置事件。當用戶點擊表單中的重置按鈕時，該事件會被觸發。這個功能在處理用戶輸入和表單狀態管理時非常有用。

## 文檔
### 目的
`onreset` 事件的主要目的是在表單被重置時執行特定的 JavaScript 代碼。這可以用來清理任何額外的操作或通知用戶表單已被重置。

### 用法
要使用 `onreset` 事件，你可以將其直接設置在 HTML 表單元素上，或者通過 JavaScript 代碼在表單加載後進行註冊。

#### HTML 示例
```html
<form onreset="handleReset()">
  <input type="text" name="username" placeholder="用戶名稱">
  <input type="password" name="password" placeholder="密碼">
  <input type="reset" value="重置">
</form>
```

#### JavaScript 示例
```javascript
document.getElementById("myForm").onreset = function() {
  alert("表單已重置！");
};
```

## 示例
以下是幾個 `onreset` 事件的基本使用示例：

### 示例 1：基本重置
```html
<form id="myForm" onreset="alert('表單已重置！')">
  <input type="text" name="email" placeholder="電子郵件">
  <input type="reset" value="重置">
</form>
```

### 示例 2：清理操作
```html
<form id="myForm">
  <input type="text" name="name" placeholder="姓名">
  <input type="reset" value="重置">
</form>

<script>
  document.getElementById("myForm").onreset = function() {
    console.log("重置操作完成");
  };
</script>
```

## 解釋
使用 `onreset` 時需要注意以下幾點：
- **事件順序**：`onreset` 事件在表單的所有字段被重置之前觸發。
- **自動行為**：重置事件不會自動保存用戶輸入的數據，如果需要在重置後保留某些數據，需自行實現。
- **兼容性**：確保在所有主要瀏覽器中進行測試，因為某些舊版瀏覽器可能對事件的支持有限。

## 一句總結
`onreset` 是用於捕捉和處理表單重置事件的 JavaScript 事件處理器，幫助開發者在表單被重置時執行特定操作。