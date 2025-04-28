<!--
Meta Description: # MIDIInputMap（JavaScriptにおけるMIDI入力マッピング） ## 概要 MIDIInputMapは、Web MIDI APIの一部として、MIDIデバイスからの入力を管理するためのインターフェースです。これにより、開発者はMIDIデバイスからの信号を簡単に扱い、音楽アプリケー...
Meta Keywords: inputs, midiinputmapは, midiaccess, input, web
-->

# MIDIInputMap（JavaScriptにおけるMIDI入力マッピング）

## 概要
MIDIInputMapは、Web MIDI APIの一部として、MIDIデバイスからの入力を管理するためのインターフェースです。これにより、開発者はMIDIデバイスからの信号を簡単に扱い、音楽アプリケーションやインタラクティブな体験を作成することができます。

## ドキュメンテーション
### 目的
MIDIInputMapは、接続されたMIDIデバイスからの入力をマッピングし、各MIDIメッセージの取り扱いを容易にします。このインターフェースを使用することで、特定のMIDIメッセージに対してイベントリスナーを設定し、リアルタイムで反応することが可能になります。

### 使用法
MIDIInputMapは、通常、MIDIInputオブジェクトから取得されます。以下のように使用します。

```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
  const inputs = midiAccess.inputs;
  for (let input of inputs.values()) {
    input.onmidimessage = (message) => {
      // メッセージ処理
      console.log(message.data);
    };
  }
});
```

### 詳細
- `MIDIInputMap`は、接続されたMIDIデバイスが送信するMIDIメッセージを管理します。
- 各MIDIデバイスは、複数の入力を持つことができ、これにより、複数のMIDI信号を同時に処理できます。
- MIDIメッセージには、ノートオン、ノートオフ、コントロールチェンジなどがあります。
- このAPIは、音楽制作、ゲーム開発、インタラクティブなアートなど、多様な用途に利用されます。

## 例
以下は、MIDIInputMapを用いた基本的な使用例です。

```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
  const inputs = midiAccess.inputs;
  
  inputs.forEach((input) => {
    input.onmidimessage = (event) => {
      const [status, note, velocity] = event.data;
      if (status === 144) { // ノートオン
        console.log(`ノート ${note} がオン、ベロシティ: ${velocity}`);
      } else if (status === 128) { // ノートオフ
        console.log(`ノート ${note} がオフ`);
      }
    };
  });
});
```

## 説明
- MIDIInputMapを使用する際の一般的な落とし穴は、MIDIデバイスが接続されているかどうかを確認せずにメッセージを処理しようとすることです。接続がない場合、メッセージは受信されません。
- また、MIDIメッセージの構造を理解していないと、データを正しく解釈できない可能性があります。
- Web MIDI APIは、ブラウザのサポート状況によって異なるため、使用する前にブラウザの互換性を確認してください。

## 一文の要約
MIDIInputMapは、Web MIDI APIにおいてMIDIデバイスからの入力を管理し、リアルタイムでの音楽処理を可能にするインターフェースです。