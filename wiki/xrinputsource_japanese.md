<!--
Meta Description: # XRInputSource: JavaScriptのXRデバイス入力管理 ## 概要 XRInputSourceは、WebXR APIにおける重要なインターフェースで、仮想現実（VR）および拡張現実（AR）デバイスからの入力を処理するためのオブジェクトです。このインターフェースを使用することで、...
Meta Keywords: inputsource, xrinputsourceは, session, gamepad, pressed
-->

# XRInputSource: JavaScriptのXRデバイス入力管理

## 概要
XRInputSourceは、WebXR APIにおける重要なインターフェースで、仮想現実（VR）および拡張現実（AR）デバイスからの入力を処理するためのオブジェクトです。このインターフェースを使用することで、開発者はユーザーのデバイスからの入力（トリガー、スティック、ボタンなど）を簡単に取得し、インタラクティブな体験を構築できます。

## ドキュメンテーション
### 目的
XRInputSourceは、VRおよびARのアプリケーションで、さまざまな入力デバイス（コントローラー、ハンドトラッキングデバイスなど）からのデータを管理するためのインターフェースです。

### 使用法
XRInputSourceは、通常、XRセッションの開始時に取得されるXRSession.inputSources配列の要素として提供されます。このオブジェクトを使用して、入力デバイスが持つさまざまなプロパティやメソッドにアクセスできます。

### 詳細
- **プロパティ**:
  - `handedness`: 入力デバイスが右手か左手かを示す文字列。
  - `targetRaySpace`: 入力デバイスの光線がどの空間で発生しているかを示すXRSpaceオブジェクト。
  - `profiles`: 入力デバイスに関連付けられたプロファイルの配列。
  - `gamepad`: デバイスがゲームパッドの場合、その状態を表すGamepadオブジェクト。

- **メソッド**:
  - 特にメソッドは定義されていませんが、プロパティを使用してデバイスの状態を確認し、ユーザーの入力に基づいたアクションを実行できます。

## 例
以下は、XRInputSourceを使用してVRデバイスのトリガー入力を取得する基本的な例です。

```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSource = event.inputSource;
        console.log(`${inputSource.handedness} hand trigger pressed.`);
    });

    session.requestAnimationFrame((time) => {
        session.inputSources.forEach((inputSource) => {
            if (inputSource.gamepad) {
                const buttonPressed = inputSource.gamepad.buttons[0].pressed;
                console.log(`Button 0 pressed: ${buttonPressed}`);
            }
        });
    });
});
```

## 説明
XRInputSourceを使用する際の一般的な落とし穴は、デバイスが正しく接続されていない場合や、セッションが適切に開始されていない場合に、期待した入力が得られないことです。また、異なるデバイス間でのプロパティの互換性に注意が必要です。各デバイスの仕様を確認し、適切にハンドリングすることが重要です。

## 一文要約
XRInputSourceは、WebXR APIを通じて仮想現実および拡張現実デバイスからの入力を管理するためのインターフェースです。