<!--
Meta Description: # XRInputSourceArray: JavaScriptによるXRデバイス入力管理 ## 概要 `XRInputSourceArray`は、WebXR APIの一部であり、XRデバイス（仮想現実や拡張現実デバイス）からの入力情報を管理するための配列です。このオブジェクトは、ユーザーのインタラ...
Meta Keywords: xrinputsourcearray, inputsources, session, webxr, xrinputsource
-->

# XRInputSourceArray: JavaScriptによるXRデバイス入力管理

## 概要
`XRInputSourceArray`は、WebXR APIの一部であり、XRデバイス（仮想現実や拡張現実デバイス）からの入力情報を管理するための配列です。このオブジェクトは、ユーザーのインタラクションをリアルタイムで扱うために必要なデータを提供します。

## ドキュメンテーション
`XRInputSourceArray`は、XRセッション中に接続されているすべての入力ソースを格納するための配列です。これには、コントローラ、ハンドトラッキング、その他の入力デバイスが含まれます。各入力ソースは`XRInputSource`オブジェクトとして表現され、デバイスの種類や状態、位置情報などの詳細を持ちます。

### 使用目的
- XRデバイスからの入力を管理する
- ユーザーインターフェースの操作を可能にする
- ゲームやアプリケーションのインタラクティブ性を向上させる

### 詳細
`XRInputSourceArray`は以下のプロパティやメソッドを持ちます：
- **length**: 現在の入力ソースの数を返す整数値。
- **[index]**: 特定のインデックスにある`XRInputSource`オブジェクトにアクセスするためのインデックス演算子。

### 例
以下は、`XRInputSourceArray`の基本的な使用例です。

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSources = session.inputSources;
        inputSources.forEach((inputSource) => {
            if (inputSource.hand) {
                console.log('ハンドトラッキングデバイスが入力されています。');
            } else {
                console.log('コントローラーデバイスが入力されています。');
            }
        });
    });
});
```

## 説明
### 一般的な落とし穴
- **デバイスの互換性**: すべてのブラウザやデバイスがWebXRをサポートしているわけではないため、事前に対応状況を確認することが重要です。
- **非同期処理**: XRセッションの初期化は非同期で行われるため、セッションが開始される前に`inputSources`にアクセスしようとすると、エラーが発生する可能性があります。

### 注意点
- `XRInputSourceArray`は読み取り専用であり、直接変更することはできません。
- 変更があった場合（デバイスの接続や切断）、`inputSources`の内容は自動的に更新されます。

## 一文要約
`XRInputSourceArray`は、WebXR APIにおいてXRデバイスからの入力を効率的に管理するための配列です。