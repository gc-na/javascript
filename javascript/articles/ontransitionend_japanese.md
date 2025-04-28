<!--
Meta Description: # ontransitionendイベントに関する完全ガイド - JavaScript ## 概要 `ontransitionend`は、CSSトランジションが終了した際に発火するイベントです。このイベントを利用することで、トランジションが完了したタイミングで特定のアクションを実行できます。 ## ...
Meta Keywords: box, ontransitionend, event, transitionend, width
-->

# ontransitionendイベントに関する完全ガイド - JavaScript

## 概要
`ontransitionend`は、CSSトランジションが終了した際に発火するイベントです。このイベントを利用することで、トランジションが完了したタイミングで特定のアクションを実行できます。

## ドキュメンテーション
`ontransitionend`イベントは、DOM要素に適用されたCSSトランジションが完了したときに発生します。このイベントは、主にアニメーションの終了後に何らかの処理を行いたい場合に使用されます。

### 使用方法
`ontransitionend`イベントは、JavaScriptで次のように設定できます。

```javascript
element.addEventListener('transitionend', function(event) {
    // トランジション終了時の処理
});
```

### イベントオブジェクト
`transitionend`イベントのイベントオブジェクトには、トランジションの詳細情報が含まれています。主なプロパティには以下があります：

- `propertyName`: トランジションが適用されたCSSプロパティの名前。
- `elapsedTime`: トランジションが完了するまでの時間（秒単位）。
- `pseudoElement`: トランジションが適用された擬似要素（`::before`や`::after`など）。

## 例
以下は、`ontransitionend`イベントを使用した基本的な例です。

### 例1: 色の変更トランジション
```html
<div id="box" style="width:100px; height:100px; background-color:red; transition: background-color 2s;"></div>
<script>
    const box = document.getElementById('box');

    box.addEventListener('transitionend', function(event) {
        if (event.propertyName === 'background-color') {
            alert('背景色のトランジションが完了しました！');
        }
    });

    // 背景色を変更
    setTimeout(() => {
        box.style.backgroundColor = 'blue';
    }, 1000);
</script>
```

### 例2: サイズ変更トランジション
```html
<div id="box" style="width:100px; height:100px; background-color:green; transition: width 2s;"></div>
<script>
    const box = document.getElementById('box');

    box.addEventListener('transitionend', function(event) {
        if (event.propertyName === 'width') {
            console.log('幅のトランジションが完了しました！');
        }
    });

    // 幅を変更
    setTimeout(() => {
        box.style.width = '200px';
    }, 1000);
</script>
```

## 説明
`ontransitionend`イベントを使用する際の一般的な注意点は以下の通りです。

- **複数のトランジション**: 同時に複数のトランジションが発生する場合、イベントはそれぞれのプロパティごとに発火します。そのため、`event.propertyName`をチェックして、どのトランジションが完了したかを判断する必要があります。
- **トランジションの中断**: トランジションが中断された場合、`transitionend`イベントは発火しないことがあります。これは、要素がスタイルを変更したり、DOMから削除された場合に当てはまります。
- **ブラウザの互換性**: `ontransitionend`イベントは、ほとんどのモダンブラウザでサポートされていますが、古いブラウザでは動作しない場合があります。必要に応じて、ポリフィルを使用することを検討してください。

## 一文要約
`ontransitionend`は、CSSトランジションが完了した際に発火するイベントで、特定のアクションを実行するために使用されます。