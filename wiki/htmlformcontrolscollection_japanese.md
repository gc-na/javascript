<!--
Meta Description: # HTMLFormControlsCollection：JavaScriptにおけるHTMLフォームコントロールのコレクション ## 概要 `HTMLFormControlsCollection`は、HTMLフォーム内のすべてのフォームコントロールを表すオブジェクトです。このコレクションは、フォー...
Meta Keywords: htmlformcontrolscollection, form, name, elements, const
-->

# HTMLFormControlsCollection：JavaScriptにおけるHTMLフォームコントロールのコレクション

## 概要
`HTMLFormControlsCollection`は、HTMLフォーム内のすべてのフォームコントロールを表すオブジェクトです。このコレクションは、フォームの要素（入力フィールド、ボタンなど）にアクセスし、操作するための便利な方法を提供します。

## ドキュメント
`HTMLFormControlsCollection`は、HTML文書内のフォーム要素を管理するために使用されます。フォームコントロールは、一般的に`<input>`, `<select>`, `<textarea>`, 及び`<button>`要素で構成されます。このコレクションは、これらの要素に対してインデックスや名前を使用してアクセスすることができるため、開発者はフォームデータの取得や操作を容易に行えます。

### 使用法
`HTMLFormControlsCollection`は、通常`<form>`要素の`elements`プロパティを通じて取得されます。以下のように使用します。

```javascript
const form = document.querySelector('form');
const controls = form.elements;
```

### 詳細
- **取得方法**: `elements`プロパティは、フォーム内のすべてのコントロールを含む`HTMLFormControlsCollection`オブジェクトを返します。
- **インデックスアクセス**: コレクションは配列のようにインデックスを使用してアクセスできます。
- **名前アクセス**: 各コントロールは`name`属性を持つ場合、名前をキーとしてアクセスすることも可能です。

## 例
以下は、`HTMLFormControlsCollection`を使用してフォームコントロールにアクセスする基本的な例です。

```html
<form id="myForm">
    <input type="text" name="username" />
    <input type="password" name="password" />
    <button type="submit">送信</button>
</form>

<script>
    const form = document.getElementById('myForm');
    const controls = form.elements;

    console.log(controls[0].name); // 'username'
    console.log(controls['password'].type); // 'password'
</script>
```

## 説明
`HTMLFormControlsCollection`を使用する際の注意点やよくある落とし穴について説明します。

- **コレクションの長さ**: `length`プロパティを使用して、コレクション内の要素数を確認できますが、動的に変更されることがあります。要素が追加または削除されると、`length`は自動的に更新されます。
- **名前の重複**: 同じ`name`属性を持つ複数のフォームコントロールがある場合、配列のようにインデックスでアクセスすることが必要です。
- **フォームの送信**: フォームが送信されると、コントロールの値はサーバーに送信されます。JavaScriptでの操作が必要な場合は、送信イベントを適切に処理する必要があります。

## 一文要約
`HTMLFormControlsCollection`は、HTMLフォーム内の全てのフォームコントロールを管理し、操作するための便利なオブジェクトです。