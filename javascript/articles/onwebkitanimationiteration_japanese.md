<!--
Meta Description: # onwebkitanimationiterationイベントについて - JavaScriptの使い方 ## 概要 `onwebkitanimationiteration`は、CSSアニメーションが1回の繰り返しを完了したときに発火するイベントです。このイベントは、アニメーションの進行状況を追跡...
Meta Keywords: onwebkitanimationiteration, html, element, event, width
-->

# onwebkitanimationiterationイベントについて - JavaScriptの使い方

## 概要
`onwebkitanimationiteration`は、CSSアニメーションが1回の繰り返しを完了したときに発火するイベントです。このイベントは、アニメーションの進行状況を追跡したり、アニメーションの効果をカスタマイズしたりする際に役立ちます。

## ドキュメンテーション
### 目的
`onwebkitanimationiteration`イベントは、WebKitブラウザ（主にSafari）でのCSSアニメーションが繰り返されたときに実行されるコールバックを指定するために使用されます。これにより、アニメーションの再生中に特定のアクションを実行したり、アニメーションの状態を変更したりすることが可能になります。

### 使用法
このイベントは、HTML要素に対して直接設定することができます。一般的には、次のようにイベントリスナーを追加します。

```javascript
element.onwebkitanimationiteration = function(event) {
    // アニメーションが繰り返された時の処理
    console.log('アニメーションが繰り返されました。');
};
```

### 詳細
- **イベント名**: `webkitAnimationIteration`
- **対応ブラウザ**: 主にWebKitベースのブラウザ（Safariなど）。他のブラウザでの使用には、`animationiteration`という標準イベントを使用することが推奨されます。
- **プロパティ**: イベントオブジェクトには、アニメーションの名前や、アニメーションの状態に関する情報が含まれます。

## 例
### 基本的な使用例

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .animate {
            width: 100px;
            height: 100px;
            background-color: red;
            animation: example 2s infinite;
        }

        @keyframes example {
            from { background-color: red; }
            to { background-color: blue; }
        }
    </style>
</head>
<body>

<div class="animate"></div>

<script>
    const element = document.querySelector('.animate');
    element.onwebkitanimationiteration = function(event) {
        console.log('アニメーションが繰り返されました。');
    };
</script>

</body>
</html>
```

## 説明
- **互換性**: `onwebkitanimationiteration`は、WebKitベースのブラウザでのみサポートされています。他のブラウザでは、標準の`animationiteration`イベントを使用するべきです。
- **複数のアニメーション**: 同時に複数のアニメーションが実行されている場合、どのアニメーションが繰り返されたのかを確認するために、`event.animationName`プロパティを利用できます。
- **監視の設定**: イベントリスナーは、アニメーションが追加される前に設定する必要があります。アニメーションの開始後に設定すると、期待した動作が得られない可能性があります。

## 一文要約
`onwebkitanimationiteration`は、CSSアニメーションが繰り返されるたびに発火するイベントで、アニメーションの進行状況を追跡する際に使用されます。