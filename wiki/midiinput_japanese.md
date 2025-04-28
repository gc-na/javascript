<!--
Meta Description: # MIDIInput: JavaScriptにおけるMIDIデバイス入力の操作 ## 概要 MIDIInputは、Web MIDI APIの一部であり、JavaScriptを使用してMIDIデバイスからの入力を管理するためのインターフェースを提供します。この機能を利用することで、ブラウザ上でMID...
Meta Keywords: midiinputは, function, inputs, web, midi
-->

# MIDIInput: JavaScriptにおけるMIDIデバイス入力の操作

## 概要
MIDIInputは、Web MIDI APIの一部であり、JavaScriptを使用してMIDIデバイスからの入力を管理するためのインターフェースを提供します。この機能を利用することで、ブラウザ上でMIDIデバイスとリアルタイムで通信し、音楽や音声アプリケーションを作成することが可能になります。

## ドキュメンテーション
### 目的
MIDIInputは、MIDIデバイスから送信されるMIDIメッセージを受信するためのインターフェースです。これにより、ユーザーはMIDIキーボードやコントローラーと連携したインタラクティブなアプリケーションを構築できます。

### 使用法
MIDIInputは、`navigator.requestMIDIAccess()`メソッドを使用してMIDI接続を取得し、その後、接続されたMIDIデバイスの入力をリッスンします。以下は、基本的な使用手順です。

1. MIDIアクセスをリクエストする。
2. 利用可能なMIDIデバイスを取得する。
3. MIDIInputオブジェクトを使用して、MIDIメッセージを受信する。

### 詳細
- **プロパティ**: `state`（接続状態）、`type`（MIDIデバイスのタイプ）など。
- **メソッド**:
  - `addEventListener()`: MIDIメッセージを受信するためのイベントリスナーを追加します。
  - `removeEventListener()`: イベントリスナーを削除します。

## 例
以下は、MIDIInputを使用してMIDIメッセージを受信する基本的な例です。

```javascript
navigator.requestMIDIAccess().then(onSuccess, onFailure);

function onSuccess(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(input => {
        input.addEventListener('midimessage', onMIDIMessage);
    });
}

function onFailure() {
    console.error('MIDIデバイスにアクセスできませんでした。');
}

function onMIDIMessage(event) {
    const [status, data1, data2] = event.data;
    console.log(`MIDIメッセージ: ステータス=${status}, データ1=${data1}, データ2=${data2}`);
}
```

## 説明
- **共通の落とし穴**: MIDIデバイスが正しく接続されていない場合、MIDIメッセージを受信できません。デバイスの接続状態を確認することが重要です。
- **ブラウザの互換性**: Web MIDI APIは、すべてのブラウザでサポートされているわけではありません。ChromeやOperaが主にサポートしているため、他のブラウザでの動作を確認することが必要です。

## 一文要約
MIDIInputは、JavaScriptを通じてMIDIデバイスからの入力をリアルタイムで管理するための機能です。