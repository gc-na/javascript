<!--
Meta Description: # JavaScriptにおけるキーボードイベントの完全ガイド ## 概要 JavaScriptでは、キーボードイベントを使用してユーザーのキーボード入力を管理できます。これにより、Webアプリケーションはユーザーからの入力に対して動的に反応することが可能になります。 ## ドキュメンテーション キ...
Meta Keywords: event, key, keydown, addeventlistener, enter
-->

# JavaScriptにおけるキーボードイベントの完全ガイド

## 概要
JavaScriptでは、キーボードイベントを使用してユーザーのキーボード入力を管理できます。これにより、Webアプリケーションはユーザーからの入力に対して動的に反応することが可能になります。

## ドキュメンテーション
キーボードイベントは、ユーザーがキーボードのキーを押したり離したりしたときに発生します。主に以下の3つのイベントが使用されます。

1. **keydown**: キーが押されたときに発生します。
2. **keypress**: 押されたキーが文字を生成する場合に発生します（非推奨）。
3. **keyup**: キーが離されたときに発生します。

### 使用法
キーボードイベントをリッスンするには、`addEventListener`メソッドを使用します。例えば、次のように記述します。

```javascript
document.addEventListener('keydown', function(event) {
    console.log('Key pressed: ', event.key);
});
```

### 詳細
- **event.key**: 押されたキーの値を返します（例: "a", "Enter", "Shift"）。
- **event.code**: 押されたキーの物理的位置を示します（例: "KeyA", "Enter"）。
- **event.altKey, event.ctrlKey, event.shiftKey**: 修飾キーが押されているかどうかを確認できます。

## 例
### 基本的な使用例

```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        console.log('Enter key was pressed');
    }
});
```

### 複数キーの組み合わせ

```javascript
document.addEventListener('keydown', function(event) {
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault(); // デフォルトの保存動作を防ぐ
        console.log('Ctrl + S was pressed');
    }
});
```

## 説明
- **非推奨のkeypressイベント**: `keypress`イベントは、すべてのブラウザで一貫してサポートされていないため、`keydown`または`keyup`を使用することが推奨されます。
- **デフォルト動作の防止**: 特定のキー操作（例: Ctrl + S）でブラウザのデフォルト動作を防ぐためには、`event.preventDefault()`を使用します。
- **ブラウザ間の互換性**: 一部の古いブラウザでは`event.key`のサポートが不十分なため、互換性に注意する必要があります。

## 一文要約
JavaScriptのキーボードイベントを利用することで、ユーザーのキーボード入力に対してインタラクティブに反応することが可能です。