<!--
Meta Description: # MIDIAccess: JavaScriptでのメディアデバイスへのアクセス ## 概要 MIDIAccessは、Web MIDI APIの一部で、JavaScriptを使用してMIDIデバイスにアクセスし、操作するための機能を提供します。これにより、ブラウザベースのアプリケーションでリアルタイ...
Meta Keywords: midiaccess, navigator, requestmidiaccess, inputs, outputs
-->

# MIDIAccess: JavaScriptでのメディアデバイスへのアクセス

## 概要
MIDIAccessは、Web MIDI APIの一部で、JavaScriptを使用してMIDIデバイスにアクセスし、操作するための機能を提供します。これにより、ブラウザベースのアプリケーションでリアルタイムでMIDIメッセージを送受信し、音楽制作やインタラクティブなミュージックアプリケーションを開発することが可能になります。

## ドキュメント
MIDIAccessインターフェースは、MIDIデバイスへのアクセスを管理し、接続されたデバイスの情報を提供します。主な目的は、MIDI入力および出力ポートに対する操作を簡単に行うことです。

### 使用方法
MIDIAccessを利用するには、まず`navigator.requestMIDIAccess()`メソッドを呼び出して、MIDIデバイスへのアクセスを要求します。このメソッドは、Promiseを返し、成功時にはMIDIAccessオブジェクトを取得できます。

```javascript
navigator.requestMIDIAccess()
  .then(onMIDISuccess, onMIDIFailure);

function onMIDISuccess(midiAccess) {
  // MIDIデバイスにアクセス成功
  console.log("MIDIデバイスが利用可能です");
}

function onMIDIFailure() {
  // MIDIデバイスにアクセス失敗
  console.error("MIDIデバイスにアクセスできません");
}
```

### 詳細
- **MIDIAccessオブジェクト**: MIDIデバイスへの情報を持つオブジェクト。
- **inputs**: 接続されたMIDI入力ポートのリスト。
- **outputs**: 接続されたMIDI出力ポートのリスト。
- **onstatechange**: MIDIデバイスの接続状態が変化した際に呼び出されるイベントハンドラ。

## 例
### MIDIデバイスのリストを表示する
次のコードは、接続されたすべてのMIDIデバイスをリスト表示します。

```javascript
navigator.requestMIDIAccess()
  .then(midiAccess => {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
      console.log(`MIDI入力ポート: ${input.name}`);
    });
  });
```

### MIDIメッセージの送信
以下のコードは、MIDI出力ポートを使用してMIDIメッセージを送信します。

```javascript
navigator.requestMIDIAccess()
  .then(midiAccess => {
    const outputs = midiAccess.outputs;
    const output = outputs.values().next().value; // 最初の出力ポートを取得
    output.send([0x90, 60, 0x7f]); // Note On メッセージ
  });
```

## 説明
MIDIAccessを使用する際の一般的な注意点：
- MIDIデバイスへのアクセスは、ユーザーの許可が必要です。ブラウザがユーザーにアクセスを要求します。
- 一部のブラウザでは、HTTPS接続が必要です。
- プラットフォームによっては、MIDIデバイスが正しく認識されない場合があります。

## 一文要約
MIDIAccessは、JavaScriptを使用してWebブラウザ内でMIDIデバイスにアクセスし、リアルタイムで音楽データを操作するためのAPIです。