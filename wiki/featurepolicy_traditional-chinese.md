<!--
Meta Description: # FeaturePolicy：JavaScript中的功能政策 ## 概述 FeaturePolicy（功能政策）是一個網頁安全性技術，允許開發者控制網站中某些功能的可用性。透過FeaturePolicy，開發者可以限制或允許某些特性和API的使用，以提升網站的安全性和性能。 ## 文檔 ### ...
Meta Keywords: iframe, none, geolocation, self, html
-->

# FeaturePolicy：JavaScript中的功能政策

## 概述
FeaturePolicy（功能政策）是一個網頁安全性技術，允許開發者控制網站中某些功能的可用性。透過FeaturePolicy，開發者可以限制或允許某些特性和API的使用，以提升網站的安全性和性能。

## 文檔
### 目的
FeaturePolicy的主要目的是給予開發者對於網站上特定功能的控制權，這樣可以防止不必要的功能被濫用，並減少潛在的安全風險。

### 使用方法
FeaturePolicy可以透過HTTP響應標頭或HTML `iframe` 標籤的屬性來設置。開發者可以使用以下方法來配置功能政策：

1. **HTTP響應標頭**：
   ```
   Feature-Policy: geolocation 'self'; microphone 'none'
   ```

2. **HTML `iframe` 標籤**：
   ```html
   <iframe src="example.html" allow="geolocation; microphone 'none'"></iframe>
   ```

### 詳細信息
FeaturePolicy支持多種功能的控制，例如：地理位置（geolocation）、攝影機（camera）及麥克風（microphone）。開發者可以指定這些功能是僅限於同源（'self'）的使用，還是完全禁止（'none'）。

## 範例
以下是幾個基本的使用範例：

### 1. 設置HTTP響應標頭
```http
HTTP/1.1 200 OK
Feature-Policy: geolocation 'self'; camera 'none'
```

### 2. 在HTML中使用`iframe`設置功能政策
```html
<iframe src="child.html" allow="geolocation 'self'"></iframe>
```

### 3. 限制多個功能
```http
HTTP/1.1 200 OK
Feature-Policy: microphone 'none'; camera 'none'; vibrate 'self'
```

## 解釋
使用FeaturePolicy時，開發者可能會遇到一些常見的陷阱和注意事項：

- **不兼容的瀏覽器**：並非所有瀏覽器都完全支持FeaturePolicy。開發者應檢查目標瀏覽器的兼容性。
- **功能的嵌套**：在嵌套的`iframe`中，父框架的功能政策可能會影響子框架的行為。
- **錯誤的策略設置**：設置不正確的功能政策可能導致功能無法正常運行，因此要謹慎設置。

## 一句總結
FeaturePolicy是一種控制網頁功能使用的安全技術，能夠提升網站的安全性和性能。