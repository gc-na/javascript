<!--
Meta Description: # MIDIMessageEventに関する詳細ガイド - JavaScript ## 概要 MIDIMessageEventは、Web MIDI APIで使用されるイベントの一種で、MIDIメッセージを表現します。このイベントは、MIDIデバイスから送信されたメッセージを受信する際に発生します。 ...
Meta Keywords: function, midi, event, midimessageeventは, web
-->

# MIDIMessageEventに関する詳細ガイド - JavaScript

## 概要
MIDIMessageEventは、Web MIDI APIで使用されるイベントの一種で、MIDIメッセージを表現します。このイベントは、MIDIデバイスから送信されたメッセージを受信する際に発生します。

## ドキュメント
MIDIMessageEventは、Web MIDI APIの一部として定義されており、MIDIメッセージが受信されたときに発生します。このイベントの主な目的は、MIDIデバイスからのメッセージデータを取得することです。

### 使用方法
MIDIMessageEventは通常、MIDI入力デバイスからメッセージを受信する際に、イベントリスナーを介して使用されます。以下は、MIDIMessageEventの基本的な構造です。

```javascript
// MIDIアクセスを取得
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    
    // MIDI入力デバイスの各入力に対してイベントリスナーを追加
    inputs.forEach(function(input) {
        input.onmidimessage = function(event) {
            // MIDIMessageEventの処理
            console.log(event.data); // MIDIメッセージデータを表示
        };
    });
});
```

### 詳細
MIDIMessageEventには以下のプロパティがあります。

- `data`: MIDIメッセージのデータを含むUint8Array。メッセージの種類（ノートオン、ノートオフなど）やそのパラメーターが格納されています。
- `timeStamp`: イベントが発生した時刻をミリ秒単位で示す数値。

MIDIMessageEventは、MIDIデータの受信時にリアルタイムで反応するため、音楽制作やパフォーマンスにおいて非常に重要です。

## 例
以下のコードは、MIDIメッセージを受信し、コンソールに出力する基本的な例です。

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    midiAccess.inputs.forEach(function(input) {
        input.onmidimessage = function(event) {
            console.log(`Received MIDI message: ${event.data}`);
        };
    });
});
```

この例では、MIDIデバイスからのメッセージを受信し、その内容をコンソールに表示します。

## 説明
MIDIMessageEventを使用する際の一般的な注意点は以下の通りです。

1. **ブラウザのサポート**: Web MIDI APIはすべてのブラウザでサポートされているわけではありません。使用する前に、ブラウザの対応状況を確認してください。
2. **MIDIデバイスの接続**: MIDIデバイスが正しく接続されていることを確認し、適切な権限を許可する必要があります。
3. **データ形式**: event.dataはUint8Arrayであり、データを扱う際にはその形式を理解しておくことが重要です。

## 一文要約
MIDIMessageEventは、Web MIDI APIを通じてMIDIデバイスから受信したメッセージを処理するための重要なイベントです。