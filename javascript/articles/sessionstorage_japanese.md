<!--
Meta Description: # sessionStorage: JavaScriptのセッションストレージ機能 ## 概要 `sessionStorage`は、Webブラウザでのセッション中にデータを保存するためのJavaScriptのオブジェクトです。このストレージは、ユーザーがブラウザタブを閉じるまでデータを保持します。セ...
Meta Keywords: sessionstorage, username, key, json, taro
-->

# sessionStorage: JavaScriptのセッションストレージ機能

## 概要
`sessionStorage`は、Webブラウザでのセッション中にデータを保存するためのJavaScriptのオブジェクトです。このストレージは、ユーザーがブラウザタブを閉じるまでデータを保持します。セッションストレージは、クライアント側での一時的なデータ管理に最適です。

## ドキュメント
### 目的
`sessionStorage`は、ドメインごとにデータを保存するためのAPIを提供します。このデータは、同じタブまたはウィンドウでのページ遷移間で保持されますが、タブを閉じると消去されます。

### 使用法
`sessionStorage`オブジェクトは、以下のメソッドとプロパティを提供します。

- **setItem(key, value)**: 指定したキーに対する値を保存します。
- **getItem(key)**: 指定したキーに対応する値を取得します。
- **removeItem(key)**: 指定したキーに対応する値を削除します。
- **clear()**: セッションストレージ内のすべてのデータを削除します。
- **length**: ストレージに保存されているアイテムの数を返します。
- **key(index)**: 指定したインデックスのキーを取得します。

### 詳細
`sessionStorage`は、ブラウザのストレージAPIの一部であり、特にクライアントサイドのデータ管理に利用されます。データは文字列として保存されるため、オブジェクトや配列を保存する場合は、`JSON.stringify()`を使用して文字列化し、取得時には`JSON.parse()`で復元する必要があります。

## 例
### 基本的な使用例
```javascript
// データの保存
sessionStorage.setItem('username', 'taro');

// データの取得
const username = sessionStorage.getItem('username');
console.log(username); // "taro"

// データの削除
sessionStorage.removeItem('username');

// ストレージのクリア
sessionStorage.clear();
```

### オブジェクトの保存
```javascript
const user = { name: 'taro', age: 25 };
sessionStorage.setItem('user', JSON.stringify(user));

// オブジェクトの取得
const retrievedUser = JSON.parse(sessionStorage.getItem('user'));
console.log(retrievedUser.name); // "taro"
```

## 説明
`sessionStorage`の一般的な落とし穴として、データがブラウザタブを閉じると消えてしまうことが挙げられます。これにより、ユーザーが再度訪れた際にデータが失われるため、長期的なデータ保存には向いていません。また、`sessionStorage`は同一オリジンポリシーに従うため、異なるドメインやサブドメインからはアクセスできません。

さらに、`sessionStorage`はストレージの上限があり、ブラウザによって異なりますが、通常は5MB程度です。大量のデータを保存する場合は、他のストレージオプションを検討する必要があります。

## 一文要約
`sessionStorage`は、ブラウザセッション中にデータを一時的に保存するためのJavaScriptオブジェクトです。