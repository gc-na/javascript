<!--
Meta Description: # XRInputSourcesChangeEvent: JavaScriptにおけるXR入力ソースの変更イベント ## 概要 XRInputSourcesChangeEventは、WebXR APIにおいて、XR入力ソースが追加または削除される際に発生するイベントです。このイベントは、仮想現実（V...
Meta Keywords: xrinputsourceschangeeventは, inputsource, event, added, removed
-->

# XRInputSourcesChangeEvent: JavaScriptにおけるXR入力ソースの変更イベント

## 概要
XRInputSourcesChangeEventは、WebXR APIにおいて、XR入力ソースが追加または削除される際に発生するイベントです。このイベントは、仮想現実（VR）や拡張現実（AR）アプリケーションにおいて、ユーザーの入力デバイスの状態を検知するために使用されます。

## ドキュメント
### 目的
XRInputSourcesChangeEventは、XRセッションにおける入力ソースの変更を監視するためのイベントです。このイベントを利用することで、開発者は新しい入力デバイスを検出したり、既存のデバイスが取り外されたことを認識したりできます。

### 使用法
XRInputSourcesChangeEventは、XRセッションにおける`inputSources`の変更があった際に、自動的にトリガーされます。具体的には、以下の手順で使用します。

1. XRセッションを開始します。
2. `oninputsourceschange`イベントリスナーを設定します。
3. イベントが発生した際に、変更された入力ソースの情報を取得します。

### 詳細
- **プロパティ**:
  - `added`: 新たに追加された入力ソースの配列。
  - `removed`: 削除された入力ソースの配列。

## 例
以下は、XRInputSourcesChangeEventの基本的な使用例です。

```javascript
const xrSession = await navigator.xr.requestSession('immersive-vr');

xrSession.addEventListener('inputsourceschange', (event) => {
    event.added.forEach((inputSource) => {
        console.log('新しい入力ソースが追加されました:', inputSource);
    });

    event.removed.forEach((inputSource) => {
        console.log('入力ソースが削除されました:', inputSource);
    });
});
```

## 説明
XRInputSourcesChangeEventを使用する際の一般的な落とし穴や注意点があります。

- **イベントのリスニング**: `inputsourceschange`イベントを正しくリッスンしていない場合、入力デバイスの変更を見逃す可能性があります。
- **デバイスの互換性**: 一部のデバイスは、特定のブラウザやプラットフォームでのみサポートされているため、開発時には互換性に注意が必要です。
- **パフォーマンス**: 大量の入力デバイスがある環境では、イベントが頻繁に発生するため、パフォーマンスに影響を与える可能性があります。

## 一文の要約
XRInputSourcesChangeEventは、XRセッション内での入力デバイスの追加や削除を検知するための重要なイベントです。