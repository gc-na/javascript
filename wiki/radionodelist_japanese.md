<!--
Meta Description: # RadioNodeList: JavaScriptにおけるラジオボタンのリスト操作 ## 概要 `RadioNodeList`は、HTMLドキュメント内のラジオボタンの集合を表すオブジェクトであり、JavaScriptを使用して操作することができます。このオブジェクトは、特にフォーム要素の管理や...
Meta Keywords: radionodelist, radio, input, type, name
-->

# RadioNodeList: JavaScriptにおけるラジオボタンのリスト操作

## 概要
`RadioNodeList`は、HTMLドキュメント内のラジオボタンの集合を表すオブジェクトであり、JavaScriptを使用して操作することができます。このオブジェクトは、特にフォーム要素の管理やユーザーの選択を取得する際に役立ちます。

## ドキュメンテーション
`RadioNodeList`は、`HTMLFormControlsCollection`のサブクラスであり、同じ名前を持つラジオボタンのグループを表します。このオブジェクトは、`document.forms`や`form`要素の中の`input`要素を通じて取得されます。ラジオボタンは、ユーザーが複数の選択肢から1つを選択するためのUI要素です。

### 使用方法
`RadioNodeList`は、次のようにして取得できます。

```javascript
const radios = document.querySelectorAll('input[type="radio"][name="groupName"]');
```

ここで、`groupName`は関連するラジオボタングループの名前です。`radios`は`NodeList`を返しますが、`RadioNodeList`として扱うことができます。

### 詳細
`RadioNodeList`には、以下のプロパティとメソッドがあります：

- **length**: ラジオボタンの数を返します。
- **item(index)**: 指定したインデックスのラジオボタンを返します。
- **forEach(callback)**: 各ラジオボタンに対してコールバック関数を実行します。

## 例
以下は、`RadioNodeList`を使用してラジオボタンの選択を取得する基本的な例です。

```html
<form id="myForm">
  <input type="radio" name="color" value="red"> Red<br>
  <input type="radio" name="color" value="blue"> Blue<br>
  <input type="radio" name="color" value="green"> Green<br>
</form>
<button id="submitBtn">Submit</button>

<script>
  document.getElementById('submitBtn').addEventListener('click', function() {
    const radios = document.querySelectorAll('input[type="radio"][name="color"]');
    let selectedValue;
    radios.forEach(radio => {
      if (radio.checked) {
        selectedValue = radio.value;
      }
    });
    alert('選択された色: ' + selectedValue);
  });
</script>
```

このスクリプトは、ユーザーが選択したラジオボタンの値を取得し、アラートで表示します。

## 説明
`RadioNodeList`を使用する際の一般的な注意点や罠には以下のようなものがあります：

- **選択肢が未選択の場合**: すべてのラジオボタンが未選択の場合、`selectedValue`は`undefined`になります。適切なエラーハンドリングが必要です。
- **NodeListとRadioNodeListの違い**: `NodeList`は静的なリストであり、DOMの変更があっても自動的に更新されませんが、`RadioNodeList`は特定の名前のグループ内のラジオボタンを動的に反映します。
- **フォーム送信時の挙動**: フォームが送信されると、選択されたラジオボタンの値が自動的にサーバーに送信されるため、JavaScriptでの処理が必要ない場合もあります。

## 一文要約
`RadioNodeList`は、JavaScriptを使用してHTML内のラジオボタンの選択を管理するための便利なオブジェクトです。