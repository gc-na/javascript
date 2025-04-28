<!--
Meta Description: # JavaScriptの「onstorage」イベントに関する完全ガイド ## 概要 `onstorage`は、Web Storage APIの一部であり、ローカルストレージまたはセッションストレージのデータが変更されたときに発生するイベントです。このイベントは、異なるブラウザタブやウィンドウ間で...
Meta Keywords: onstorage, event, localstorage, イベントは, window
-->

# JavaScriptの「onstorage」イベントに関する完全ガイド

## 概要
`onstorage`は、Web Storage APIの一部であり、ローカルストレージまたはセッションストレージのデータが変更されたときに発生するイベントです。このイベントは、異なるブラウザタブやウィンドウ間でデータの同期を可能にします。

## ドキュメンテーション
### 目的
`onstorage`イベントは、同一オリジン内の異なるウィンドウやタブでのストレージの変更を監視するために使用されます。これにより、ユーザーが別のタブで行った変更が、他のタブに即座に反映されることが可能になります。

### 使用法
`onstorage`イベントは、`window`オブジェクトのプロパティとして設定されます。以下は基本的な構文です。

```javascript
window.onstorage = function(event) {
    // イベントハンドラーの処理
};
```

### 詳細
`onstorage`イベントが発生すると、イベントオブジェクトが生成され、以下のプロパティを持ちます：

- **key**: 変更されたストレージアイテムのキー。
- **newValue**: 新しく設定された値。
- **oldValue**: 変更前の値。
- **url**: 変更が行われたページのURL。
- **storageArea**: 変更が行われたストレージエリア（`localStorage`または`sessionStorage`）。

## 例
以下は、`onstorage`イベントを使用した基本的な例です。

```javascript
// ストレージイベントのリスナーを設定
window.onstorage = function(event) {
    console.log("キー: " + event.key);
    console.log("新しい値: " + event.newValue);
    console.log("古い値: " + event.oldValue);
};

// ローカルストレージにアイテムを追加
localStorage.setItem('exampleKey', 'exampleValue');
```

この例では、他のタブで`localStorage`が変更されたときに、変更内容がコンソールに出力されます。

## 説明
`onstorage`イベントにはいくつかの注意点があります：

- **同一オリジン制約**: `onstorage`イベントは、同一オリジン内でのみ発生します。異なるオリジンではイベントは発火しません。
- **新しいタブでの変更**: `localStorage`や`sessionStorage`の変更は、同じオリジンの他のタブでのみ`onstorage`イベントを発火させます。
- **ブラウザのサポート**: ほとんどの最新ブラウザは`onstorage`イベントをサポートしていますが、古いブラウザでは動作しないことがあります。

## 一文要約
`onstorage`は、Web Storage APIにおいてローカルストレージまたはセッションストレージのデータが変更された際に発生するイベントで、異なるタブ間でのデータの同期を可能にします。