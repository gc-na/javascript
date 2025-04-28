<!--
Meta Description: # CanvasCaptureMediaStreamTrack: JavaScriptにおけるCanvas要素のキャプチャ ## 概要 `CanvasCaptureMediaStreamTrack`は、HTML Canvas要素の描画内容をメディアストリームトラックとしてキャプチャするためのインター...
Meta Keywords: canvascapturemediastreamtrack, capturestream, video, const, canvas
-->

# CanvasCaptureMediaStreamTrack: JavaScriptにおけるCanvas要素のキャプチャ

## 概要
`CanvasCaptureMediaStreamTrack`は、HTML Canvas要素の描画内容をメディアストリームトラックとしてキャプチャするためのインターフェースです。このインターフェースは、WebRTCやメディアストリーミングアプリケーションにおいて、リアルタイムでCanvasの内容を配信するのに役立ちます。

## ドキュメンテーション
`CanvasCaptureMediaStreamTrack`は、Canvasのビジュアルコンテンツをリアルタイムで取得し、メディアストリームとして扱うことを可能にします。このトラックは、`HTMLCanvasElement.captureStream()`メソッドを使用して生成されます。

### 目的
このインターフェースは、主に以下の目的で使用されます。
- Canvas描画のリアルタイムキャプチャ
- WebRTCなどのメディア通信プロトコルでの利用
- ビデオストリームの作成と配信

### 使い方
`CanvasCaptureMediaStreamTrack`を使用するには、以下の手順を実行します。

1. HTML Canvas要素を作成します。
2. Canvasの`captureStream()`メソッドを呼び出して、メディアストリームを取得します。
3. 取得したストリームをWebRTCや他のメディアAPIに接続します。

### 詳細
- `captureStream(fps)`メソッドを使用して、フレームレートを指定できます。デフォルトでは30fpsが設定されています。
- 取得したストリームは、`MediaStream`オブジェクトとして扱われ、`MediaStreamTrack`を含みます。

## 例
以下に、`CanvasCaptureMediaStreamTrack`の基本的な使用例を示します。

```javascript
// Canvas要素の作成
const canvas = document.createElement('canvas');
const context = canvas.getContext('2d');

// Canvasに描画
context.fillStyle = 'red';
context.fillRect(0, 0, 100, 100);

// メディアストリームの取得
const stream = canvas.captureStream(30); // 30fpsでキャプチャ

// ビデオ要素にストリームを設定
const video = document.createElement('video');
video.srcObject = stream;
video.play();
document.body.appendChild(video);
```

## 説明
- **共通の落とし穴**: `captureStream()`メソッドは、ブラウザによってサポートされていない場合があるため、使用する前にブラウザの互換性を確認することが重要です。
- **描画の同期**: Canvasの描画内容が変更されると、自動的にストリームに反映されますが、描画頻度が高い場合は、パフォーマンスに影響を与えることがあります。

## 一行要約
`CanvasCaptureMediaStreamTrack`は、HTML Canvasの内容をリアルタイムでキャプチャし、メディアストリームとして扱うためのJavaScriptインターフェースです。