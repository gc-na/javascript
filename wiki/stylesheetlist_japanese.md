<!--
Meta Description: # StyleSheetList: JavaScriptにおけるスタイルシートの管理 ## 概要 `StyleSheetList`は、JavaScriptでスタイルシートのコレクションを表現するオブジェクトです。これにより、HTML文書に関連付けられたすべてのスタイルシートにアクセスし、操作すること...
Meta Keywords: stylesheets, stylesheetlist, document, console, log
-->

# StyleSheetList: JavaScriptにおけるスタイルシートの管理

## 概要
`StyleSheetList`は、JavaScriptでスタイルシートのコレクションを表現するオブジェクトです。これにより、HTML文書に関連付けられたすべてのスタイルシートにアクセスし、操作することが可能になります。

## ドキュメンテーション
`StyleSheetList`は、`document.styleSheets`プロパティを使用して取得できるオブジェクトです。このプロパティは、ページに読み込まれたすべてのスタイルシートをリスト形式で提供します。各スタイルシートは、`CSSStyleSheet`オブジェクトとして表現され、スタイルの追加、削除、変更が可能です。

### 使用方法
```javascript
const styleSheets = document.styleSheets; // StyleSheetListの取得
console.log(styleSheets.length); // スタイルシートの数を表示

// 各スタイルシートをループ処理
for (let i = 0; i < styleSheets.length; i++) {
    console.log(styleSheets[i].href); // 各スタイルシートのURLを表示
}
```

### 詳細
- **プロパティ**: `StyleSheetList`は、スタイルシートの数やそれぞれのスタイルシートへのアクセスを提供するプロパティを持っています。
- **メソッド**: `StyleSheetList`自体には特別なメソッドはありませんが、各スタイルシートは`CSSStyleSheet`オブジェクトとしてメソッドを持っています。

## 例
### 基本の使用例
```javascript
// スタイルシートの数を取得
console.log(`スタイルシートの数: ${document.styleSheets.length}`);

// スタイルシートのURLを出力
for (let i = 0; i < document.styleSheets.length; i++) {
    console.log(`スタイルシート ${i}: ${document.styleSheets[i].href}`);
}
```

### スタイルシートの新規追加
```javascript
const newStyle = document.createElement('link');
newStyle.rel = 'stylesheet';
newStyle.href = 'styles.css'; // 新しいスタイルシートのURL
document.head.appendChild(newStyle);
console.log(`新しいスタイルシートが追加されました: ${newStyle.href}`);
```

## 説明
`StyleSheetList`を使用する際の一般的な注意点として、スタイルシートの追加や削除がDOMの変更を伴うため、ページのリフローを引き起こす可能性があります。また、外部スタイルシートが読み込まれていない場合、`href`プロパティは`null`になります。このため、存在しないスタイルシートを扱う際は、適切なエラーチェックを行うことが推奨されます。

## 一文要約
`StyleSheetList`は、JavaScriptを用いてHTML文書内のすべてのスタイルシートにアクセスし、操作するためのオブジェクトです。