<!--
Meta Description: # JavaScriptにおけるSharedWorkerの詳細ガイド ## 概要 SharedWorkerは、複数のスクリプトやウィンドウ間で共有できるWeb Workerの一種です。これにより、同一オリジン内の異なるタブやウィンドウが同じワーカーを利用して、データを効率的に共有することが可能になり...
Meta Keywords: worker, port, event, sharedworkerは, sharedworker
-->

# JavaScriptにおけるSharedWorkerの詳細ガイド

## 概要
SharedWorkerは、複数のスクリプトやウィンドウ間で共有できるWeb Workerの一種です。これにより、同一オリジン内の異なるタブやウィンドウが同じワーカーを利用して、データを効率的に共有することが可能になります。

## ドキュメント

### 目的
SharedWorkerは、複数のブラウザタブやウィンドウで同じスクリプトを実行するための手段を提供します。これにより、リソースの無駄遣いを防ぎ、データの一貫性を保ちながら、パフォーマンスを向上させることができます。

### 使用法
SharedWorkerを使用するには、まず`SharedWorker`オブジェクトを生成し、ワーカーのスクリプトファイルを指定します。次に、`port`を介してメッセージの送受信を行います。

#### 基本構文
```javascript
const worker = new SharedWorker('worker.js');
```

### 詳細
1. **ワーカーの作成**: `SharedWorker`コンストラクタにスクリプトのURLを指定します。
2. **ポートの取得**: `worker.port`を使用して、ワーカーとの通信ポートを取得します。
3. **メッセージの送受信**: `postMessage`メソッドを用いてメッセージを送信し、`onmessage`イベントを使用してメッセージを受け取ります。

## 例

### 基本的な使用例
以下は、SharedWorkerを使用した簡単な例です。

**worker.js**
```javascript
onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(event) {
        port.postMessage(`Hello, ${event.data}`);
    };
};
```

**main.js**
```javascript
const worker = new SharedWorker('worker.js');

worker.port.onmessage = function(event) {
    console.log(event.data); // "Hello, John"
};

worker.port.start(); // ポートの開始
worker.port.postMessage('John'); // メッセージの送信
```

## 説明
SharedWorkerにはいくつかの注意点があります。

- **同一オリジン**: SharedWorkerは同一オリジン内でのみ共有可能です。異なるオリジンのタブ間では使用できません。
- **複数タブのサポート**: SharedWorkerは、異なるタブやウィンドウの間でデータを共有できますが、すべてのタブがワーカーの状態を反映するわけではありません。
- **メモリ管理**: SharedWorkerは、最後のポートが閉じられたときに終了します。適切なタイミングでポートを閉じることが重要です。

## 一文要約
SharedWorkerは、複数のブラウザタブやウィンドウ間でデータを共有するための強力なWeb Workerの一種です。