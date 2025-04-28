<!--
Meta Description: # JavaScriptのonbeforeunloadイベント: ページ離脱時の確認ダイアログ ## 概要 `onbeforeunload`は、ユーザーがウェブページを離れようとした際に確認ダイアログを表示するためのイベントです。このイベントは、ページの内容が未保存である場合や、ユーザーが意図しない...
Meta Keywords: event, onbeforeunload, window, preventdefault, returnvalue
-->

# JavaScriptのonbeforeunloadイベント: ページ離脱時の確認ダイアログ

## 概要
`onbeforeunload`は、ユーザーがウェブページを離れようとした際に確認ダイアログを表示するためのイベントです。このイベントは、ページの内容が未保存である場合や、ユーザーが意図しない離脱を防ぐために便利です。

## ドキュメンテーション

### 目的
`onbeforeunload`イベントは、ユーザーがページをリロードしたり、別のURLに移動したり、タブを閉じたりする際に発生します。このイベントを使用することで、ユーザーに対して「本当にページを離れますか？」という警告を表示できます。

### 使用方法
`onbeforeunload`イベントは、`window`オブジェクトのプロパティとして設定します。以下のように、イベントリスナーを追加することで実装できます。

```javascript
window.onbeforeunload = function(event) {
    event.preventDefault(); // 標準の動作を防ぐ
    event.returnValue = ''; // ダイアログを表示するための値
};
```

### 詳細
- `event.preventDefault()`メソッドは、ブラウザのデフォルトの動作をキャンセルします。
- `event.returnValue`に空文字を設定することで、確認ダイアログが表示されます。ブラウザによっては、カスタムメッセージは表示されず、標準の警告メッセージが表示される場合があります。

## 例

### 基本的な使用例
以下は、ページ離脱時に確認ダイアログを表示する基本的な例です。

```javascript
window.onbeforeunload = function(event) {
    event.preventDefault();
    event.returnValue = '未保存の変更があります。ページを離れますか？';
};
```

### 条件付きでの使用例
特定の条件下でのみダイアログを表示することも可能です。

```javascript
let isUnsaved = true; // 変更が未保存かどうかのフラグ

window.onbeforeunload = function(event) {
    if (isUnsaved) {
        event.preventDefault();
        event.returnValue = '未保存の変更があります。ページを離れますか？';
    }
};
```

## 解説
- **共通の落とし穴**: 一部のブラウザでは、カスタムメッセージが無視され、標準のメッセージしか表示されないことがあります。また、最新のブラウザでは、ユーザー体験を重視するため、無闇にダイアログを表示することが制限されています。
- **パフォーマンスへの影響**: `onbeforeunload`イベントを多用することは、ユーザーにとって煩わしい体験となるため、適切に使用することが重要です。特に、ユーザーの行動を過剰に制約することは避けましょう。

## 一文要約
`onbeforeunload`は、ユーザーがページを離れる際に確認ダイアログを表示するためのJavaScriptのイベントです。