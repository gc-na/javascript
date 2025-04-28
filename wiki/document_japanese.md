<!--
Meta Description: # JavaScriptの「document」オブジェクト：ウェブページ操作の基礎 ## 概要 JavaScriptにおける「document」オブジェクトは、HTMLやXML文書を操作するための主要なインターフェースです。このオブジェクトを使用することで、DOM（Document Object M...
Meta Keywords: document, オブジェクトは, getelementbyid, javascript, const
-->

# JavaScriptの「document」オブジェクト：ウェブページ操作の基礎

## 概要
JavaScriptにおける「document」オブジェクトは、HTMLやXML文書を操作するための主要なインターフェースです。このオブジェクトを使用することで、DOM（Document Object Model）にアクセスし、要素の取得、変更、追加、削除が可能です。

## ドキュメンテーション
「document」オブジェクトは、ブラウザが読み込んだウェブページの全体を表します。JavaScriptを使用して、このオブジェクトを操作することで、動的なコンテンツの作成や、ユーザーインターフェースの改善ができます。

### 主な機能
- **要素の取得**: `document.getElementById()`や`document.querySelector()`などのメソッドを使用して、特定のHTML要素を取得します。
- **要素の追加**: `document.createElement()`で新しい要素を作成し、`appendChild()`で既存の要素に追加します。
- **要素の変更**: 取得した要素のプロパティを変更することで、テキストやスタイルを動的に変更できます。
- **イベントリスナーの追加**: `addEventListener()`を使用して、ユーザーの操作に応じたイベントを処理します。

## 例
### 要素の取得と変更
```javascript
// IDが"example"の要素を取得
const element = document.getElementById("example");

// 要素のテキストを変更
element.textContent = "新しいテキスト";
```

### 新しい要素の作成と追加
```javascript
// 新しいdiv要素を作成
const newDiv = document.createElement("div");
newDiv.textContent = "これは新しい要素です";

// bodyに新しい要素を追加
document.body.appendChild(newDiv);
```

### イベントリスナーの追加
```javascript
const button = document.getElementById("myButton");
button.addEventListener("click", function() {
    alert("ボタンがクリックされました！");
});
```

## 説明
「document」オブジェクトを使用する際の一般的な落とし穴には、要素がDOMに存在しない状態でアクセスしようとすることがあります。この場合、`null`が返されるため、必ず要素が存在することを確認してから操作を行うようにしてください。また、DOMが完全に読み込まれる前にJavaScriptコードが実行されると、期待通りの動作をしないことがあります。そのため、`DOMContentLoaded`イベントを利用して、DOMが読み込まれた後にコードを実行することが推奨されます。

## 一文要約
JavaScriptの「document」オブジェクトは、ウェブページのHTML内容を操作するための中心的なインターフェースです。