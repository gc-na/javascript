<!--
Meta Description: # CanvasRenderingContext2D: JavaScriptでの2D描画コンテキスト ## 概要 `CanvasRenderingContext2D`は、HTML5の`<canvas>`要素で2Dグラフィックスを描画するためのAPIです。このコンテキストを使用すると、図形、テキスト、...
Meta Keywords: ctx, canvas, const, canvasrenderingcontext2d, getcontext
-->

# CanvasRenderingContext2D: JavaScriptでの2D描画コンテキスト

## 概要
`CanvasRenderingContext2D`は、HTML5の`<canvas>`要素で2Dグラフィックスを描画するためのAPIです。このコンテキストを使用すると、図形、テキスト、画像を描画・操作することができます。

## ドキュメント
`CanvasRenderingContext2D`は、HTMLの`<canvas>`要素を介して取得されます。`getContext('2d')`メソッドを呼び出すことで、2D描画コンテキストのインスタンスを取得し、グラフィックスを描画するためのメソッドやプロパティを使用できます。

### 主な用途
- **図形の描画**: 四角形、円、線などの基本的な図形を描画できます。
- **テキストの描画**: フォント、サイズ、色を指定してテキストを描画できます。
- **画像の操作**: 画像をキャンバスに描画し、サイズ変更やトリミングが可能です。
- **アニメーション**: フレームごとに描画を更新することでアニメーションを作成できます。

### 使用方法
以下は、`CanvasRenderingContext2D`を使用する基本的な手順です。

1. HTMLで`<canvas>`要素を作成します。
   ```html
   <canvas id="myCanvas" width="500" height="500"></canvas>
   ```

2. JavaScriptでコンテキストを取得し、描画を行います。
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');

   // 矩形の描画
   ctx.fillStyle = 'blue';
   ctx.fillRect(20, 20, 150, 100);
   ```

## 例
以下は、`CanvasRenderingContext2D`を使用した基本的な例です。

### 四角形の描画
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

ctx.fillStyle = 'red';
ctx.fillRect(10, 10, 100, 100);
```

### 円の描画
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

ctx.beginPath();
ctx.arc(150, 150, 50, 0, Math.PI * 2);
ctx.fillStyle = 'green';
ctx.fill();
```

### テキストの描画
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

ctx.font = '30px Arial';
ctx.fillStyle = 'black';
ctx.fillText('Hello, Canvas!', 50, 50);
```

## 説明
`CanvasRenderingContext2D`を使用する際の一般的な注意点や罠には以下のようなものがあります。

- **座標系**: キャンバスの左上が原点(0, 0)であり、Y軸は下方向に増加します。これに慣れることが重要です。
- **描画のクリア**: 新しいフレームを描画する前に、`clearRect()`メソッドを使用してキャンバスをクリアすることが必要です。
- **アニメーション**: アニメーションを作成する場合、`requestAnimationFrame()`を利用してスムーズな描画を行うことが推奨されます。

## 一文要約
`CanvasRenderingContext2D`は、HTML5のキャンバス要素を使用して、2Dグラフィックスを描画および操作するための強力なAPIです。