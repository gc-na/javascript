<!--
Meta Description: # CSSTransition：JavaScript中平滑過渡的關鍵技術 ## 簡介 CSSTransition 是一個用於在React應用程序中實現CSS過渡的組件，能夠簡化動畫效果的添加，提升用戶體驗。 ## 文檔 ### 目的 CSSTransition 主要用於在React中處理元素的進出動...
Meta Keywords: csstransition, fade, div, opacity, react
-->

# CSSTransition：JavaScript中平滑過渡的關鍵技術

## 簡介
CSSTransition 是一個用於在React應用程序中實現CSS過渡的組件，能夠簡化動畫效果的添加，提升用戶體驗。

## 文檔
### 目的
CSSTransition 主要用於在React中處理元素的進出動畫，通過添加和刪除CSS類來控制過渡效果，使動畫的實現更加簡單和直觀。

### 使用方法
要使用 `CSSTransition`，首先需要安裝 `react-transition-group` 包，然後可以在你的React組件中導入並使用。

#### 基本語法：
```javascript
import { CSSTransition } from 'react-transition-group';

<CSSTransition
  in={this.state.show}
  timeout={300}
  classNames="fade"
  unmountOnExit
>
  <div className="my-node">內容</div>
</CSSTransition>
```

### 參數說明：
- `in`：一個布爾值，表示是否顯示該組件。
- `timeout`：過渡持續時間，單位為毫秒。
- `classNames`：指定過渡時的CSS類名前綴。
- `unmountOnExit`：當組件隱藏時是否從DOM中卸載該組件。

## 示例
### 基本用法
下面是一個簡單的示例，展示如何使用 `CSSTransition` 來控制一個元素的顯示與隱藏效果。

```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css'; // 包含CSS過渡樣式

const Example = () => {
  const [show, setShow] = useState(false);

  return (
    <div>
      <button onClick={() => setShow(!show)}>
        {show ? '隱藏' : '顯示'}
      </button>
      <CSSTransition
        in={show}
        timeout={300}
        classNames="fade"
        unmountOnExit
      >
        <div className="fade-node">這是一個過渡效果的內容！</div>
      </CSSTransition>
    </div>
  );
};

export default Example;
```

### CSS樣式
```css
.fade-enter {
  opacity: 0;
}
.fade-enter-active {
  opacity: 1;
  transition: opacity 300ms;
}
.fade-exit {
  opacity: 1;
}
.fade-exit-active {
  opacity: 0;
  transition: opacity 300ms;
}
```

## 解釋
### 常見問題
1. **過渡效果不生效**：確保CSS類名與 `classNames` 屬性相匹配，並檢查是否正確設置了 `in` 屬性。
2. **不斷重複渲染**：避免在 `in` 屬性的計算中使用不穩定的狀態，這可能導致不必要的重新渲染。
3. **卸載問題**：如果設置了 `unmountOnExit`，請注意組件會在隱藏後從DOM中卸載，這可能影響其內部狀態。

## 總結
CSSTransition 是React中實現平滑過渡和動畫效果的重要組件，通過簡單的API使得動畫的管理變得高效和直觀。