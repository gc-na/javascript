<!--
Meta Description: # originAgentCluster: JavaScript 中的原始代理集群 ## 摘要 `originAgentCluster` 是一個 JavaScript 特性，旨在增強網頁的安全性與隱私性，透過隔離不同來源的網頁程式碼與資料，確保其不會互相干擾。 ## 文件 ### 目的 `origi...
Meta Keywords: originagentcluster, origin, http, html, agent
-->

# originAgentCluster: JavaScript 中的原始代理集群

## 摘要
`originAgentCluster` 是一個 JavaScript 特性，旨在增強網頁的安全性與隱私性，透過隔離不同來源的網頁程式碼與資料，確保其不會互相干擾。

## 文件
### 目的
`originAgentCluster` 是一個用於為網頁創建獨立代理的功能，這意味著每個來源（origin）都可以有自己的獨立環境，降低資料洩漏與安全風險。

### 使用方法
要使用 `originAgentCluster`，您需要在網頁的 HTML 中加入 `Origin-Agent-Cluster` HTTP 標頭。這樣可以告訴瀏覽器為該來源創建一個新的代理集群。

#### 基本語法：
```http
Origin-Agent-Cluster: ?1
```

### 詳細信息
啟用 `originAgentCluster` 的 HTTP 標頭後，瀏覽器會為該來源創建一個獨立的代理集群。這意味著即使是來自同一個網域的不同頁面或資源，它們之間也會被隔離，這樣可以防止不必要的資料共享和潛在的安全風險。這一特性特別適合於涉及敏感數據或需要高安全性的應用場景。

## 示例
以下是一個如何在服務器響應中使用 `originAgentCluster` 的範例：

```http
HTTP/1.1 200 OK
Content-Type: text/html
Origin-Agent-Cluster: ?1

<!DOCTYPE html>
<html>
<head>
    <title>示範頁面</title>
</head>
<body>
    <h1>歡迎來到我的網站</h1>
</body>
</html>
```

## 解釋
### 常見問題
1. **不支持情況**：並非所有瀏覽器都支持 `originAgentCluster`，在實現前請檢查瀏覽器的兼容性。
2. **性能影響**：創建獨立的代理集群可能會影響頁面的性能，特別是在高流量的應用中。
3. **錯誤配置**：如果 `Origin-Agent-Cluster` 標頭配置不正確，可能會導致安全性問題或功能無法正常運作。

### 附加注意事項
- 確保在每次 HTTP 響應中都正確設置 `Origin-Agent-Cluster` 標頭，以保持一致性。
- 在使用此特性時，應考慮應用的安全需求，避免不必要的風險。

## 一句話總結
`originAgentCluster` 是一個 JavaScript 特性，用於創建獨立的代理環境，以提高網頁的安全性與隱私性。