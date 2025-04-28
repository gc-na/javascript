<!--
Meta Description: # DOMRect: JavaScriptにおける矩形オブジェクトの詳細 ## 概要 `DOMRect`は、要素の境界ボックスのサイズと位置を取得するためのオブジェクトです。主に、要素のレイアウトや位置を操作する際に役立ちます。 ## ドキュメント ### 目的 `DOMRect`は、HTML要素の...
Meta Keywords: domrect, rect, getboundingclientrect, const, element
-->

# DOMRect: JavaScriptにおける矩形オブジェクトの詳細

## 概要
`DOMRect`は、要素の境界ボックスのサイズと位置を取得するためのオブジェクトです。主に、要素のレイアウトや位置を操作する際に役立ちます。

## ドキュメント
### 目的
`DOMRect`は、HTML要素の矩形情報（位置とサイズ）を表現するために使用されます。これにより、特定の要素が画面上のどこにあるか、またそのサイズがどれくらいであるかを簡単に取得できます。

### 使用法
`DOMRect`オブジェクトは、通常、`getBoundingClientRect()`メソッドを使用して取得されます。このメソッドは、要素の境界ボックスの情報を含む`DOMRect`オブジェクトを返します。

```javascript
const element = document.getElementById('myElement');
const rect = element.getBoundingClientRect();
```

### 詳細
`DOMRect`オブジェクトには、次のプロパティがあります：

- `x`: 矩形の左上隅のX座標（viewport内）
- `y`: 矩形の左上隅のY座標（viewport内）
- `width`: 矩形の幅
- `height`: 矩形の高さ
- `top`: 矩形の上辺のY座標
- `right`: 矩形の右辺のX座標
- `bottom`: 矩形の下辺のY座標
- `left`: 矩形の左辺のX座標

これらのプロパティを使用して、要素の位置やサイズを取得できます。

## 例
基本的な使用例を以下に示します。

```javascript
// 要素を取得
const element = document.querySelector('.example');

// 矩形情報を取得
const rect = element.getBoundingClientRect();

// 矩形のプロパティをログ出力
console.log(`X: ${rect.x}, Y: ${rect.y}`);
console.log(`Width: ${rect.width}, Height: ${rect.height}`);
```

## 説明
`DOMRect`を使用する際の一般的な注意点：

- **スクロール位置の影響**: `getBoundingClientRect()`は、要素の位置をviewport基準で返します。スクロール位置によって結果が変わるため、注意が必要です。
- **CSS変形**: CSSのtransformプロパティで要素を変形させた場合、返される座標は変形後の位置になります。
- **パフォーマンス**: このメソッドはDOMのアクセスを伴うため、頻繁に呼び出すとパフォーマンスに影響を与える可能性があります。必要に応じてキャッシュすることを検討してください。

## 一文要約
`DOMRect`は、要素のサイズと位置を取得するためのオブジェクトで、主に`getBoundingClientRect()`メソッドを通じて使用されます。