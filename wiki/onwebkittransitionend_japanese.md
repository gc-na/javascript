<!--
Meta Description: # onwebkittransitionend: JavaScriptによるCSSトランジションの終了イベント ## 概要 `onwebkittransitionend`は、CSSトランジションが完了したときに発生するイベントを処理するためのJavaScriptプロパティです。このイベントは、Web...
Meta Keywords: onwebkittransitionend, box, event, ontransitionend, style
-->

# onwebkittransitionend: JavaScriptによるCSSトランジションの終了イベント

## 概要
`onwebkittransitionend`は、CSSトランジションが完了したときに発生するイベントを処理するためのJavaScriptプロパティです。このイベントは、WebKitベースのブラウザで特に使用されます。

## ドキュメンテーション
`onwebkittransitionend`は、要素のCSSトランジションが終了したことを検知するために使われます。これにより、トランジション完了後に特定のアクションを実行することが可能になります。主に、アニメーションの完了後にクラスを変更したり、次のアニメーションを開始したりする際に利用されます。

### 使用方法
このプロパティは、イベントリスナーとして設定され、要素に対してトランジションが終了した際に呼び出される関数を指定します。以下は基本的な構文です。

```javascript
element.onwebkittransitionend = function(event) {
    // トランジション終了後の処理
};
```

### 詳細
- **対象ブラウザ**: `onwebkittransitionend`は主にWebKitエンジンを使用するブラウザ（Safari、古いバージョンのChromeなど）でサポートされています。
- **イベントオブジェクト**: イベントハンドラ内で受け取る`event`オブジェクトには、トランジションが適用されたCSSプロパティに関する情報が含まれています。
- **互換性**: `ontransitionend`イベントも同様の機能を提供しますが、全てのブラウザでのサポートを考慮すると、標準の`ontransitionend`を優先的に使用し、必要に応じてベンダープレフィックスを使用してください。

## 例
以下は、`onwebkittransitionend`を利用した簡単な例です。

```html
<div id="box" style="width: 100px; height: 100px; background-color: red; transition: background-color 2s;"></div>
<script>
    const box = document.getElementById('box');

    box.onwebkittransitionend = function(event) {
        console.log('トランジションが完了しました: ' + event.propertyName);
        box.style.backgroundColor = 'blue'; // トランジション後に色を変更
    };

    // トランジションを開始
    box.style.backgroundColor = 'green';
</script>
```

## 説明
`onwebkittransitionend`を使用する際の一般的な注意点や落とし穴は、以下の通りです。

- **複数のトランジション**: 複数のトランジションが同時に実行される場合、どのトランジションが完了したのかを正確に把握するためには、`event.propertyName`を確認することが重要です。
- **イベントの重複**: トランジションが複数回発生する場合、イベントハンドラが重複して呼び出されることがあります。これを防ぐためには、必要に応じてハンドラを一時的に無効化することを考慮しましょう。
- **ブラウザ互換性**: すべてのブラウザが`onwebkittransitionend`をサポートしているわけではないため、標準の`ontransitionend`を併用することを推奨します。

## 一文要約
`onwebkittransitionend`は、WebKitベースのブラウザにおいてCSSトランジションの完了を検知するためのJavaScriptイベントプロパティです。