<!--
Meta Description: # JavaScriptのStaticRange: 使い方と例 ## 概要 `StaticRange`は、DOM内の静的なテキスト範囲を表すために使用されるJavaScriptのインターフェイスです。このオブジェクトは、特定のノード内のテキストの範囲を扱う際に便利です。 ## ドキュメンテーション ...
Meta Keywords: staticrange, startcontainer, endcontainer, startoffset, endoffset
-->

# JavaScriptのStaticRange: 使い方と例

## 概要
`StaticRange`は、DOM内の静的なテキスト範囲を表すために使用されるJavaScriptのインターフェイスです。このオブジェクトは、特定のノード内のテキストの範囲を扱う際に便利です。

## ドキュメンテーション
### 目的
`StaticRange`は、選択したテキストの範囲を表現し、特定のノードの内容を操作するための情報を提供します。これにより、テキストの操作やスタイルの適用が簡単に行えます。

### 使用法
`StaticRange`は、次のように作成されます：

```javascript
let staticRange = new StaticRange({
    startContainer: node, // 範囲の開始ノード
    startOffset: number,   // 開始オフセット
    endContainer: node,    // 範囲の終了ノード
    endOffset: number      // 終了オフセット
});
```

- **startContainer**: 範囲の開始位置を示すノード。
- **startOffset**: 開始ノード内でのオフセット位置。
- **endContainer**: 範囲の終了位置を示すノード。
- **endOffset**: 終了ノード内でのオフセット位置。

### 詳細
`StaticRange`は、選択範囲が変更されることなく、特定のノードに固定されるため、ページ内のテキスト操作において安定した状態を保ちます。このインターフェイスは主に、テキストの選択や範囲を処理するために使用されます。

## 例
以下は、`StaticRange`の基本的な使用例です。

```javascript
// DOM内の要素を取得
const startNode = document.getElementById("start");
const endNode = document.getElementById("end");

// StaticRangeの作成
const staticRange = new StaticRange({
    startContainer: startNode,
    startOffset: 0,
    endContainer: endNode,
    endOffset: endNode.textContent.length
});

// StaticRangeの情報を表示
console.log(staticRange.startContainer); // 開始ノード
console.log(staticRange.endContainer);   // 終了ノード
```

## 説明
`StaticRange`を使用する際の一般的な落とし穴には、以下のようなものがあります。

- **ノードの不一致**: `startContainer`と`endContainer`が異なるタイプのノードである場合、意図した範囲が正しく設定されないことがあります。
- **オフセットの範囲外**: `startOffset`または`endOffset`が、指定したノードのテキスト長を超えるとエラーが発生する可能性があります。常にオフセットがノード内の範囲内であることを確認してください。

## 一文まとめ
`StaticRange`は、JavaScriptにおいて静的なテキスト範囲を表現し、DOM内のテキスト操作を容易にするためのインターフェイスです。