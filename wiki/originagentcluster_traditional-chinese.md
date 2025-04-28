<!--
Meta Description: # originAgentCluster: JavaScript 的新特性 ## 簡介 `originAgentCluster` 是一個 JavaScript 特性，旨在提升網頁的隱私性和安全性。此功能使開發人員能夠控制在不同的來源之間的資料共享，進而減少跨來源追蹤的風險。 ## 文檔 ### 目的...
Meta Keywords: originagentcluster, origin, cross, policy, javascript
-->

# originAgentCluster: JavaScript 的新特性

## 簡介
`originAgentCluster` 是一個 JavaScript 特性，旨在提升網頁的隱私性和安全性。此功能使開發人員能夠控制在不同的來源之間的資料共享，進而減少跨來源追蹤的風險。

## 文檔
### 目的
`originAgentCluster` 主要用於強化網頁應用的隔離性。透過這個特性，瀏覽器能夠在不同的來源間創建獨立的代理集群，從而降低資料洩露的可能性。

### 使用方式
要啟用 `originAgentCluster`，開發者需要在 HTML 文件的 `<head>` 部分中使用 `Cross-Origin-Embedder-Policy` 和 `Cross-Origin-Opener-Policy` 標頭來設置相關的政策。以下是基本的設置範例：

```html
<head>
    <meta http-equiv="Cross-Origin-Embedder-Policy" content="require-corp">
    <meta http-equiv="Cross-Origin-Opener-Policy" content="same-origin">
</head>
```

當這些政策被設置後，瀏覽器會自動將 `originAgentCluster` 屬性設置為 `true`，這意味著該頁面將獲得一個獨立的代理集群。

### 詳細說明
- `originAgentCluster` 是一個只讀屬性，當頁面啟用該特性時，屬性值將為 `true`，否則為 `false`。
- 當頁面在不同的來源之間進行交互時，`originAgentCluster` 的啟用可防止資料洩露，增強安全性。
- 這個特性對於需要在網絡應用中保護用戶隱私的情況尤其重要，例如金融服務或醫療應用。

## 範例
以下是如何檢查 `originAgentCluster` 的基本範例：

```javascript
if (window.originAgentCluster) {
    console.log("此頁面啟用了 originAgentCluster");
} else {
    console.log("此頁面未啟用 originAgentCluster");
}
```

在上面的範例中，開發者可以根據 `originAgentCluster` 的值來決定後續行為。

## 說明
### 常見陷阱與注意事項
- **瀏覽器支持**：並非所有瀏覽器都支持 `originAgentCluster`，在使用之前需確認目標瀏覽器的兼容性。
- **政策設置**：正確設置 `Cross-Origin-Embedder-Policy` 和 `Cross-Origin-Opener-Policy` 標頭至關重要，否則 `originAgentCluster` 將無法生效。
- **性能考量**：在某些情況下，啟用此特性可能會導致性能下降，特別是在需要大量跨來源請求的應用中。

## 一句總結
`originAgentCluster` 是一個增強網頁安全性和隱私性的 JavaScript 特性，透過隔離來源間的資料共享來降低潛在風險。