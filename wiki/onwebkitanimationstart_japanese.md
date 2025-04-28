<!--
Meta Description: # onwebkitanimationstart: JavaScriptでのアニメーションイベントの開始 ## 概要 `onwebkitanimationstart`は、CSSアニメーションがWebKitブラウザ（主にSafari）で開始されたときに発生するイベントです。このイベントを利用することで...
Meta Keywords: onwebkitanimationstart, animatedelement, event, style, background
-->

# onwebkitanimationstart: JavaScriptでのアニメーションイベントの開始

## 概要
`onwebkitanimationstart`は、CSSアニメーションがWebKitブラウザ（主にSafari）で開始されたときに発生するイベントです。このイベントを利用することで、アニメーションが始まったタイミングで特定の処理を実行することができます。

## ドキュメント
### 目的
`onwebkitanimationstart`イベントは、CSSアニメーションが開始された瞬間をキャッチし、JavaScriptでアクションをトリガーするために使用されます。このイベントは、アニメーションの開始時にさまざまな処理を行いたい場合に非常に便利です。

### 使用法
このイベントは、HTML要素のプロパティとして設定されます。以下のように、特定の要素に対してイベントリスナーを追加することで使用します。

```javascript
const element = document.getElementById('animatedElement');
element.onwebkitanimationstart = function(event) {
    console.log('アニメーションが開始されました:', event.animationName);
};
```

### 詳細
- **イベントオブジェクト**: `onwebkitanimationstart`イベントが発生すると、イベントオブジェクトが生成され、アニメーション名やアニメーションの持続時間などの情報を含みます。
- **ブラウザ互換性**: 主にWebKitベースのブラウザ（Safariなど）でサポートされています。ChromeやFirefoxなどの他のブラウザでは、標準の`animationstart`イベントを使用します。

## 例
以下は、`onwebkitanimationstart`を使用した基本的な例です。

```html
<div id="animatedElement" style="width: 100px; height: 100px; background: red; animation: example 2s;">
</div>

<script>
    document.getElementById('animatedElement').onwebkitanimationstart = function(event) {
        console.log('アニメーションが開始されました:', event.animationName);
    };
</script>

<style>
@keyframes example {
    from {background: red;}
    to {background: blue;}
}
</style>
```

このコードでは、`animatedElement`がアニメーションを開始すると、コンソールにアニメーション名が表示されます。

## 説明
- **共通の落とし穴**: `onwebkitanimationstart`はWebKitブラウザ専用のイベントであるため、他のブラウザで使用すると機能しない場合があります。そのため、通常は`animationstart`イベントも併用することが推奨されます。
- **アニメーションの遅延**: アニメーションが遅延されている場合、最初のトリガーが意図した通りに行われないことがあります。このため、アニメーションの状態を確認するロジックを追加することが重要です。

## 一文要約
`onwebkitanimationstart`は、WebKitブラウザでCSSアニメーションが開始された際に発生するイベントで、特定の処理を実行するために使用されます。