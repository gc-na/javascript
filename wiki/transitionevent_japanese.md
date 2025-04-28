<!--
Meta Description: # TransitionEvent：JavaScriptにおけるトランジションの管理 ## 概要 `TransitionEvent`は、CSSトランジションの開始、終了、キャンセルを追跡するためのイベントです。JavaScriptを使用して、トランジションの進行状況を監視し、アニメーションを制御する...
Meta Keywords: transitionevent, element, event, propertyname, transitionend
-->

# TransitionEvent：JavaScriptにおけるトランジションの管理

## 概要
`TransitionEvent`は、CSSトランジションの開始、終了、キャンセルを追跡するためのイベントです。JavaScriptを使用して、トランジションの進行状況を監視し、アニメーションを制御することができます。

## ドキュメンテーション
### 目的
`TransitionEvent`は、CSSトランジションが発生したときにブラウザが発行するイベントオブジェクトです。これにより、トランジションの状態を把握し、特定のアクションをトリガーすることが可能になります。

### 使用法
`TransitionEvent`は、`transitionstart`、`transitionend`、`transitioncancel`のイベントリスナーを通じて使用されます。これらのイベントは、要素のCSSプロパティが変更された際に発生します。

### プロパティ
- **propertyName**: トランジションが適用されたCSSプロパティの名前。
- **elapsedTime**: トランジションの経過時間（秒）。
- **pseudoElement**: トランジションが発生した擬似要素（例：`::before`や`::after`）。

## 例
以下は、`TransitionEvent`を使用した基本的な例です。

### 例1: トランジションの開始を検知する
```javascript
const element = document.querySelector('.box');

element.addEventListener('transitionstart', (event) => {
    console.log(`${event.propertyName}のトランジションが開始されました。`);
});

element.style.transition = 'transform 2s';
element.style.transform = 'translateX(100px)';
```

### 例2: トランジションの終了を検知する
```javascript
element.addEventListener('transitionend', (event) => {
    console.log(`${event.propertyName}のトランジションが終了しました。`);
});
```

### 例3: トランジションのキャンセルを検知する
```javascript
element.addEventListener('transitioncancel', (event) => {
    console.log(`${event.propertyName}のトランジションがキャンセルされました。`);
});
```

## 説明
`TransitionEvent`を使用する際の一般的な注意点：
- トランジションが開始される前にスタイルを変更すると、イベントが発生しないことがあります。
- 複数のトランジションが同時に発生する場合、`propertyName`を使用してどのトランジションが発生したのかを識別する必要があります。
- `transitionend`イベントは、トランジションが正常に終了した場合にのみ発生します。トランジションがキャンセルされた場合は、`transitioncancel`イベントが発生します。

## 一文要約
`TransitionEvent`は、JavaScriptでCSSトランジションの状態を管理し、アニメーションの制御を可能にするイベントオブジェクトです。