<!--
Meta Description: # JavaScriptのonprogressイベント：進行状況を追跡する方法 ## 概要 JavaScriptの`onprogress`イベントは、データの読み込みや処理の進行状況を追跡するために使用されます。このイベントは、特にXMLHttpRequestやFetch APIを使用する際に、ユー...
Meta Keywords: xhr, const, onprogress, event, percentcomplete
-->

# JavaScriptのonprogressイベント：進行状況を追跡する方法

## 概要
JavaScriptの`onprogress`イベントは、データの読み込みや処理の進行状況を追跡するために使用されます。このイベントは、特にXMLHttpRequestやFetch APIを使用する際に、ユーザーインターフェースに進行状況を表示する場合に役立ちます。

## ドキュメンテーション
### 目的
`onprogress`イベントは、データの読み込みが進行中であることを示し、ユーザーに進行状況を通知するために使用されます。これにより、ユーザーエクスペリエンスが向上し、処理が完了するまでの待機時間を明示的に示すことができます。

### 使用法
`onprogress`イベントは、XMLHttpRequestオブジェクトまたはFetch APIのレスポンスに関連付けて使用されます。以下は、XMLHttpRequestを使用した基本的な使用法の例です。

```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://example.com/data', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`読み込み進行状況: ${percentComplete}%`);
    } else {
        console.log('進行状況を計測できません。');
    }
};

xhr.onload = function() {
    console.log('データの読み込みが完了しました。');
};

xhr.send();
```

## 例
### 基本的な使用例
- **XMLHttpRequestを使用した例**
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://example.com/file', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`進捗: ${percentComplete}%`);
    }
};

xhr.onload = function() {
    console.log('読み込み完了');
};

xhr.send();
```

- **Fetch APIを使用した例**
```javascript
async function fetchData() {
    const response = await fetch('https://example.com/data');
    const reader = response.body.getReader();
    const contentLength = +response.headers.get('Content-Length');

    let receivedLength = 0; // 受信したバイト数
    let chunks = []; // 受信したデータのチャンク

    while(true) {
        const { done, value } = await reader.read();
        if (done) break;

        chunks.push(value);
        receivedLength += value.length;

        const percentComplete = (receivedLength / contentLength) * 100;
        console.log(`進捗: ${percentComplete}%`);
    }
}
fetchData();
```

## 説明
### 注意点
- `lengthComputable`プロパティが`true`の場合、全体のデータ量が分かるため、進行状況をパーセンテージで表示できます。しかし、全体のデータ量が不明な場合は、進行状況を正確に計測できません。
- `onprogress`イベントは、データの読み込み中に複数回発火することがあります。そのため、UIの更新が必要な場合は、パフォーマンスを考慮する必要があります。

### よくある落とし穴
- `onprogress`イベントの実装が不十分な場合、ユーザーが進行状況を認識できないことがあります。
- イベントが発火しない場合、ネットワークの状態やサーバーの設定を確認する必要があります。

## 一文要約
JavaScriptの`onprogress`イベントは、データの読み込みや処理の進行状況を追跡し、ユーザーに進行状況を表示するために使用されます。