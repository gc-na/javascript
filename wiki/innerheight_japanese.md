<!--
Meta Description: # JavaScriptのinnerHeightプロパティ：ウィンドウの高さを取得する方法 ## 概要 `innerHeight`は、JavaScriptでウィンドウの内部の高さをピクセル単位で取得するためのプロパティです。このプロパティは、ビューポートの高さを知るのに役立ち、レスポンシブデザインや...
Meta Keywords: innerheight, window, javascript, let, height
-->

# JavaScriptのinnerHeightプロパティ：ウィンドウの高さを取得する方法

## 概要
`innerHeight`は、JavaScriptでウィンドウの内部の高さをピクセル単位で取得するためのプロパティです。このプロパティは、ビューポートの高さを知るのに役立ち、レスポンシブデザインや動的コンテンツの調整に利用されます。

## ドキュメンテーション
### 目的
`window.innerHeight`は、ブラウザのビューポートの高さを返します。この値は、スクロールバーを含むウィンドウの表示可能な領域の高さを表します。

### 使用法
`innerHeight`は、以下の形式で使用します：

```javascript
let height = window.innerHeight;
```

このコードを実行すると、`height`変数に現在のビューポートの高さがピクセル単位で格納されます。

### 詳細
- **型**: `number`（数値）
- **読み取り専用**: `innerHeight`は読み取り専用のプロパティであり、直接変更することはできません。
- **ブラウザの互換性**: `innerHeight`は、主なブラウザ（Chrome、Firefox、Safari、Edgeなど）でサポートされていますが、古いブラウザではサポートがない場合があります。

## 例
### 基本的な使用例
以下は、`innerHeight`を使用して現在のウィンドウの高さをコンソールに表示する例です。

```javascript
// ウィンドウの高さを取得して表示
let currentHeight = window.innerHeight;
console.log("現在のウィンドウの高さ: " + currentHeight + "px");
```

### リサイズ時の高さの取得
ウィンドウがリサイズされたときに高さを取得する例です。

```javascript
window.addEventListener('resize', function() {
    let newHeight = window.innerHeight;
    console.log("リサイズ後のウィンドウの高さ: " + newHeight + "px");
});
```

## 説明
### よくある落とし穴
- **スクロールバーの影響**: `innerHeight`はスクロールバーを含む高さを返します。これにより、特にウィンドウが小さいデバイスでは、期待したサイズと異なる場合があります。
- **レスポンシブデザインでの使用**: レスポンシブデザインを実現する際、`innerHeight`の値が変わることがあるため、リサイズイベントに基づいて動的にコンテンツを調整する必要があります。

### 注意点
- `innerHeight`は、表示されているコンテンツやウィンドウの状態によって値が変化するため、ページの読み込み時だけでなく、リサイズ時にも再取得することをお勧めします。
- モバイルデバイスでは、アドレスバーやツールバーの表示によって、`innerHeight`の値が変わることがあります。

## 一文の要約
`innerHeight`は、JavaScriptでブラウザウィンドウの内部の高さをピクセル単位で取得するためのプロパティです。