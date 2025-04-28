<!--
Meta Description: # onwebkitanimationend イベントに関する完全ガイド ## 概要 `onwebkitanimationend` は、WebKit ブラウザ（主に Safari）においてアニメーションが終了した際に発生するイベントです。このイベントを利用することで、アニメーションが完了した後に特定...
Meta Keywords: onwebkitanimationend, webkit, css, element, myelement
-->

# onwebkitanimationend イベントに関する完全ガイド

## 概要
`onwebkitanimationend` は、WebKit ブラウザ（主に Safari）においてアニメーションが終了した際に発生するイベントです。このイベントを利用することで、アニメーションが完了した後に特定のアクションを実行できます。

## ドキュメンテーション
### 目的
`onwebkitanimationend` イベントは、CSS アニメーションが完了したことを検知し、それに基づいて JavaScript コードを実行するために使用されます。これにより、アニメーションが終了した後の状態を管理したり、次のアクションをトリガーしたりすることが可能です。

### 使用法
このイベントは、HTML 要素に対して直接設定することができます。イベントリスナーを追加することで、アニメーション終了時に特定の関数を呼び出すことができます。

```javascript
const element = document.getElementById('myElement');

element.onwebkitanimationend = function() {
    console.log('アニメーションが終了しました。');
};
```

### 詳細
- **イベント名**: `webkitanimationend`
- **発生時期**: CSS アニメーションが完全に終了したときに発生します。
- **ブラウザ対応**: 主に Safari などの WebKit ベースのブラウザでサポートされています。
- **プロパティ**: イベントオブジェクトには、終了したアニメーションの詳細を含むプロパティが含まれています。

## 例
以下は、`onwebkitanimationend` イベントを使用した基本的な例です。

### 例1: シンプルなアニメーション終了時の処理
```html
<div id="myElement" style="width: 100px; height: 100px; background: red; animation: example 2s;"></div>
<script>
  const element = document.getElementById('myElement');

  element.onwebkitanimationend = function() {
      alert('アニメーションが終了しました！');
  };
</script>
<style>
@keyframes example {
  from {background-color: red;}
  to {background-color: blue;}
}
</style>
```

## 説明
`onwebkitanimationend` イベントを使用する際の注意点や一般的な落とし穴について説明します。

- **ブラウザの互換性**: このイベントは特に WebKit ベースのブラウザに特化しているため、他のブラウザ（Chrome、Firefox など）では `animationend` イベントを使用することが推奨されます。
- **CSS アニメーションの定義**: アニメーションが正しく定義されていることを確認してください。アニメーションが適用されていない要素では、このイベントは発生しません。
- **複数のアニメーション**: 同時に複数のアニメーションが適用されている場合、各アニメーションごとに `onwebkitanimationend` イベントが発生します。

## 一文要約
`onwebkitanimationend` は、WebKit ブラウザにおいて CSS アニメーションが終了した際に発生するイベントで、アニメーション完了後の処理を実行するために使用されます。