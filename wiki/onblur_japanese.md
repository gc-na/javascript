<!--
Meta Description: # JavaScriptのonblurイベントハンドラ：使い方と例 ## 概要 `onblur`は、JavaScriptにおけるイベントハンドラで、要素がフォーカスを失ったときに発生します。このイベントは、フォーム入力やボタン、テキストエリアなどのインタラクティブな要素で特に有用です。 ## ドキュ...
Meta Keywords: onblur, html, myinput, head, title
-->

# JavaScriptのonblurイベントハンドラ：使い方と例

## 概要
`onblur`は、JavaScriptにおけるイベントハンドラで、要素がフォーカスを失ったときに発生します。このイベントは、フォーム入力やボタン、テキストエリアなどのインタラクティブな要素で特に有用です。

## ドキュメンテーション
### 目的
`onblur`イベントは、ユーザーが要素からフォーカスを外した際に何らかの処理を実行するために使用されます。これにより、入力の検証やユーザーインターフェースの改善が可能になります。

### 使用法
`onblur`は、HTML要素に直接指定することができ、JavaScriptではイベントリスナーとしても利用できます。以下のように使用します。

#### HTMLでの指定
```html
<input type="text" onblur="myFunction()">
```

#### JavaScriptでの指定
```javascript
document.getElementById("myInput").onblur = function() {
    myFunction();
};
```

### 詳細
`onblur`イベントは、通常、フォームの入力フィールドやボタンなど、ユーザーが操作する要素に関連付けられます。このイベントが発生する主なシナリオは以下の通りです：

- ユーザーが他の要素をクリックしたとき
- ユーザーがキーボードのタブキーを押してフォーカスを移動したとき

なお、`onblur`はバブリングしないため、親要素での`blur`イベントリスナーは実行されません。

## 例
以下の例では、テキスト入力フィールドからフォーカスが外れたときにアラートを表示します。

### 基本例
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>onblurイベントの例</title>
</head>
<body>
    <input type="text" id="myInput" onblur="alert('フォーカスが外れました！');">
</body>
</html>
```

### JavaScriptによる例
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>onblurイベントのJavaScript例</title>
</head>
<body>
    <input type="text" id="myInput">
    <script>
        document.getElementById("myInput").onblur = function() {
            alert('フォーカスが外れました！');
        };
    </script>
</body>
</html>
```

## 説明
`onblur`イベントを使用する際の一般的な注意点：

- **イベントの流れ**: `onblur`はバブリングしないため、親要素での`blur`イベントは処理されません。必要に応じて、各要素に個別にイベントリスナーを追加する必要があります。
- **フォーカスの移動**: フォーカスを失うと、`onblur`イベントが発生しますが、要素が無効化されている場合や、DOMから削除された場合は発生しません。
- **デフォルトアクション**: `onblur`の実行中に、ユーザーが別の要素にフォーカスを移動することができるため、処理が完了する前に他のアクションが発生する可能性があります。

## 一文要約
`onblur`は、JavaScriptにおいて要素がフォーカスを失ったときに発生するイベントで、ユーザーインターフェースの動的な改善に役立ちます。