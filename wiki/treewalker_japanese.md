<!--
Meta Description: # TreeWalker（ツリーウォーカー）: JavaScript の DOM 操作を簡素化する ## 概要 TreeWalker は、JavaScript における DOM（Document Object Model）を操作するための強力なインターフェースです。特に、DOM ツリーを効率的に t...
Meta Keywords: treewalker, dom, nodefilter, javascript, document
-->

# TreeWalker（ツリーウォーカー）: JavaScript の DOM 操作を簡素化する

## 概要
TreeWalker は、JavaScript における DOM（Document Object Model）を操作するための強力なインターフェースです。特に、DOM ツリーを効率的に traversing（走査）するためのメソッドを提供し、ノードの選択やフィルタリングを容易にします。

## ドキュメンテーション
### 目的
TreeWalker は、指定したノードを起点にして、DOM ツリー内のノードを順に走査するためのオブジェクトです。特定の条件に基づいてノードをフィルタリングし、必要なノードのみを取得することができます。

### 使用法
TreeWalker を作成するには、`document.createTreeWalker` メソッドを使用します。このメソッドは、以下の引数を受け取ります。

```javascript
let treeWalker = document.createTreeWalker(
    rootNode,           // 起点となるノード
    whatToShow,        // 表示するノードの種類
    filterFunction,    // フィルタリング関数
    entityReferenceExpansion  // エンティティ参照を展開するかどうか
);
```

- **rootNode**: TreeWalker の起点となるノードを指定します。
- **whatToShow**: 表示するノードの種類を指定する定数。例えば、`NodeFilter.SHOW_ELEMENT` や `NodeFilter.SHOW_TEXT` など。
- **filterFunction**: フィルタリングを行う関数。ノードを引数に取り、`NodeFilter.FILTER_ACCEPT`、`NodeFilter.FILTER_REJECT` または `NodeFilter.FILTER_SKIP` を返します。
- **entityReferenceExpansion**: エンティティ参照を展開する場合は `true`、そうでない場合は `false` を指定します。

### プロパティとメソッド
- **nextNode()**: 次のノードを取得します。
- **previousNode()**: 前のノードを取得します。
- **currentNode**: 現在のノードを取得または設定します。

## 例
基本的な使用例を以下に示します。

```javascript
// DOM ツリーのルートノードを取得
let root = document.getElementById("root");

// TreeWalker を作成
let treeWalker = document.createTreeWalker(
    root,
    NodeFilter.SHOW_ELEMENT,
    null,
    false
);

// 次のノードを走査
while (treeWalker.nextNode()) {
    console.log(treeWalker.currentNode.tagName); // 各要素のタグ名を表示
}
```

## 説明
TreeWalker を使用する際の注意点として、以下の点があります。

- **フィルタリング関数**: フィルタリング関数は、条件に合致しないノードをスキップする場合があるため、意図したノードが取得できないことがあります。適切にフィルタリング条件を設定することが重要です。
- **ノードの変更**: TreeWalker を使用している間に、DOM ツリーが変更されると、意図しない結果を招くことがあります。DOM の変更が行われる場合は、TreeWalker を再作成することを検討してください。

## 一文の要約
TreeWalker は、DOM ツリー内のノードを効率的に走査し、フィルタリングするための JavaScript インターフェースです。