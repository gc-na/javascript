<!--
Meta Description: # DOMRectReadOnly: JavaScriptにおける不変の矩形オブジェクト ## 概要 `DOMRectReadOnly`は、JavaScriptにおいて矩形の位置やサイズを表す不変のオブジェクトです。このオブジェクトは、特にHTML要素のボックスモデルの情報を取得する際に使用されます...
Meta Keywords: rect, domrectreadonly, getboundingclientrect, width, height
-->

# DOMRectReadOnly: JavaScriptにおける不変の矩形オブジェクト

## 概要
`DOMRectReadOnly`は、JavaScriptにおいて矩形の位置やサイズを表す不変のオブジェクトです。このオブジェクトは、特にHTML要素のボックスモデルの情報を取得する際に使用されます。

## ドキュメント
`DOMRectReadOnly`は、要素の四隅の座標とサイズ（幅と高さ）を含むプロパティを提供します。これは、CSSのボックスモデルに基づいた情報を取得するために利用され、ユーザーインターフェースのレイアウト計算やアニメーションなどの場面で重要な役割を果たします。

### プロパティ
- `x`: 矩形の左上隅のX座標。
- `y`: 矩形の左上隅のY座標。
- `width`: 矩形の幅。
- `height`: 矩形の高さ。
- `top`: 矩形の上辺のY座標（`y`プロパティと同じ）。
- `right`: 矩形の右辺のX座標（`x + width`）。
- `bottom`: 矩形の下辺のY座標（`y + height`）。
- `left`: 矩形の左辺のX座標（`x`プロパティと同じ）。

### 使用法
`DOMRectReadOnly`オブジェクトは、主に`getBoundingClientRect()`メソッドによって生成されます。このメソッドは、要素のビューポートに対する位置とサイズを返します。

```javascript
const element = document.getElementById('myElement');
const rect = element.getBoundingClientRect();
console.log(rect.x, rect.y, rect.width, rect.height);
```

## 例
以下は、`DOMRectReadOnly`の基本的な使用例です。

```javascript
// HTML要素を取得
const element = document.getElementById('example');

// 要素の矩形情報を取得
const rect = element.getBoundingClientRect();

// 矩形のプロパティを表示
console.log(`左上隅の座標: (${rect.x}, ${rect.y})`);
console.log(`幅: ${rect.width}`);
console.log(`高さ: ${rect.height}`);
```

## 説明
`DOMRectReadOnly`は不変であるため、取得したプロパティを変更することはできません。これは、アニメーションやレイアウト計算の精度を保つために重要です。また、`getBoundingClientRect()`が返す値は、ビューポートのスケーリングやスクロールに応じて動的に変化するため、常に最新の情報を取得するために、必要に応じてこのメソッドを再呼び出す必要があります。

### 一般的な落とし穴
- **不変性**: `DOMRectReadOnly`のプロパティは、直接変更することができません。これに注意し、必要に応じて新しい矩形を生成してください。
- **ブラウザの互換性**: 一部の古いブラウザでは、`getBoundingClientRect()`の実装が異なる場合がありますので、互換性を確認してください。

## 一文要約
`DOMRectReadOnly`は、JavaScriptにおいて要素の位置とサイズを表す不変の矩形オブジェクトであり、主に`getBoundingClientRect()`メソッドによって生成されます。