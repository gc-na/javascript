<!--
Meta Description: # JavaScriptのonmouseoverイベント: マウスオーバー時のイベント処理 ## 概要 `onmouseover`は、HTML要素にマウスカーソルが乗ったときに発生するイベントを処理するためのJavaScriptイベントハンドラです。このイベントを利用することで、インタラクティブなユ...
Meta Keywords: onmouseover, html, div, style, width
-->

# JavaScriptのonmouseoverイベント: マウスオーバー時のイベント処理

## 概要
`onmouseover`は、HTML要素にマウスカーソルが乗ったときに発生するイベントを処理するためのJavaScriptイベントハンドラです。このイベントを利用することで、インタラクティブなユーザーインターフェースを作成し、ユーザーの操作に応じた動的な反応を実現できます。

## ドキュメンテーション
`onmouseover`イベントは、指定したHTML要素にマウスが乗ったときにトリガーされます。このイベントは、ユーザーが要素にカーソルを合わせた際に、視覚的なフィードバックを提供するために広く使用されます。

### 使い方
`onmouseover`は、HTML要素の属性としても、JavaScriptコード内でイベントリスナーを追加する方法でも使用できます。

#### HTML属性としての使用例
```html
<div onmouseover="alert('マウスが乗っています！')">このテキストにマウスを乗せてください。</div>
```

#### JavaScriptでの使用例
```javascript
const divElement = document.getElementById('myDiv');
divElement.onmouseover = function() {
    alert('マウスが乗っています！');
};
```

### 詳細
- **対応ブラウザ**: 主要なブラウザ（Chrome, Firefox, Safari, Edgeなど）でサポートされています。
- **イベントオブジェクト**: `onmouseover`イベントが発生すると、イベントオブジェクトが生成され、マウスの位置や関連する要素情報を含んでいます。
- **関連イベント**: `onmouseout`（マウスが要素から離れたとき）と組み合わせて使用することが多いです。

## 例
### 基本的な使用例
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onmouseoverの例</title>
    <style>
        #highlight {
            width: 200px;
            height: 100px;
            background-color: lightgray;
            text-align: center;
            line-height: 100px;
        }
    </style>
</head>
<body>

<div id="highlight" onmouseover="this.style.backgroundColor='yellow';" onmouseout="this.style.backgroundColor='lightgray';">
    マウスを乗せてください
</div>

</body>
</html>
```

## 説明
`onmouseover`イベントを使用する際の一般的な落とし穴や注意点があります。

- **パフォーマンス**: 多くの要素で`onmouseover`を使用すると、パフォーマンスに影響を与える可能性があります。必要な場合にのみ使用することが推奨されます。
- **タッチデバイス**: タッチデバイスでは、`onmouseover`イベントが期待通りに動作しないことがあります。代わりに、タッチイベントを考慮する必要があります。
- **バブリング**: `onmouseover`はバブリングイベントであり、親要素でも発生する可能性があるため、意図しない動作を引き起こすことがあります。

## 一文要約
`onmouseover`は、HTML要素にマウスカーソルが乗った際にトリガーされるJavaScriptイベントで、インタラクティブなユーザーインターフェースを構築するために使用されます。