<!--
Meta Description: # MutationRecordについての詳細ガイド - JavaScriptのDOM変更を追跡する ## 概要 `MutationRecord`は、JavaScriptにおけるDOMの変更を記録するためのオブジェクトです。主に`MutationObserver`とともに使用され、DOMツリーの変更...
Meta Keywords: mutationrecord, mutationobserver, attributes, const, targetnode
-->

# MutationRecordについての詳細ガイド - JavaScriptのDOM変更を追跡する

## 概要
`MutationRecord`は、JavaScriptにおけるDOMの変更を記録するためのオブジェクトです。主に`MutationObserver`とともに使用され、DOMツリーの変更（追加、削除、属性の変更など）を監視する際に重要な役割を果たします。

## ドキュメンテーション
### 目的
`MutationRecord`は、DOMの変更に関する詳細情報を提供します。これにより、開発者はリアルタイムで変更を監視し、必要に応じてアクションを取ることができます。

### 使用法
`MutationRecord`は、`MutationObserver`によって生成されます。`MutationObserver`のコールバック関数内で、DOMの変更に関する情報が`MutationRecord`の配列として渡されます。

### プロパティ
`MutationRecord`には以下のプロパティがあります：

- **type**: 変更のタイプを示す文字列（例：`"childList"`、`"attributes"`、`"characterData"`）。
- **target**: 変更が行われたノード。
- **addedNodes**: 追加されたノードのリスト（`NodeList`）。
- **removedNodes**: 削除されたノードのリスト（`NodeList`）。
- **previousSibling**: 変更が行われたノードの直前の兄弟ノード。
- **nextSibling**: 変更が行われたノードの直後の兄弟ノード。
- **attributeName**: 変更された属性の名前（`type`が`"attributes"`の時のみ）。
- **oldValue**: 変更前の値（`type`が`"characterData"`または`"attributes"`の時のみ）。

## 例
以下は、`MutationObserver`を使用して`MutationRecord`を取得する基本的な例です。

```javascript
// 監視するノードを取得
const targetNode = document.getElementById('target');

// 変更を監視するためのオブザーバーを作成
const observer = new MutationObserver((mutationsList) => {
    for (const mutation of mutationsList) {
        console.log(mutation);
    }
});

// オブザーバーを設定
observer.observe(targetNode, {
    childList: true,
    attributes: true,
    characterData: true
});

// ノードに変更を加える
targetNode.setAttribute('data-example', 'newValue');
const newElement = document.createElement('div');
targetNode.appendChild(newElement);
```

## 説明
`MutationRecord`を使用する際の一般的な落とし穴や注意点を以下に示します。

- **非同期処理**: `MutationObserver`のコールバックは非同期で呼び出されるため、DOMの変更が瞬時に反映されない場合があります。コールバック内での処理は注意が必要です。
- **不要な監視**: 無駄な変更を監視するとパフォーマンスに影響を与えることがあります。必要な変更のみを監視するように設定を最適化することが重要です。
- **複数の変更**: 1回の変更で複数の`MutationRecord`が生成される場合がありますが、これらは1つのコールバック内でまとめて処理されます。

## 一文要約
`MutationRecord`は、JavaScriptにおけるDOMの変更を記録するオブジェクトであり、`MutationObserver`と組み合わせて使用されます。