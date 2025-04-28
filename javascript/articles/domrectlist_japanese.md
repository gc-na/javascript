<!--
Meta Description: # DOMRectList: JavaScriptにおけるDOMRectListの完全ガイド ## 概要 `DOMRectList`は、複数の`DOMRect`オブジェクトを管理するためのインターフェースであり、特にブラウザの描画領域や要素のサイズ、位置を取得する際に役立ちます。このインターフェース...
Meta Keywords: domrectlist, domrect, getclientrects, element, rects
-->

# DOMRectList: JavaScriptにおけるDOMRectListの完全ガイド

## 概要
`DOMRectList`は、複数の`DOMRect`オブジェクトを管理するためのインターフェースであり、特にブラウザの描画領域や要素のサイズ、位置を取得する際に役立ちます。このインターフェースは、要素の境界ボックス情報を効率的に操作するための手段を提供します。

## ドキュメンテーション
`DOMRectList`は、`DOMRect`オブジェクトのコレクションであり、主に`getClientRects()`メソッドや`getBoundingClientRect()`メソッドから取得されます。これにより、要素の可視領域やレイアウト情報を取得することができます。`DOMRectList`は、配列のようなオブジェクトであり、インデックスを使用して各`DOMRect`にアクセスすることが可能です。

### 使用方法
- **取得**: `DOMRectList`は、以下のメソッドを使用して取得します。
  - `element.getClientRects()`: 要素のクライアント矩形のリストを取得します。
  - `element.getBoundingClientRect()`: 要素の単一の境界矩形を取得しますが、`DOMRectList`ではなく`DOMRect`オブジェクトが返されます。

### 詳細
- `DOMRectList`は、`length`プロパティを持ち、要素内の矩形の数を示します。
- 各`DOMRect`には、`x`, `y`, `width`, `height`, `top`, `right`, `bottom`, `left`のプロパティがあり、矩形の位置とサイズを表します。
- `DOMRectList`は、通常の配列メソッド（`forEach`, `map`, `filter`など）を使用することができませんが、ループを使用して個別の`DOMRect`にアクセスできます。

## 例
以下は、`DOMRectList`を使用して要素の境界矩形を取得する基本的な例です。

```javascript
// 要素を取得
const element = document.getElementById('myElement');

// DOMRectListを取得
const rects = element.getClientRects();

// 各矩形の情報を表示
for (let i = 0; i < rects.length; i++) {
    console.log(`矩形 ${i + 1}:`, rects[i]);
}
```

## 説明
`DOMRectList`を使用する際の一般的な落とし穴には、以下があります。

- **空のリスト**: 要素が視覚的に表示されていない場合、`getClientRects()`は空の`DOMRectList`を返すことがあります。このため、要素が正しく表示されていることを確認する必要があります。
- **レイアウトの変更**: DOMの変更やCSSの変更があった場合、取得した`DOMRectList`は瞬時に無効になることがあります。必要に応じて再取得することが推奨されます。
- **ブラウザの互換性**: 一部の古いブラウザでは、`DOMRectList`や関連メソッドがサポートされていない場合があるため、互換性を確認することが重要です。

## 一行要約
`DOMRectList`は、複数の`DOMRect`オブジェクトを管理し、要素の境界ボックス情報を取得するためのJavaScriptのインターフェースです。