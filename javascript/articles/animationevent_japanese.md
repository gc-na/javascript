<!--
Meta Description: # AnimationEvent: JavaScriptにおけるアニメーションイベント ## 概要 `AnimationEvent`は、CSSアニメーションの開始、終了、または中断をトリガーするイベントを表します。このイベントを使用することで、アニメーションの状態を検知し、JavaScriptでアニ...
Meta Keywords: animationevent, event, box, addeventlistener, animationname
-->

# AnimationEvent: JavaScriptにおけるアニメーションイベント

## 概要
`AnimationEvent`は、CSSアニメーションの開始、終了、または中断をトリガーするイベントを表します。このイベントを使用することで、アニメーションの状態を検知し、JavaScriptでアニメーションに対するリアクションを実装できます。

## ドキュメンテーション
### 目的
`AnimationEvent`は、CSSアニメーションのライフサイクルを管理するために設計されています。このイベントは、アニメーションが開始されたとき、終了したとき、または中断されたときに発生します。

### 使用法
`AnimationEvent`は、`addEventListener`メソッドを使用してリスナーを追加することで活用されます。アニメーションのイベントには、以下の3つがあります。

- `animationstart`: アニメーションが開始したときに発生します。
- `animationend`: アニメーションが終了したときに発生します。
- `animationiteration`: アニメーションが1回のサイクルを完了したときに発生します。

### イベントプロパティ
- `animationName`: トリガーされたアニメーションの名前を返します。
- `elapsedTime`: アニメーションの開始からの経過時間（秒）を返します。

## 例
以下は、`AnimationEvent`を使用した基本的な例です。

```javascript
const box = document.querySelector('.box');

box.addEventListener('animationstart', (event) => {
    console.log(`アニメーションが開始しました: ${event.animationName}`);
});

box.addEventListener('animationend', (event) => {
    console.log(`アニメーションが終了しました: ${event.animationName}`);
});

box.addEventListener('animationiteration', (event) => {
    console.log(`アニメーションが繰り返されました: ${event.animationName}`);
});
```

## 説明
`AnimationEvent`を使用する際の一般的な注意点として、以下の点が挙げられます。

- CSSアニメーションが正しく設定されていないと、イベントが発生しないことがあります。アニメーション名やプロパティを確認してください。
- イベントが発生するタイミングを考慮する必要があります。例えば、アニメーションが非常に短い場合、`animationend`イベントが発生する前に次のアニメーションが開始されることがあります。
- ブラウザの互換性に注意してください。特に古いバージョンのブラウザでは、アニメーションイベントがサポートされていない場合があります。

## 一文要約
`AnimationEvent`は、CSSアニメーションのライフサイクルを管理し、アニメーションの状態をJavaScriptで操作するためのイベントです。