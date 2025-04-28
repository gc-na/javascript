<!--
Meta Description: # MediaQueryListEvent: JavaScriptにおけるメディアクエリのイベント ## 概要 `MediaQueryListEvent`は、JavaScriptでメディアクエリの状態が変化したときに発生するイベントを表します。これにより、デバイスのビューポートやメディア条件に基づい...
Meta Keywords: mediaquerylistevent, mediaquerylist, matchmedia, addeventlistener, handlemediachange
-->

# MediaQueryListEvent: JavaScriptにおけるメディアクエリのイベント

## 概要
`MediaQueryListEvent`は、JavaScriptでメディアクエリの状態が変化したときに発生するイベントを表します。これにより、デバイスのビューポートやメディア条件に基づいて動的にスタイルやレイアウトを変更することが可能になります。

## ドキュメント
### 目的
`MediaQueryListEvent`は、`MediaQueryList`オブジェクトのリスナーが呼び出されるときに発生します。このイベントは、メディアクエリが適用される状態が変わったときに通知を受け取るために使用されます。

### 使用法
1. **メディアクエリの作成**: `window.matchMedia()`メソッドを使用して、特定のメディアクエリを監視する`MediaQueryList`オブジェクトを作成します。
2. **イベントリスナーの追加**: `addEventListener`メソッドを使用して、`MediaQueryListEvent`をリッスンします。
3. **イベントの処理**: 発生したイベントに対処するためのコールバック関数を定義します。

### 詳細
- **プロパティ**: `MediaQueryListEvent`には、`matches`（メディアクエリが適用されているかどうかを示す真偽値）や`media`（クエリの文字列）というプロパティがあります。
- **イベントの発生**: メディアクエリがマッチする状態から不一致の状態、またはその逆に変わったときにこのイベントが発生します。

## 例
以下は、メディアクエリを監視し、状態が変わったときにコンソールにメッセージを表示する基本的な例です。

```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');

function handleMediaChange(event) {
    if (event.matches) {
        console.log('600px以下の幅にマッチしました。');
    } else {
        console.log('600pxを超える幅です。');
    }
}

// イベントリスナーを追加
mediaQueryList.addEventListener('change', handleMediaChange);

// 初回チェック
handleMediaChange(mediaQueryList);
```

## 説明
- **共通の落とし穴**: `MediaQueryListEvent`を使用する前に、`matchMedia`を正しく使用していることを確認してください。誤ったメディアクエリを指定すると、期待する動作が得られません。
- **ブラウザの互換性**: 一部の古いブラウザでは`addEventListener`がサポートされていないため、`MediaQueryList`の`onchange`プロパティを使用してイベントをリッスンすることが必要です。

## 一文要約
`MediaQueryListEvent`は、メディアクエリの状態変化をキャッチするためのJavaScriptイベントであり、レスポンシブデザインの実装を容易にします。