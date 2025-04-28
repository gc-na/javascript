<!--
Meta Description: # onscrollsnapchange: JavaScriptにおけるスクロールスナップの変化イベント ## 概要 `onscrollsnapchange`は、CSS Scroll Snapの機能に関連するJavaScriptイベントで、スクロールスナップの位置が変化したときに発生します。このイベ...
Meta Keywords: onscrollsnapchange, scroll, div, snap, class
-->

# onscrollsnapchange: JavaScriptにおけるスクロールスナップの変化イベント

## 概要
`onscrollsnapchange`は、CSS Scroll Snapの機能に関連するJavaScriptイベントで、スクロールスナップの位置が変化したときに発生します。このイベントを使用することで、ユーザーのスクロール動作に基づいて特定のアクションを実行できます。

## ドキュメント
### 目的
`onscrollsnapchange`イベントは、特定の要素がスクロールスナップによって新しい位置にスナップした際にトリガーされます。このイベントを利用することで、ユーザーがスクロールした際にインタラクティブなフィードバックを提供したり、アニメーションを実行したりすることが可能になります。

### 使用方法
`onscrollsnapchange`イベントは、JavaScriptのイベントリスナーを使用して監視します。次の手順で使用できます。

1. 対象の要素を選択します。
2. `onscrollsnapchange`イベントリスナーを追加します。
3. コールバック関数内で、必要なアクションを定義します。

### 詳細
このイベントは、要素がCSSのスクロールスナップを使用して新しい位置に移動するたびに発生します。スナップポイントは、CSSで設定された特定の位置に要素がスナップすることを意味します。

### イベントのプロパティ
- `target`: イベントが発生した要素。
- `detail`: スナップ位置の詳細情報。

## 例
以下は、`onscrollsnapchange`イベントの基本的な使用例です。

```html
<div class="scroll-container" style="overflow: scroll; scroll-snap-type: y mandatory;">
  <div class="snap-item" style="scroll-snap-align: start;">アイテム1</div>
  <div class="snap-item" style="scroll-snap-align: start;">アイテム2</div>
  <div class="snap-item" style="scroll-snap-align: start;">アイテム3</div>
</div>

<script>
  const container = document.querySelector('.scroll-container');
  
  container.onscrollsnapchange = function(event) {
    console.log('スナップ位置が変わりました！');
  };
</script>
```

## 説明
`onscrollsnapchange`イベントを使用する際には、以下の点に注意が必要です。

- **ブラウザの互換性**: 現在、このイベントはすべてのブラウザでサポートされているわけではありません。最新のブラウザでの動作を確認することが重要です。
- **パフォーマンス**: スクロール中に多くの処理を行うと、パフォーマンスに影響を与える可能性があります。必要なアクションだけを実行するように心掛けましょう。

## 一文の要約
`onscrollsnapchange`は、CSS Scroll Snapの位置が変わった際にトリガーされるJavaScriptイベントです。