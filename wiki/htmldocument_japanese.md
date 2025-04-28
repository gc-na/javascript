<!--
Meta Description: # HTMLDocument: JavaScriptにおける重要なインターフェース ## 概要 `HTMLDocument`は、JavaScriptを使用してHTML文書を操作するためのインターフェースです。このインターフェースは、DOM（Document Object Model）を通じて文書の内...
Meta Keywords: document, htmldocument, javascript, const, body
-->

# HTMLDocument: JavaScriptにおける重要なインターフェース

## 概要
`HTMLDocument`は、JavaScriptを使用してHTML文書を操作するためのインターフェースです。このインターフェースは、DOM（Document Object Model）を通じて文書の内容や構造にアクセスし、変更するための機能を提供します。

## ドキュメンテーション
`HTMLDocument`は、Webページ上のHTML文書を表現するオブジェクトです。このオブジェクトを使用することで、JavaScriptはページ上の要素にアクセス、追加、削除、または変更することができます。主に、`document`オブジェクトを通じて利用されます。

### 目的
`HTMLDocument`は、ユーザーインターフェースを動的に変更したり、ユーザーの入力に基づいてリアルタイムでページを更新したりするために使用されます。

### 使用法
`HTMLDocument`を使用するためには、通常、次のように`document`オブジェクトを通じてアクセスします。

```javascript
// ページタイトルを取得
console.log(document.title);

// 新しい要素を作成
const newElement = document.createElement('div');
newElement.textContent = 'こんにちは、世界！';
document.body.appendChild(newElement);
```

### 詳細
`HTMLDocument`は以下のメソッドやプロパティを持っています。

- **プロパティ**
  - `title`: 文書のタイトルを取得または設定します。
  - `body`: 文書の`<body>`要素を取得します。
  - `head`: 文書の`<head>`要素を取得します。
  
- **メソッド**
  - `getElementById()`: 指定したIDを持つ要素を取得します。
  - `getElementsByClassName()`: 指定したクラス名を持つ要素のリストを取得します。
  - `querySelector()`: CSSセレクタを使用して最初の要素を取得します。

## 例
以下は、`HTMLDocument`を使用した基本的な例です。

### 例1: タイトルの変更
```javascript
document.title = '新しいタイトル';
```

### 例2: 要素の追加
```javascript
const newDiv = document.createElement('div');
newDiv.textContent = '新しいコンテンツ';
document.body.appendChild(newDiv);
```

### 例3: 既存要素の取得と変更
```javascript
const header = document.getElementById('header');
header.style.color = 'blue';
```

## 説明
`HTMLDocument`を使用する際の一般的な落とし穴には、要素がDOMに追加される前にアクセスしようとすることがあります。たとえば、`DOMContentLoaded`イベントをリッスンしてから操作を行うことが推奨されます。

```javascript
document.addEventListener('DOMContentLoaded', () => {
    const mainContent = document.getElementById('main-content');
    mainContent.textContent = 'ページが読み込まれました';
});
```

また、`getElementsByClassName()`や`getElementsByTagName()`メソッドは、ノードリストを返すため、対象の要素を直接操作する際には注意が必要です。

## 一文での要約
`HTMLDocument`は、JavaScriptを使用してHTML文書を動的に操作するための主要なインターフェースです。