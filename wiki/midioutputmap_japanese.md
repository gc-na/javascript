<!--
Meta Description: # MIDIOutputMap: JavaScriptにおけるMIDI出力デバイスの管理 ## 概要 MIDIOutputMapは、Web MIDI APIの一部として、JavaScriptを使用してMIDI出力デバイスを管理するためのインターフェースです。この機能を利用することで、Webアプリケー...
Meta Keywords: outputs, function, midiaccess, err, const
-->

# MIDIOutputMap: JavaScriptにおけるMIDI出力デバイスの管理

## 概要
MIDIOutputMapは、Web MIDI APIの一部として、JavaScriptを使用してMIDI出力デバイスを管理するためのインターフェースです。この機能を利用することで、WebアプリケーションはMIDIデバイスと通信し、音楽制作やリアルタイムの音楽演奏を可能にします。

## ドキュメンテーション
### 目的
MIDIOutputMapは、接続されているMIDI出力デバイスのリストを提供し、各デバイスの詳細情報を取得するために使用されます。このインターフェースは、特に音楽アプリケーションやゲームにおいて、ユーザーがMIDIデバイスを選択し、利用できるようにするために重要です。

### 使用法
MIDIOutputMapは、`navigator.requestMIDIAccess()`メソッドを使用して取得されるMIDI接続オブジェクトの一部として得られます。このオブジェクトを通じて、MIDI出力デバイスにアクセスし、デバイスの情報を取得できます。

#### 基本的な構文
```javascript
navigator.requestMIDIAccess()
  .then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    const outputMap = outputs.values();
    for (let output of outputMap) {
      console.log(output.name); // 出力デバイスの名前を表示
    }
  })
  .catch(function(err) {
    console.error("MIDIアクセスに失敗しました:", err);
  });
```

## 例
以下は、MIDIOutputMapを使った基本的な使用例です。

### 例1: 接続されているすべてのMIDI出力デバイスのリストを表示する
```javascript
navigator.requestMIDIAccess()
  .then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    outputs.forEach(output => {
      console.log(`デバイス名: ${output.name}, ID: ${output.id}`);
    });
  })
  .catch(function(err) {
    console.error("エラー:", err);
  });
```

### 例2: 特定のMIDI出力デバイスを選択してメッセージを送信する
```javascript
navigator.requestMIDIAccess()
  .then(function(midiAccess) {
    const outputs = midiAccess.outputs;
    const outputDevice = outputs.get("デバイスID"); // デバイスIDを指定
    if (outputDevice) {
      outputDevice.send([0x90, 60, 0x7f]); // ノートオンメッセージを送信
    }
  })
  .catch(function(err) {
    console.error("エラー:", err);
  });
```

## 説明
### 一般的な落とし穴
- **MIDIデバイスの接続状態**: MIDIデバイスが正しく接続されていないと、MIDIOutputMapは空になる可能性があります。デバイスを確認してください。
- **ブラウザのサポート**: Web MIDI APIはすべてのブラウザでサポートされているわけではありません。特に、SafariやInternet Explorerでは動作しないことがあります。
- **ユーザーの許可**: MIDIデバイスへのアクセスには、ユーザーの許可が必要です。アクセスを要求すると、ブラウザがポップアップを表示します。

## 一文要約
MIDIOutputMapは、JavaScriptを利用してMIDI出力デバイスを管理し、音楽アプリケーションにおいてMIDIメッセージの送信を可能にするインターフェースです。