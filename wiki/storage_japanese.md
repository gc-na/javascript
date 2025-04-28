<!--
Meta Description: # JavaScriptにおけるストレージ (Storage) ## 概要 JavaScriptにおけるストレージは、Webアプリケーションがデータをクライアント側に保存するためのメカニズムです。主に`localStorage`と`sessionStorage`の2つのストレージオプションがあり、ユ...
Meta Keywords: localstorage, sessionstorage, key, username, sessionid
-->

# JavaScriptにおけるストレージ (Storage)

## 概要
JavaScriptにおけるストレージは、Webアプリケーションがデータをクライアント側に保存するためのメカニズムです。主に`localStorage`と`sessionStorage`の2つのストレージオプションがあり、ユーザーのブラウザにデータを保存することができます。

## ドキュメンテーション
JavaScriptのストレージAPIは、Web Storage APIとして知られ、以下の2つの主要なストレージオプションを提供します。

### localStorage
- **目的**: 永続的にデータを保存します。ブラウザを閉じてもデータが保持されます。
- **使用方法**: `localStorage.setItem('key', 'value')`でデータを保存し、`localStorage.getItem('key')`でデータを取得します。削除は`localStorage.removeItem('key')`、全削除は`localStorage.clear()`です。
  
### sessionStorage
- **目的**: セッション中のみデータを保存します。タブを閉じるとデータは消えます。
- **使用方法**: `sessionStorage.setItem('key', 'value')`でデータを保存し、`sessionStorage.getItem('key')`でデータを取得します。削除は`sessionStorage.removeItem('key')`、セッション全体のデータを削除するには`sessionStorage.clear()`を使用します。

両者は、同じインターフェースを持ちますが、データの持続性が異なります。

## 例
### localStorageの例
```javascript
// データの保存
localStorage.setItem('username', 'JohnDoe');

// データの取得
const username = localStorage.getItem('username');
console.log(username); // "JohnDoe"

// データの削除
localStorage.removeItem('username');

// 全データの削除
localStorage.clear();
```

### sessionStorageの例
```javascript
// データの保存
sessionStorage.setItem('sessionId', '123456');

// データの取得
const sessionId = sessionStorage.getItem('sessionId');
console.log(sessionId); // "123456"

// データの削除
sessionStorage.removeItem('sessionId');

// 全データの削除
sessionStorage.clear();
```

## 説明
- **ストレージの制限**: `localStorage`と`sessionStorage`には、一般的に5MBの制限があります。これはブラウザによって異なる場合がありますので、注意が必要です。
- **データの型**: ストレージには文字列のみを保存できます。他の型のデータを保存する場合は、JSON.stringify()を使用して文字列に変換し、取得時にはJSON.parse()を使用して元の型に戻す必要があります。
- **クロスドメイン制限**: 各ドメインごとにストレージが分離されているため、異なるドメイン間でデータを共有することはできません。

## 一文要約
JavaScriptのストレージAPIは、`localStorage`と`sessionStorage`を通じてクライアント側にデータを保存し、管理するための便利な方法を提供します。