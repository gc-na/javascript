<!--
Meta Description: # IntersectionObserver：JavaScript 的可見性監察器 ## 簡介 IntersectionObserver 是一個強大的 JavaScript API，允許開發者異步監察元素的可見性變化，特別是在滾動或改變視口時。這使得性能優化和無縫的用戶體驗成為可能，特別是在實現懶加...
Meta Keywords: intersectionobserver, const, observer, javascript, callback
-->

# IntersectionObserver：JavaScript 的可見性監察器

## 簡介
IntersectionObserver 是一個強大的 JavaScript API，允許開發者異步監察元素的可見性變化，特別是在滾動或改變視口時。這使得性能優化和無縫的用戶體驗成為可能，特別是在實現懶加載和無限滾動等功能時。

## 文檔

### 目的
IntersectionObserver 的主要目的是提供一種有效的方法來監控一個或多個目標元素是否在其祖先元素或視口中可見。這可以幫助開發者在正確的時間觸發某些行為，例如加載圖片或顯示動畫。

### 使用方法
要使用 IntersectionObserver，開發者需要創建一個 IntersectionObserver 實例，然後通過 `observe` 方法監控特定的 DOM 元素。以下是其基本語法：

```javascript
const observer = new IntersectionObserver(callback, options);
observer.observe(targetElement);
```

- `callback`：當監察的元素進入或退出可見範圍時，該回調函數將被調用。
- `options`：一個可選的對象，包含以下屬性：
  - `root`：用來指定監察的視口，默認為瀏覽器的視口。
  - `rootMargin`：一個用於增加或減少根邊界的 CSS 樣式字串。
  - `threshold`：一個數字或數字數組，指定何時觸發回調。

### 詳細說明
在使用 IntersectionObserver 時，開發者需要注意以下幾點：
- 當你添加多個目標元素時，回調函數會接收一個包含所有已變化的目標的數組。
- 可以使用 `unobserve` 方法停止監控某個元素。
- 使用 `disconnect` 方法可以停止監察所有元素。

## 範例

### 基本使用範例

```javascript
const options = {
    root: null, // 默認視口
    rootMargin: '0px',
    threshold: 0.5 // 當元素至少有 50% 可見時觸發
};

const callback = (entries, observer) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            console.log('元素在視口中可見！');
            // 執行其他操作，如加載圖片
        }
    });
};

const observer = new IntersectionObserver(callback, options);
const target = document.querySelector('#targetElement');
observer.observe(target);
```

## 解釋
- **常見陷阱**：在設置 `threshold` 時要小心，因為數字範圍在 0 到 1 之間，0 代表任何可見性變化，1 代表元素完全可見。
- **性能問題**：雖然 IntersectionObserver 是性能優化的工具，但過多的監察元素可能會影響性能，因此應謹慎選擇要監察的元素。
- **支援性**：需要注意某些舊版瀏覽器可能不支援 IntersectionObserver，建議使用 polyfill 以確保兼容性。

## 一句話總結
IntersectionObserver 是一個優雅且高效的 API，用於監察元素的可見性變化，從而提升網頁性能與用戶體驗。