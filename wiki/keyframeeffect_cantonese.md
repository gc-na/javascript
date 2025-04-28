<!--
Meta Description: # KeyframeEffect：JavaScript動畫中的關鍵幀效果 ## 簡介 `KeyframeEffect` 是一個用於創建和控制 CSS 動畫的 JavaScript 物件。它允許開發者使用關鍵幀定義動畫的不同狀態，並為動畫提供更高的靈活性和控制。 ## 文檔 ### 目的 `Keyfr...
Meta Keywords: keyframeeffect, const, css, animation, keyframes
-->

# KeyframeEffect：JavaScript動畫中的關鍵幀效果

## 簡介
`KeyframeEffect` 是一個用於創建和控制 CSS 動畫的 JavaScript 物件。它允許開發者使用關鍵幀定義動畫的不同狀態，並為動畫提供更高的靈活性和控制。

## 文檔
### 目的
`KeyframeEffect` 主要用於在 Web 應用中創建動畫效果。它能夠幫助開發者在元素的不同狀態之間進行平滑過渡，增強用戶體驗。

### 用法
`KeyframeEffect` 通常與 `Animation` 接口一起使用。創建 `KeyframeEffect` 物件的基本語法如下：

```javascript
let keyframeEffect = new KeyframeEffect(
    targetElement, // 目標元素
    keyframes,     // 關鍵幀
    options        // 動畫選項
);
```

- **targetElement**：要應用動畫的 HTML 元素。
- **keyframes**：一個陣列，包含不同狀態的 CSS 屬性值。
- **options**：一個物件，用於設置動畫的持續時間、延遲等屬性。

### 詳細說明
`KeyframeEffect` 的關鍵幀定義可以是簡單的 CSS 屬性變化，也可以是複雜的多屬性變化。這使得開發者能夠創建出多樣化的動畫效果。以下是常用的選項：

- `duration`：動畫持續時間（以毫秒為單位）。
- `easing`：動畫過渡函數，控制速度的變化。
- `fill`：定義動畫結束後的狀態（例如：`forwards`, `backwards`, `both`）。

## 示例
以下是使用 `KeyframeEffect` 創建簡單動畫的示例：

```javascript
const box = document.querySelector('.box');

const keyframes = [
    { transform: 'translateY(0px)', opacity: 1 },
    { transform: 'translateY(-100px)', opacity: 0.5 },
    { transform: 'translateY(0px)', opacity: 1 }
];

const options = {
    duration: 1000,
    easing: 'ease-in-out',
    fill: 'forwards'
};

const effect = new KeyframeEffect(box, keyframes, options);
const animation = new Animation(effect, document.timeline);
animation.play();
```

這段代碼將一個元素從原位置向上移動並逐漸變得透明，然後回到原位。

## 解釋
在使用 `KeyframeEffect` 時，開發者需注意以下幾點：

- 確保目標元素在動畫開始時可見，否則可能看不到效果。
- 適當選擇 `easing` 函數，以達到理想的動畫效果。
- 了解 `fill` 屬性的影響，選擇正確的填充方式可以改變動畫結束後的外觀。

## 總結
`KeyframeEffect` 是一個強大的工具，能夠輕鬆創建複雜的 CSS 動畫，提升網頁的互動性和美觀性。