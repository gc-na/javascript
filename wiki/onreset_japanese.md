<!--
Meta Description: # onreset: JavaScriptにおけるリセットイベントの活用法 ## 概要 `onreset`は、HTMLフォームがリセットされたときに発生するイベントです。このイベントは、ユーザーがフォーム内の入力を初期状態に戻したときにトリガーされ、JavaScriptで特定の処理を実行するのに役立...
Meta Keywords: onreset, form, html, reset, input
-->

# onreset: JavaScriptにおけるリセットイベントの活用法

## 概要
`onreset`は、HTMLフォームがリセットされたときに発生するイベントです。このイベントは、ユーザーがフォーム内の入力を初期状態に戻したときにトリガーされ、JavaScriptで特定の処理を実行するのに役立ちます。

## ドキュメンテーション
`onreset`イベントは、HTMLフォーム内で`<form>`要素の`reset`メソッドやリセットボタンを使用した際に発生します。このイベントを利用することで、フォームがリセットされた際に特定のアクションを実行することができます。

### 使用方法
`onreset`イベントは、次のようにHTMLの`<form>`タグに直接指定するか、JavaScriptを使用してイベントリスナーを追加することで設定できます。

#### HTMLでの設定例
```html
<form onreset="handleReset()">
  <input type="text" name="name" value="初期値">
  <input type="reset" value="リセット">
</form>
```

#### JavaScriptでの設定例
```javascript
document.querySelector('form').onreset = function(event) {
  console.log('フォームがリセットされました');
};
```

## 例
### 基本的な使用例
以下は、`onreset`イベントを使用してフォームがリセットされた際にメッセージを表示する例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>onresetイベントの例</title>
</head>
<body>
    <form id="myForm" onreset="handleReset()">
        <input type="text" name="username" placeholder="ユーザー名">
        <input type="reset" value="リセット">
    </form>

    <script>
        function handleReset() {
            alert('フォームがリセットされました！');
        }
    </script>
</body>
</html>
```

## 説明
`onreset`イベントを使用する際の一般的な注意点は以下の通りです。

1. **リセットボタンの使用**: `onreset`イベントは、通常リセットボタンをクリックしたときにのみ発生します。JavaScriptから`reset()`メソッドを呼び出す場合も同様です。
2. **フォームの初期値に注意**: フォームの初期値が設定されていない場合、リセット時に何も変化がないように見えることがあります。
3. **イベントの伝播**: `onreset`イベントは他のイベントと同様に伝播します。必要に応じて`event.stopPropagation()`を使用して、伝播を制御することができます。

## 一文の要約
`onreset`は、HTMLフォームがリセットされた際にトリガーされるイベントで、ユーザーの入力を初期状態に戻す際に特定のアクションを実行するために使用されます。