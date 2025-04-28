<!--
Meta Description: # JavaScriptのonkeydownイベント: キーボード入力をキャッチする方法 ## 概要 `onkeydown`は、ユーザーがキーボードのキーを押したときに発生するイベントです。このイベントを利用することで、リアルタイムでキーボードの入力を監視し、インタラクティブなユーザー体験を提供でき...
Meta Keywords: event, onkeydown, key, document, function
-->

# JavaScriptのonkeydownイベント: キーボード入力をキャッチする方法

## 概要
`onkeydown`は、ユーザーがキーボードのキーを押したときに発生するイベントです。このイベントを利用することで、リアルタイムでキーボードの入力を監視し、インタラクティブなユーザー体験を提供できます。

## ドキュメンテーション
`onkeydown`イベントは、HTML要素（主にフォーム要素やドキュメント全体）に関連付けられます。このイベントは、キーが押されると即座にトリガーされ、押されたキーの情報を取得することができます。主に次のような用途で使用されます：

- 入力フォームのバリデーション
- ショートカットキーの実装
- ゲームやアプリケーションでのカスタム操作

### 使用方法
`onkeydown`イベントは次のように設定できます。

```javascript
document.addEventListener('keydown', function(event) {
    console.log(`押されたキー: ${event.key}`);
});
```

### イベントオブジェクト
`onkeydown`イベントが発生すると、イベントオブジェクトが渡され、以下の重要なプロパティが含まれます：

- `event.key`: 押されたキーの値（例: 'a', 'Enter'）
- `event.code`: キーの物理的な位置に関する値（例: 'KeyA', 'Enter'）
- `event.altKey`: Altキーが押されているかどうか
- `event.ctrlKey`: Ctrlキーが押されているかどうか
- `event.shiftKey`: Shiftキーが押されているかどうか

## 例
以下は、`onkeydown`イベントを使用した基本的な例です。

### 例1: キー入力の表示
```html
<input type="text" id="myInput">
<script>
    const input = document.getElementById('myInput');
    input.onkeydown = function(event) {
        alert(`押されたキー: ${event.key}`);
    };
</script>
```

### 例2: ショートカットキーの実装
```javascript
document.addEventListener('keydown', function(event) {
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault(); // デフォルトの保存動作を防ぐ
        alert('Ctrl + Sが押されました！');
    }
});
```

## 説明
`onkeydown`イベントを使用する際の一般的な落とし穴や注意点は以下の通りです：

- **デフォルト動作の防止**: 一部のキーはブラウザに特定の動作を持っているため、`event.preventDefault()`を使用してその動作を防ぐ必要があります。
- **キーリピート**: キーを押し続けると、`onkeydown`イベントが繰り返しトリガーされるため、処理を制御する必要があります。
- **ブラウザの互換性**: 一部の古いブラウザでは、`event.key`が正しく機能しないことがあります。代わりに`event.which`を使用することが推奨される場合があります。

## 一文の要約
`onkeydown`イベントは、ユーザーがキーボードのキーを押したときに発生し、リアルタイムで入力を処理するために利用されます。