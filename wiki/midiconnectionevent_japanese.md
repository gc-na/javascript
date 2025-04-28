<!--
Meta Description: # MIDIConnectionEvent: JavaScriptでのMIDI接続イベントの詳細 ## 概要 MIDIConnectionEventは、Web MIDI APIにおけるMIDIデバイスの接続や切断を示すイベントを表します。このイベントは、JavaScriptを使用してMIDIデバイス...
Meta Keywords: event, midiaccess, port, function, midiconnectioneventは
-->

# MIDIConnectionEvent: JavaScriptでのMIDI接続イベントの詳細

## 概要
MIDIConnectionEventは、Web MIDI APIにおけるMIDIデバイスの接続や切断を示すイベントを表します。このイベントは、JavaScriptを使用してMIDIデバイスを操作する際に重要な役割を果たします。

## ドキュメンテーション
### 目的
MIDIConnectionEventは、MIDIデバイスの状態変更に関する情報を提供します。これにより、開発者は接続されたデバイスのリストを更新したり、ユーザーインターフェイスを適切に反映させたりすることができます。

### 使用法
MIDIConnectionEventは、Web MIDI APIの一部であり、MIDIデバイスが接続または切断された際に発生します。このイベントは、`navigator.requestMIDIAccess()`メソッドを使用してMIDIアクセスを取得した後にリッスンすることができます。

### プロパティ
- `port`: 接続または切断されたMIDIポートの情報を含むオブジェクト。

### イベントのリッスン
MIDI接続イベントをリッスンするためには、以下のように`onstatechange`イベントハンドラを設定します。

```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    midiAccess.onstatechange = function(event) {
        console.log(event);
    };
});
```

## 例
以下は、MIDIConnectionEventの基本的な使用例です。

### 例1: MIDIデバイスの接続と切断を監視する
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    midiAccess.onstatechange = function(event) {
        if (event.port.state === 'connected') {
            console.log('MIDIデバイスが接続されました:', event.port.name);
        } else if (event.port.state === 'disconnected') {
            console.log('MIDIデバイスが切断されました:', event.port.name);
        }
    };
});
```

### 例2: 接続されているMIDIデバイスの情報を取得
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    for (let input of midiAccess.inputs.values()) {
        console.log('接続されているMIDI入力デバイス:', input.name);
    }
});
```

## 説明
MIDIConnectionEventを利用する際に注意すべき点は、MIDIデバイスの接続状況が変化した場合に即座に反応する必要があるということです。特に、複数のMIDIデバイスを使用する場合、イベントリスナーを適切に設定しないと、デバイスの状態を正確に把握できないことがあります。また、ブラウザの互換性にも注意が必要で、すべてのブラウザがWeb MIDI APIをサポートしているわけではありません。

## ワンラインサマリー
MIDIConnectionEventは、JavaScriptでMIDIデバイスの接続と切断を管理するために使用されるイベントです。