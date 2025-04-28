<!--
Meta Description: # onpause: JavaScriptのメディア制御イベント ## 概要 `onpause`は、HTML5のメディア要素（`<video>`や`<audio>`）に関連するイベントで、メディアが一時停止した際に発火します。このイベントを利用することで、ユーザーのインタラクションに基づいた動的なア...
Meta Keywords: onpause, video, イベントは, videoelement, myvideo
-->

# onpause: JavaScriptのメディア制御イベント

## 概要
`onpause`は、HTML5のメディア要素（`<video>`や`<audio>`）に関連するイベントで、メディアが一時停止した際に発火します。このイベントを利用することで、ユーザーのインタラクションに基づいた動的なアプリケーションを構築することが可能です。

## ドキュメント
### 目的
`onpause`イベントは、メディアが一時停止した瞬間に特定のコードを実行するために使用されます。これにより、ユーザーがメディアの再生を中断した際に、アプリケーションの状態を変更したり、関連情報を表示したりすることができます。

### 使用法
`onpause`イベントは、HTMLのメディア要素に対して設定されます。例えば、`<video>`タグや`<audio>`タグに対して直接イベントリスナーを追加することができます。

```javascript
const videoElement = document.getElementById('myVideo');

videoElement.onpause = function() {
    console.log('動画が一時停止しました。');
};
```

### 詳細
- **イベントオブジェクト**: `onpause`イベントは、イベントオブジェクトを持たないシンプルなイベントです。したがって、リスナー関数の引数として特別な情報を受け取ることはありません。
- **対応ブラウザ**: `onpause`はほとんどのモダンブラウザでサポートされていますが、古いブラウザでは互換性に注意が必要です。

## 例
### 基本的な使用例

以下の例では、`<video>`要素が一時停止されたときに、アラートボックスを表示します。

```html
<video id="myVideo" width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    ブラウザが動画タグをサポートしていません。
</video>

<script>
    const videoElement = document.getElementById('myVideo');

    videoElement.onpause = function() {
        alert('動画が一時停止しました。');
    };
</script>
```

## 説明
### 一般的な落とし穴
- **イベントの登録漏れ**: `onpause`イベントを設定する際、正しいメディア要素に対して設定されているか確認してください。間違った要素に設定すると、期待通りに動作しません。
- **他のイベントとの競合**: `onpause`は、`onplay`や`onended`などの他のメディアイベントと連携して使用することが多いですが、意図しない挙動を引き起こす可能性があるため、他のイベントとの関係を考慮する必要があります。

## 一文での要約
`onpause`イベントは、HTML5メディア要素が一時停止された際に発火し、動的なアプリケーションでのインタラクションを強化するために利用されます。