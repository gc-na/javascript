<!--
Meta Description: # onauxclick: JavaScriptにおける非標準イベントハンドラ ## 概要 `onauxclick`は、JavaScriptにおいてマウスの補助ボタンがクリックされたときにトリガーされる非標準のイベントハンドラです。特に、マウスの中ボタン（ホイールボタン）や追加のボタンでのクリックを...
Meta Keywords: onauxclick, button, event, html, function
-->

# onauxclick: JavaScriptにおける非標準イベントハンドラ

## 概要
`onauxclick`は、JavaScriptにおいてマウスの補助ボタンがクリックされたときにトリガーされる非標準のイベントハンドラです。特に、マウスの中ボタン（ホイールボタン）や追加のボタンでのクリックを検出するのに使用されます。

## ドキュメンテーション
`onauxclick`イベントは、ユーザーがマウスの補助ボタンをクリックした際に発生します。このイベントは、特定のブラウザ環境でのみサポートされており、標準的な`click`イベントとは異なる動作をします。

### 目的
このイベントを使用することによって、ユーザーの特定のマウス操作に基づくインタラクションを実装することができます。例えば、ユーザーが中ボタンで特定のアクションをトリガーしたい場合に便利です。

### 使用法
`onauxclick`は、HTML要素に直接設定するか、JavaScriptを使用してイベントリスナーを追加することで使用できます。以下はその基本的な構文です。

```javascript
element.onauxclick = function(event) {
    // イベントに対する処理
};
```

または、`addEventListener`メソッドを使用して以下のように設定できます。

```javascript
element.addEventListener('auxclick', function(event) {
    // イベントに対する処理
});
```

## 例
以下に`onauxclick`の基本的な使用例を示します。

### 例1: 中ボタンのクリックを検出する

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>onauxclickの例</title>
</head>
<body>
    <button id="testButton">中ボタンをクリックしてください</button>
    <script>
        const button = document.getElementById('testButton');

        button.onauxclick = function(event) {
            if (event.button === 1) { // 中ボタンの識別
                alert('中ボタンがクリックされました！');
            }
        };
    </script>
</body>
</html>
```

## 説明
`onauxclick`を使用する際の注意点や一般的な落とし穴について説明します。

- **ブラウザサポート**: `onauxclick`はすべてのブラウザでサポートされているわけではありません。特に、モバイルブラウザではこのイベントは発生しません。
- **イベントのプロパティ**: `event.button`プロパティを使用して、どのボタンがクリックされたかを判別できます。0は左ボタン、1は中ボタン、2は右ボタンを表します。
- **非標準性**: `onauxclick`は非標準イベントであるため、将来的に仕様が変更される可能性があります。使用する際はその点を考慮してください。

## 一文要約
`onauxclick`は、JavaScriptにおいてマウスの補助ボタンがクリックされたときに発生する非標準のイベントハンドラです。