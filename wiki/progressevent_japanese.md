<!--
Meta Description: # ProgressEvent: JavaScriptにおける進行状況イベント ## 概要 `ProgressEvent`は、JavaScriptで非同期処理の進行状況を示すイベントです。主に、データのダウンロードやアップロードなど、リソースの進行状況を追跡するために使用されます。 ## ドキュメン...
Meta Keywords: xhr, event, progressevent, const, percentcomplete
-->

# ProgressEvent: JavaScriptにおける進行状況イベント

## 概要
`ProgressEvent`は、JavaScriptで非同期処理の進行状況を示すイベントです。主に、データのダウンロードやアップロードなど、リソースの進行状況を追跡するために使用されます。

## ドキュメント
`ProgressEvent`は、`XMLHttpRequest`や`Fetch API`を使用してリソースを取得する際に、進行状況を通知するためのイベントを提供します。このイベントは、リソースが部分的に読み込まれた際や、全体の進行状況を把握するのに役立ちます。

### 目的
`ProgressEvent`は、データ転送の進行状況を監視するために設計されています。これにより、ユーザーは進行状況バーを表示したり、処理が完了するまでの待機時間を表示したりすることが可能になります。

### 使用方法
`ProgressEvent`は、通常、次のようにしてリスナーを登録します。

```javascript
const xhr = new XMLHttpRequest();

xhr.upload.addEventListener("progress", function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Uploaded ${percentComplete}%`);
    }
});

xhr.open("POST", "upload_url");
xhr.send(formData);
```

## 例
以下は、`ProgressEvent`を使用した基本的な例です。

### アップロードの進行状況を監視する例

```javascript
const xhr = new XMLHttpRequest();
const formData = new FormData(document.querySelector('form'));

xhr.open("POST", "upload_url");

xhr.upload.addEventListener("progress", (event) => {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Uploaded: ${percentComplete}%`);
    }
});

xhr.send(formData);
```

### ダウンロードの進行状況を監視する例

```javascript
const xhr = new XMLHttpRequest();

xhr.open("GET", "file_url");
xhr.responseType = "blob";

xhr.addEventListener("progress", (event) => {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Downloaded: ${percentComplete}%`);
    }
});

xhr.onload = function() {
    if (xhr.status === 200) {
        console.log("Download complete!");
    }
};

xhr.send();
```

## 説明
`ProgressEvent`を使用する際の一般的な注意点には、以下のようなものがあります。

- `lengthComputable`プロパティが`true`の場合のみ、`total`と`loaded`のプロパティを使用して進行状況を計算できます。
- イベントリスナーを適切に設定しないと、進行状況が正しく表示されない場合があります。
- `ProgressEvent`は、`XMLHttpRequest`や`Fetch API`のアップロードやダウンロードに対してのみ有効で、他のイベントとは異なる動作をします。

## 一文要約
`ProgressEvent`は、JavaScriptにおいて非同期処理の進行状況を監視するためのイベントです。