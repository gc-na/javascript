<!--
Meta Description: # JavaScriptの「onstalled」イベントについて ## 概要 「onstalled」は、Web API、特に`XMLHttpRequest`や`Fetch API`に関連するイベントで、リクエストが中断されたときに発生します。このイベントは、データの取得が途中で止まった場合にトラブル...
Meta Keywords: onstalled, xhr, xmlhttprequest, function, イベントは
-->

# JavaScriptの「onstalled」イベントについて

## 概要
「onstalled」は、Web API、特に`XMLHttpRequest`や`Fetch API`に関連するイベントで、リクエストが中断されたときに発生します。このイベントは、データの取得が途中で止まった場合にトラブルシューティングを行うために役立ちます。

## ドキュメント
### 目的
`onstalled`イベントは、リクエストが予期せず中断されたことを通知します。これにより、開発者は適切なエラーハンドリングを実装し、ユーザーにフィードバックを提供することができます。

### 使用法
`onstalled`イベントは、`XMLHttpRequest`オブジェクトのプロパティとして設定されます。以下は、基本的な構文です。

```javascript
let xhr = new XMLHttpRequest();

xhr.onprogress = function () {
  // リクエストが進行中の時の処理
};

xhr.onstalled = function () {
  console.error("リクエストが中断されました。");
};

xhr.open("GET", "https://example.com/data", true);
xhr.send();
```

この例では、リクエストの進行中に`onstalled`イベントが発生すると、エラーメッセージがコンソールに表示されます。

## 例
### 基本的な使用例

```javascript
let xhr = new XMLHttpRequest();

xhr.onload = function () {
  console.log("データ取得成功:", xhr.responseText);
};

xhr.onstalled = function () {
  console.log("リクエストが中断されました。");
};

xhr.open("GET", "https://example.com/data", true);
xhr.send();
```

このコードは、指定されたURLからデータを取得し、リクエストが中断された場合にメッセージを表示します。

## 説明
`onstalled`イベントの主な落とし穴は、リクエストが本当に中断されたのか、または他の要因によるものなのかを区別することです。例えば、ネットワークの問題やサーバーの応答が遅い場合にも`onstalled`が発生することがあります。また、`onstalled`イベントが発生した場合でも、リクエストが再開することがあるため、必ずしもエラーではありません。

## 一行要約
JavaScriptの`onstalled`イベントは、リクエストが中断された際に発生し、エラーハンドリングの実装に役立ちます。