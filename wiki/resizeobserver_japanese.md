<!--
Meta Description: # ResizeObserver: JavaScriptの要素サイズ変更監視機能 ## 概要 ResizeObserverは、DOM要素のサイズの変更を監視し、サイズが変化した際にコールバック関数を実行できるJavaScriptのAPIです。この機能を使用することで、レスポンシブデザインや動的レイア...
Meta Keywords: resizeobserver, targetelement, resizeobserverは, entry, const
-->

# ResizeObserver: JavaScriptの要素サイズ変更監視機能

## 概要
ResizeObserverは、DOM要素のサイズの変更を監視し、サイズが変化した際にコールバック関数を実行できるJavaScriptのAPIです。この機能を使用することで、レスポンシブデザインや動的レイアウトの実装を容易にすることができます。

## ドキュメンテーション

### 目的
ResizeObserverは、特定のDOM要素のサイズが変更されたときに、アプリケーションがその変化に応じて何かアクションを起こすことを可能にします。これにより、要素がリサイズされたときに動的にスタイルやコンテンツを調整できます。

### 使用法
ResizeObserverを使用するには、まずインスタンスを作成し、監視したい要素を指定します。以下は基本的な使用法です。

```javascript
// ResizeObserverのインスタンスを作成
const resizeObserver = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log('サイズが変更されました:', entry.contentRect);
    }
});

// 監視する要素を指定
const targetElement = document.querySelector('#myElement');
resizeObserver.observe(targetElement);

// 監視を停止する場合
resizeObserver.unobserve(targetElement);

// すべての監視を停止する場合
resizeObserver.disconnect();
```

### 詳細
- `ResizeObserver`コンストラクタに渡すコールバック関数は、サイズが変更された要素の情報を含む`ResizeObserverEntry`オブジェクトの配列を受け取ります。
- `contentRect`プロパティには、要素の新しいサイズが含まれています。
- 監視を停止するには、`unobserve()`メソッドを使用し、すべての監視を停止するには`disconnect()`メソッドを使用します。
- ResizeObserverは、ブラウザのパフォーマンスを考慮して、サイズ変更イベントをバッチ処理し、リサイズが完了した時点でコールバックを呼び出します。

## 例

### 基本的な使用例

```html
<div id="myElement" style="width: 100px; height: 100px; background: red;"></div>

<script>
const resizeObserver = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log(`新しいサイズ: 幅 ${entry.contentRect.width}, 高さ ${entry.contentRect.height}`);
    }
});

const targetElement = document.querySelector('#myElement');
resizeObserver.observe(targetElement);

// サイズ変更のテスト
setTimeout(() => {
    targetElement.style.width = '200px';
    targetElement.style.height = '200px';
}, 1000);
</script>
```

この例では、1秒後に要素のサイズが変更され、その新しいサイズがコンソールに表示されます。

## 説明
- **共通の落とし穴**: ResizeObserverは、要素のサイズが変更されるたびにコールバックを実行しますが、過剰に要素を監視するとパフォーマンスに影響を与える可能性があります。必要なときにだけ監視を開始し、不要になったら停止することが重要です。
- **スタイルの変更**: 要素のスタイルを変更した場合、その変更が即座に反映されないことがあります。ブラウザの再描画が行われるまで、古いサイズが返されることがあります。
- **ブラウザの互換性**: ResizeObserverは、主要な現代ブラウザでサポートされていますが、古いブラウザではサポートされていない場合があります。使用する前に、互換性を確認してください。

## 一言まとめ
ResizeObserverは、DOM要素のサイズ変更を効率的に監視し、レスポンシブなユーザーインターフェースを実現するための強力なツールです。