<!--
Meta Description: # MIDIOutput: JavaScriptにおけるMIDI出力の完全ガイド ## 概要 MIDIOutputは、Web MIDI APIの一部であり、JavaScriptを使用してMIDIデバイスにデータを送信するためのインターフェースです。この機能は、音楽制作やインタラクティブな音楽アプリケ...
Meta Keywords: output, javascript, midiaccess, outputs, midi
-->

# MIDIOutput: JavaScriptにおけるMIDI出力の完全ガイド

## 概要
MIDIOutputは、Web MIDI APIの一部であり、JavaScriptを使用してMIDIデバイスにデータを送信するためのインターフェースです。この機能は、音楽制作やインタラクティブな音楽アプリケーションでのリアルタイムMIDI通信を可能にします。

## ドキュメンテーション
### 目的
MIDIOutputは、MIDIメッセージを外部MIDIデバイスに送信するために使用されます。これにより、ユーザーはブラウザベースのアプリケーションから音楽を生成したり、MIDI機器を制御したりできます。

### 使用方法
1. **MIDIデバイスのリクエスト**:
   Web MIDI APIを使用するには、まずMIDIデバイスへのアクセスを要求する必要があります。

   ```javascript
   navigator.requestMIDIAccess().then(onMIDISuccess, onMIDIFailure);
   ```

2. **MIDIOutputの取得**:
   MIDIデバイスへのアクセスが許可された後、出力デバイスを取得します。

   ```javascript
   function onMIDISuccess(midiAccess) {
       const outputs = midiAccess.outputs;
       outputs.forEach(output => {
           // MIDIOutputの処理
       });
   }
   ```

3. **MIDIメッセージの送信**:
   取得したMIDIOutputを使用して、MIDIメッセージを送信します。

   ```javascript
   const output = midiAccess.outputs.get(outputId);
   output.send([0x90, 60, 0x7f]); // ノートオンメッセージ
   ```

### 詳細
- **MIDIメッセージ形式**:
  MIDIメッセージは、通常3つのバイトで構成されます。最初のバイトはメッセージのタイプ（例：ノートオン、ノートオフ）、次の2つはノート番号とベロシティを指定します。

- **sendメソッド**:
  - `send(data: Uint8Array | Array<number>, timestamp?: number)`メソッドを使用してMIDIメッセージを送信します。timestampはオプションで、メッセージが送信されるべき時刻を指定します。

## 例
### 1. MIDIデバイスにノートオンメッセージを送信する
```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const output = midiAccess.outputs.values().next().value;
    output.send([0x90, 60, 0x7f]); // C4を鳴らす
});
```

### 2. ノートオフメッセージを送信する
```javascript
output.send([0x80, 60, 0x40]); // C4を停止
```

## 説明
- **一般的な落とし穴**:
  - MIDIデバイスのアクセスを取得する際に、ユーザーの許可が必要です。許可が得られない場合、出力デバイスを取得できません。
  - Web MIDI APIは、すべてのブラウザでサポートされているわけではありません。最新のブラウザを使用することを確認してください。

- **注意点**:
  - MIDIメッセージの送信は非同期であるため、メッセージの送信後にすぐに確認することはできません。
  - 送信するMIDIメッセージが正しい形式であることを確認してください。

## 一文要約
MIDIOutputは、JavaScriptを使用して外部MIDIデバイスにMIDIメッセージを送信するためのWeb MIDI APIのインターフェースです。