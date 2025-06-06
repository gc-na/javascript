<!--
Meta Description: # JavaScriptの「blur」イベント：使い方と注意点 ## 概要 JavaScriptにおける「blur」イベントは、ユーザーが入力フィールドや要素からフォーカスを外したときに発生します。このイベントは、ユーザーインターフェースの制御やデータ検証に役立ちます。 ## ドキュメンテーション ...
Meta Keywords: blur, イベントは, input, javascriptの, addeventlistener
-->

# JavaScriptの「blur」イベント：使い方と注意点

## 概要
JavaScriptにおける「blur」イベントは、ユーザーが入力フィールドや要素からフォーカスを外したときに発生します。このイベントは、ユーザーインターフェースの制御やデータ検証に役立ちます。

## ドキュメンテーション
### 目的
「blur」イベントは、特定の要素がフォーカスを失った際にトリガーされ、主にフォームのバリデーションやユーザーの入力を扱う際に使用されます。

### 使用法
`blur`イベントは、DOM要素に対してリスナーを追加することで使用します。以下は基本的な構文です。

```javascript
element.addEventListener('blur', function(event) {
    // イベントが発生したときの処理
});
```

### 詳細
- **対象要素**: `blur`イベントは、`input`、`textarea`、`select`などのフォーム要素に加え、任意のHTML要素に対しても使用可能です。
- **イベントオブジェクト**: `blur`イベントが発生すると、イベントオブジェクトがコールバック関数に渡され、対象要素の情報を取得できます。
- **フォーカスと逆**: `focus`イベントと対になるイベントであり、ユーザーが要素にフォーカスを当てたときは`focus`、外したときは`blur`が発生します。

## 例
以下は、`input`要素に対する`blur`イベントの基本的な使用例です。

```html
<input type="text" id="myInput" placeholder="名前を入力してください">

<script>
    const inputElement = document.getElementById('myInput');

    inputElement.addEventListener('blur', function() {
        alert('フォーカスが外れました。');
    });
</script>
```

この例では、ユーザーが入力フィールドからフォーカスを外すとアラートが表示されます。

## 説明
### 一般的な落とし穴
- **イベントのバブリング**: `blur`イベントはバブリングしません。これにより、親要素に設定されたイベントリスナーがトリガーされないことに注意が必要です。
- **フォーカス移動**: ユーザーが他の要素にフォーカスを移動した場合、`blur`イベントが発生しますが、意図しない動作が起こることがあります。特に、フォーカスを移動する要素が動的に変更される場合は、注意が必要です。
- **ブラウザ互換性**: ほとんどのモダンブラウザでサポートされていますが、古いブラウザでは動作が異なることがあります。

## 1行要約
JavaScriptの`blur`イベントは、ユーザーが要素からフォーカスを外したときにトリガーされ、フォームバリデーションなどに利用されます。