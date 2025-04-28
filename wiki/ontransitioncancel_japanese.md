<!--
Meta Description: # ontransitioncancel: JavaScriptでのトランジションキャンセルイベント ## 概要 `ontransitioncancel` は、CSSトランジションがキャンセルされたときに発火するイベントです。このイベントを使用することで、アニメーションやスタイルの変更に対するユーザ...
Meta Keywords: ontransitioncancel, element, event, style, width
-->

# ontransitioncancel: JavaScriptでのトランジションキャンセルイベント

## 概要
`ontransitioncancel` は、CSSトランジションがキャンセルされたときに発火するイベントです。このイベントを使用することで、アニメーションやスタイルの変更に対するユーザーのインタラクションに応じて、適切な処理を行うことが可能になります。

## ドキュメンテーション
`ontransitioncancel` イベントは、HTML要素のトランジションが何らかの原因で完了しない場合に発生します。例えば、トランジション中に要素のスタイルが変更された場合、このイベントがトリガーされます。

### 目的
`ontransitioncancel` を使用することで、トランジションがキャンセルされた際に特定のアクションを実行することができます。これにより、ユーザーインターフェースの応答性を向上させることができます。

### 使い方
`ontransitioncancel` イベントは、JavaScriptのイベントリスナーを使用して追加します。以下は、基本的な構文です。

```javascript
element.ontransitioncancel = function(event) {
    // キャンセル時の処理
};
```

### 詳細
- **イベントプロパティ**: `event` オブジェクトには、キャンセルされたトランジションに関する情報が含まれています。これには、発生した要素やトランジションのプロパティなどが含まれます。
- **ブラウザサポート**: ほとんどのモダンブラウザでサポートされていますが、古いブラウザでは動作しない場合があります。ブラウザの互換性を確認することが重要です。

## 例
### 基本的な使用例

以下の例では、要素のトランジションがキャンセルされた際にコンソールにメッセージを表示します。

```html
<div id="myElement" style="width: 100px; height: 100px; background-color: blue; transition: all 2s;"></div>
<script>
    const element = document.getElementById('myElement');

    element.ontransitioncancel = function(event) {
        console.log('トランジションがキャンセルされました:', event.propertyName);
    };

    // トランジションを開始
    element.style.width = '200px';

    // 2秒後に幅を元に戻す
    setTimeout(() => {
        element.style.width = '100px'; // この時点でトランジションがキャンセルされる
    }, 1000);
</script>
```

## 説明
`ontransitioncancel` を使用する際の注意点として、トランジションの状態を把握することが重要です。トランジションがキャンセルされる原因は、スタイルの変更やユーザーの操作など多岐にわたります。また、トランジションが完了した後にこのイベントは発生しないため、適切なトリガーを設定する必要があります。

## 一文要約
`ontransitioncancel` は、CSSトランジションがキャンセルされた際に発火するイベントであり、ユーザーインターフェースの操作に対する応答性を向上させるために利用されます。