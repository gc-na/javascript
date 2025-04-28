<!--
Meta Description: # MIDIPort: JavaScriptにおけるMIDIポートの操作 ## 概要 `MIDIPort`は、Web MIDI APIの一部であり、MIDIデバイスとの接続を管理するためのインターフェースです。このインターフェースを使用することで、JavaScriptでMIDIメッセージを送受信する...
Meta Keywords: midiport, midiaccess, console, inputs, outputs
-->

# MIDIPort: JavaScriptにおけるMIDIポートの操作

## 概要
`MIDIPort`は、Web MIDI APIの一部であり、MIDIデバイスとの接続を管理するためのインターフェースです。このインターフェースを使用することで、JavaScriptでMIDIメッセージを送受信することが可能になります。

## ドキュメント
`MIDIPort`は、MIDIデバイス（入力および出力）の情報を表すオブジェクトです。主に次の2つのプロパティを持っています。

- **id**: MIDIポートの一意の識別子。
- **name**: MIDIポートの名称。
- **state**: MIDIポートの状態（`"connected"`または`"disconnected"`）。

### 使用方法
`MIDIPort`オブジェクトは、MIDIデバイスを取得するために`navigator.requestMIDIAccess()`メソッドを使用して得られる`MIDIAccess`オブジェクトからアクセスできます。以下は、基本的な使用手順です。

1. `navigator.requestMIDIAccess()`を呼び出してMIDIアクセスを取得します。
2. MIDIポート情報を取得し、`MIDIPort`オブジェクトを操作します。

```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const inputs = midiAccess.inputs;
    const outputs = midiAccess.outputs;

    inputs.forEach((input) => {
        console.log(input.name); // MIDI入力ポート名を表示
    });

    outputs.forEach((output) => {
        console.log(output.name); // MIDI出力ポート名を表示
    });
});
```

## 例
以下は、`MIDIPort`を使用してMIDIデバイスの情報を取得する基本的な例です。

```javascript
navigator.requestMIDIAccess().then(midiAccess => {
    const inputs = midiAccess.inputs;
    const outputs = midiAccess.outputs;

    console.log("MIDI入力ポート:");
    inputs.forEach(input => {
        console.log(`ID: ${input.id}, 名前: ${input.name}, 状態: ${input.state}`);
    });

    console.log("MIDI出力ポート:");
    outputs.forEach(output => {
        console.log(`ID: ${output.id}, 名前: ${output.name}, 状態: ${output.state}`);
    });
}).catch(err => {
    console.error("MIDIアクセスの取得に失敗しました:", err);
});
```

## 説明
`MIDIPort`を使用する際の一般的な注意点は以下の通りです。

- **ブラウザのサポート**: Web MIDI APIはすべてのブラウザでサポートされているわけではありません。使用する前に対応ブラウザを確認してください。
- **ユーザーの許可**: MIDIデバイスへのアクセスを要求する際には、ユーザーの許可が必要です。このため、ユーザーインターフェースを適切に設計することが重要です。
- **状態管理**: MIDIポートの状態（接続されているかどうか）を適切に管理し、変更があった場合に適切な対応を行うようにしましょう。

## 一文の要約
`MIDIPort`は、JavaScriptを使用してMIDIデバイスとの接続を管理するための重要なインターフェースです。