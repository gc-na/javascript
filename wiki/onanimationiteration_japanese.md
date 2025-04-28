<!--
Meta Description: # JavaScriptのonanimationiterationイベントについて ## 概要 `onanimationiteration`は、CSSアニメーションが1回のループを完了するたびに発火するイベントです。このイベントを使用することで、アニメーションの進行状況を監視したり、アニメーションの...
Meta Keywords: onanimationiteration, element, animated, html, width
-->

# JavaScriptのonanimationiterationイベントについて

## 概要
`onanimationiteration`は、CSSアニメーションが1回のループを完了するたびに発火するイベントです。このイベントを使用することで、アニメーションの進行状況を監視したり、アニメーションの各ループ終了時に特定のアクションを実行したりすることが可能です。

## ドキュメンテーション
### 目的
`onanimationiteration`イベントは、CSSアニメーションが1回のサイクルを完了した時に発生します。このイベントを利用することで、アニメーションの再実行や、アニメーションの状態を変更することができます。

### 使用法
`onanimationiteration`は、DOM要素に対して直接設定することができます。JavaScriptでの設定方法は以下の通りです。

```javascript
const element = document.querySelector('.animated-element');

element.addEventListener('animationiteration', (event) => {
    console.log('アニメーションが1回完了しました。');
});
```

### 詳細
- **イベントオブジェクト**: `onanimationiteration`イベントには、アニメーションの詳細を含むイベントオブジェクトが渡されます。このオブジェクトには、アニメーションの名前や、アニメーションの持続時間などの情報が含まれています。
- **CSSアニメーションとの連携**: このイベントは、CSSで設定されたアニメーションに基づいて発生します。アニメーションの定義には、`@keyframes`を使用してアニメーションの効果を指定します。

## 例
以下は、`onanimationiteration`を使用した基本的な例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onanimationiterationの例</title>
    <style>
        .animated-element {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: example 2s infinite;
        }

        @keyframes example {
            from { transform: translateX(0); }
            to { transform: translateX(100px); }
        }
    </style>
</head>
<body>
    <div class="animated-element"></div>
    <script>
        const element = document.querySelector('.animated-element');

        element.addEventListener('animationiteration', () => {
            console.log('アニメーションが1回完了しました。');
        });
    </script>
</body>
</html>
```

## 解説
- **共通の落とし穴**: `onanimationiteration`イベントは、アニメーションが無限にループする場合にも発生します。そのため、アニメーションが終了しない場合でも、イベントが繰り返し発生することを理解しておく必要があります。
- **サポートされていないブラウザ**: 古いブラウザでは、CSSアニメーション自体がサポートされていない場合があります。このため、`onanimationiteration`イベントも発生しません。最新のブラウザでのテストを推奨します。
- **アニメーション名の確認**: 複数のアニメーションがある場合、どのアニメーションが完了したのかを確認するには、イベントオブジェクトの`animationName`プロパティを利用します。

## 一文要約
`onanimationiteration`は、CSSアニメーションが1回のループを完了するたびに発火するJavaScriptイベントです。