<!--
Meta Description: # JavaScriptとCSSの連携方法：スタイル操作の基本 ## 概要 JavaScriptを使用してCSSスタイルを操作することにより、動的なウェブページを作成できます。このプロセスでは、HTML要素にスタイルを適用したり、変更したりすることができます。 ## ドキュメンテーション JavaS...
Meta Keywords: element, document, const, javascript, getelementbyid
-->

# JavaScriptとCSSの連携方法：スタイル操作の基本

## 概要
JavaScriptを使用してCSSスタイルを操作することにより、動的なウェブページを作成できます。このプロセスでは、HTML要素にスタイルを適用したり、変更したりすることができます。

## ドキュメンテーション
JavaScriptは、DOM（Document Object Model）を通じてCSSスタイルにアクセスし、変更を加えることができます。これにより、ユーザーのインタラクションに応じてリアルタイムでスタイルを変更することが可能です。

### 使用目的
- ユーザーインタラクションに基づくスタイルの変更
- アニメーションやトランジションの追加
- レスポンシブデザインの実現

### 使用方法
CSSスタイルを操作するためには、以下のメソッドやプロパティを使用します。

- **styleプロパティ**: HTML要素のインラインスタイルを直接変更します。
- **classListプロパティ**: CSSクラスを追加・削除することでスタイルを変更します。
- **getComputedStyle()**: 要素に適用されているCSSスタイルを取得します。

### 詳細
JavaScriptを使ったCSS操作は、以下のように実施できます。

1. HTML要素を取得します。
2. `style`プロパティを使用して、スタイルを直接変更します。
3. `classList`を使って、クラスを追加または削除します。

## 例
### 1. インラインスタイルの変更
```javascript
const element = document.getElementById('myElement');
element.style.color = 'red'; // 文字色を赤に変更
```

### 2. クラスの追加
```javascript
const element = document.getElementById('myElement');
element.classList.add('active'); // 'active'クラスを追加
```

### 3. クラスの削除
```javascript
const element = document.getElementById('myElement');
element.classList.remove('active'); // 'active'クラスを削除
```

### 4. スタイルの取得
```javascript
const element = document.getElementById('myElement');
const computedStyle = window.getComputedStyle(element);
console.log(computedStyle.color); // 要素の文字色を取得
```

## 説明
JavaScriptを使用してCSSを操作する際の一般的な落とし穴は、スタイルの優先順位を理解していないことです。また、`style`プロパティを使うとインラインスタイルが適用され、他のスタイルシートのスタイルを上書きする場合があります。クラスを使用する方が、スタイルの管理が容易です。

## 一文要約
JavaScriptを使ってCSSスタイルを動的に変更することで、インタラクティブで魅力的なウェブページを作成できます。