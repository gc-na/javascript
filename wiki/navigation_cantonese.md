<!--
Meta Description: # JavaScript 導航 (Navigation) 的全面指南 ## 簡介 在 JavaScript 中，導航是指用戶在網頁或應用程式中移動的方式。這包括使用 URL、歷史紀錄、以及瀏覽器的導航功能。正確的導航可以提升用戶體驗，讓用戶更容易找到他們需要的信息。 ## 文檔 ### 目的 Jav...
Meta Keywords: url, window, history, javascript, location
-->

# JavaScript 導航 (Navigation) 的全面指南

## 簡介
在 JavaScript 中，導航是指用戶在網頁或應用程式中移動的方式。這包括使用 URL、歷史紀錄、以及瀏覽器的導航功能。正確的導航可以提升用戶體驗，讓用戶更容易找到他們需要的信息。

## 文檔
### 目的
JavaScript 的導航功能主要用於控制瀏覽器的歷史紀錄、URL 變更和頁面重新加載。它可以通過 `window.location` 和 `window.history` 物件來實現。

### 使用方法
- **window.location**: 此物件用於獲取或設定當前頁面的 URL。可以讀取當前 URL，或將用戶重定向至新的 URL。
  
- **window.history**: 此物件用於操作瀏覽器的歷史紀錄。可以使用 `history.back()`、`history.forward()` 和 `history.go()` 等方法來導航。

### 詳細說明
- `window.location.href`: 讀取或設置當前頁面的完整 URL。
- `window.location.replace()`: 替換當前頁面而不在歷史紀錄中留下記錄。
- `history.pushState()`: 用於添加新的歷史紀錄條目，適用於單頁應用程式。
- `history.popState()`: 用於處理歷史紀錄變更的事件。

## 示例
### 基本用法
```javascript
// 重新導向到新 URL
window.location.href = "https://www.example.com";

// 返回上一頁
window.history.back();

// 添加新歷史紀錄
window.history.pushState({ key: 'value' }, 'title', '/new-url');
```

## 解釋
在使用 JavaScript 導航時，開發者需注意以下幾點：
- 當使用 `window.location.replace()` 時，當前頁面不會保留在歷史紀錄中，用戶無法使用 "返回" 按鈕返回之前的頁面。
- 使用 `history.pushState()` 時，需確保正確管理狀態對象，以便在用戶返回時能夠正確恢復之前的狀態。
- 過度使用 URL 變更可能會影響 SEO，需謹慎調整。

## 一句總結
JavaScript 的導航功能是管理網頁或應用程式用戶體驗的重要工具，能夠有效控制 URL 和歷史紀錄。