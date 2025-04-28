<!--
Meta Description: # onanimationend: JavaScriptのアニメーション終了イベント ## 概要 `onanimationend`は、CSSアニメーションが終了した際に発火するイベントです。JavaScriptを用いてアニメーションの完了を検知し、後続の処理を実行する際に利用されます。 ## ドキュ...
Meta Keywords: onanimationend, element, animated, イベントは, event
-->

# onanimationend: JavaScriptのアニメーション終了イベント

## 概要
`onanimationend`は、CSSアニメーションが終了した際に発火するイベントです。JavaScriptを用いてアニメーションの完了を検知し、後続の処理を実行する際に利用されます。

## ドキュメンテーション
### 目的
`onanimationend`イベントは、CSSアニメーションの完了をトリガーとして、特定の処理を行うために使用されます。これにより、アニメーションの終了後に要素のスタイルを変更したり、次のアニメーションを開始することができます。

### 使用法
`onanimationend`イベントは、HTML要素に対してJavaScriptのイベントリスナーを追加することで使用します。以下は基本的な使用方法です。

```javascript
const element = document.querySelector('.animated-element');

element.addEventListener('animationend', () => {
    console.log('アニメーションが終了しました');
});
```

### 詳細
- **イベントオブジェクト**: `onanimationend`イベントは、アニメーションの詳細を含むイベントオブジェクトを提供します。このオブジェクトには、アニメーションの名前や、どの要素で発火したかの情報が含まれています。
- **複数アニメーション**: 一つの要素に複数のアニメーションが適用されている場合、各アニメーションの終了を検知することができます。この場合、`event.animationName`をチェックして、どのアニメーションが終了したのかを判断できます。

## 例
以下は、`onanimationend`を使用した基本的な例です。

```html
<div class="animated-element"></div>

<style>
.animated-element {
    width: 100px;
    height: 100px;
    background-color: red;
    animation: fadeOut 2s;
}

@keyframes fadeOut {
    from { opacity: 1; }
    to { opacity: 0; }
}
</style>

<script>
const element = document.querySelector('.animated-element');

element.addEventListener('animationend', (event) => {
    console.log(`アニメーション "${event.animationName}" が終了しました`);
});
</script>
```

## 説明
- **ブラウザの互換性**: `onanimationend`は、主要なブラウザでサポートされていますが、古いブラウザでは動作しない可能性があります。使用する前に、対象ブラウザの互換性を確認することをお勧めします。
- **アニメーションの中断**: アニメーションが中断された場合、`onanimationend`イベントは発火しません。アニメーションを再開する場合は、アニメーションをリセットする必要があります。
- **CSSの設定**: アニメーションを正しく発火させるためには、CSSの`animation`プロパティが正しく設定されている必要があります。設定ミスがあると、イベントが発火しないことがあります。

## 一文の要約
`onanimationend`は、CSSアニメーションの完了を検知し、JavaScriptで後続の処理を実行するためのイベントです。