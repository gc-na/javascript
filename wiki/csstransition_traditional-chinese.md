<!--
Meta Description: # CSSTransition：JavaScript 中的 CSS 動畫過渡效果 ## 概述 CSSTransition 是一個由 React Transition Group 提供的組件，用於在 React 應用程序中實現 CSS 動畫效果的過渡。它通過簡單的 API 使開發者能夠輕鬆地管理元素的...
Meta Keywords: csstransition, css, react, transition, classnames
-->

# CSSTransition：JavaScript 中的 CSS 動畫過渡效果

## 概述
CSSTransition 是一個由 React Transition Group 提供的組件，用於在 React 應用程序中實現 CSS 動畫效果的過渡。它通過簡單的 API 使開發者能夠輕鬆地管理元素的進入和退出效果，提升用戶體驗。

## 文檔

### 目的
CSSTransition 的主要目的是為 React 應用中的元素添加過渡效果，當元素的狀態發生變化時（例如顯示或隱藏），可以自動應用 CSS 動畫類。

### 使用方法
要使用 CSSTransition，請首先安裝 `react-transition-group` 包：

```bash
npm install react-transition-group
```

然後在 React 組件中導入 CSSTransition：

```javascript
import { CSSTransition } from 'react-transition-group';
```

接下來，可以使用 CSSTransition 包裹要應用動畫的元素，並設置一些必要的屬性：

- `in`: 控制過渡的顯示狀態（boolean）。
- `timeout`: 設置過渡的持續時間（數字或對象）。
- `classNames`: 定義 CSS 類名的前綴，用於動畫效果。

### 詳細說明
CSSTransition 會根據 `in` 屬性的值自動添加和刪除 CSS 類。當 `in` 為 `true` 時，元素將顯示，並應用 `enter` 類；當 `in` 為 `false` 時，元素將隱藏，並應用 `exit` 類。

CSS 類的命名規則如下：

- `classNames-enter`: 元素進入時的初始狀態。
- `classNames-enter-active`: 元素進入時的過渡狀態。
- `classNames-exit`: 元素退出時的初始狀態。
- `classNames-exit-active`: 元素退出時的過渡狀態。

## 示例

以下是一個使用 CSSTransition 的基本示例：

```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css'; // 包含 CSS 動畫樣式

const MyComponent = () => {
  const [show, setShow] = useState(false);

  return (
    <div>
      <button onClick={() => setShow(!show)}>Toggle</button>
      <CSSTransition
        in={show}
        timeout={300}
        classNames="fade"
        unmountOnExit
      >
        <div className="fade">我會淡入和淡出</div>
      </CSSTransition>
    </div>
  );
};

export default MyComponent;
```

對應的 CSS 可以這樣寫：

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
在使用 CSSTransition 時，開發者可能會遇到以下常見問題：

- **未顯示過渡效果**：確保 `in` 屬性正確設置，並且 CSS 類名與 `classNames` 屬性一致。
- **過渡時間不一致**：確保 `timeout` 的設置與 CSS 中的過渡時間一致，否則會導致動畫效果不連貫。
- **性能考量**：對於頻繁更新的元素，使用過渡效果可能會影響性能，建議對過渡的頻率進行控制。

## 一句話總結
CSSTransition 是一個強大的 React 組件，能夠輕鬆地為元素添加 CSS 動畫過渡效果，從而提升用戶體驗。