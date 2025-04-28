<!--
Meta Description: # JavaScriptのonpopstateイベント：履歴管理の重要な要素 ## 概要 `onpopstate`イベントは、JavaScriptでブラウザの履歴管理を行うための重要な機能です。このイベントは、ユーザーがブラウザの「戻る」や「進む」ボタンを使用した際に発火し、履歴の変更を検知できます...
Meta Keywords: onpopstate, event, state, history, pushstate
-->

# JavaScriptのonpopstateイベント：履歴管理の重要な要素

## 概要
`onpopstate`イベントは、JavaScriptでブラウザの履歴管理を行うための重要な機能です。このイベントは、ユーザーがブラウザの「戻る」や「進む」ボタンを使用した際に発火し、履歴の変更を検知できます。

## ドキュメンテーション
### 目的
`onpopstate`イベントは、ブラウザのセッション履歴が変更されたときに発生します。特に、`history.pushState()`または`history.replaceState()`メソッドで追加された履歴エントリを視覚的に変更する手段として利用されます。

### 使用法
このイベントは、`window`オブジェクトまたは`history`オブジェクト上でリスナーとして登録されます。以下は基本的な使い方です。

```javascript
window.onpopstate = function(event) {
    if (event.state) {
        console.log("State: ", event.state);
    } else {
        console.log("No state information available.");
    }
};
```

### 詳細
- `event.state`: `onpopstate`イベントが発生した際に、状態オブジェクトを取得できます。これは`history.pushState()`または`history.replaceState()`で設定されたデータです。
- イベントは、ユーザーがブラウザの履歴を操作した場合にのみ発生します。URLが変更されるが、ページがリロードされない場合に役立ちます。

## 例
### 基本的な使用例

```javascript
// 状態を追加
history.pushState({ page: 1 }, "title 1", "?page=1");
history.pushState({ page: 2 }, "title 2", "?page=2");

window.onpopstate = function(event) {
    if (event.state) {
        console.log("戻ったページ: ", event.state.page);
    }
};

// ボタンをクリックして履歴を戻すと、onpopstateが発火
```

## 説明
`onpopstate`イベントを使用する際の一般的な落とし穴として、以下の点に注意が必要です。

1. **状態がないとき**: `event.state`が`null`の場合、`pushState`や`replaceState`で状態が設定されていないことを意味します。
2. **URLの変更**: `onpopstate`は、`pushState`や`replaceState`で追加された状態があるときのみ発火します。そのため、リロードや初回のページ読み込み時には発火しません。
3. **複数のリスナー**: `onpopstate`に複数のリスナーを追加した場合、最後に設定したリスナーのみが実行されます。

## ワンラインサマリー
`onpopstate`イベントは、ブラウザの履歴操作に応じて状態を管理するためのJavaScriptの重要な機能です。