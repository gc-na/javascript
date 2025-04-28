<!--
Meta Description: # JavaScriptのCanvasGradient：キャンバスでのグラデーションの作成 ## 概要 CanvasGradientは、HTML5のCanvas APIにおいて、色のグラデーションを定義するためのオブジェクトです。このオブジェクトを使用することで、線形または放射状のグラデーションを作...
Meta Keywords: ctx, const, addcolorstop, canvas, 200
-->

# JavaScriptのCanvasGradient：キャンバスでのグラデーションの作成

## 概要
CanvasGradientは、HTML5のCanvas APIにおいて、色のグラデーションを定義するためのオブジェクトです。このオブジェクトを使用することで、線形または放射状のグラデーションを作成し、キャンバス上に描画することができます。

## ドキュメンテーション
### 目的
CanvasGradientは、ビジュアルコンテンツの魅力を高めるために、色の変化を滑らかに表現する手段を提供します。特に、背景や図形に深みを持たせる際に利用されます。

### 使用法
CanvasGradientは、`CanvasRenderingContext2D`の`createLinearGradient`または`createRadialGradient`メソッドを使用して作成されます。

#### メソッド
1. **createLinearGradient(x0, y0, x1, y1)**
   - 線形グラデーションを作成します。
   - 引数:
     - `x0`, `y0`: グラデーションの開始点の座標。
     - `x1`, `y1`: グラデーションの終了点の座標。

2. **createRadialGradient(x0, y0, r0, x1, y1, r1)**
   - 放射状グラデーションを作成します。
   - 引数:
     - `x0`, `y0`: 内側の円の中心の座標。
     - `r0`: 内側の円の半径。
     - `x1`, `y1`: 外側の円の中心の座標。
     - `r1`: 外側の円の半径。

### グラデーションの追加
作成したグラデーションに色を追加するには、`addColorStop(position, color)`メソッドを使用します。

- **position**: グラデーションの位置（0から1の範囲）。
- **color**: 色（CSSカラー形式）。

## 例
### 基本的な使用例
以下は線形グラデーションを使用した基本的な例です。

```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// 線形グラデーションの作成
const gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'blue');

// グラデーションを塗りつぶしに設定
ctx.fillStyle = gradient;
ctx.fillRect(0, 0, 200, 200);
```

### 放射状グラデーションの例
次の例は放射状グラデーションの使用方法を示しています。

```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// 放射状グラデーションの作成
const radialGradient = ctx.createRadialGradient(100, 100, 20, 100, 100, 100);
radialGradient.addColorStop(0, 'yellow');
radialGradient.addColorStop(1, 'green');

// グラデーションを塗りつぶしに設定
ctx.fillStyle = radialGradient;
ctx.fillRect(0, 0, 200, 200);
```

## 説明
- **一般的な落とし穴**: グラデーションの位置や色の指定は、正しい範囲で行う必要があります。位置は0から1の値で指定し、間違った値を使用すると意図しない結果になることがあります。
- **ブラウザ互換性**: Canvas APIはほとんどのモダンブラウザでサポートされていますが、古いブラウザでは動作しない可能性があるため、対応状況を確認することが重要です。

## 一文の要約
CanvasGradientは、JavaScriptのCanvas APIを使用して、線形または放射状の色のグラデーションを作成し、ビジュアルコンテンツを強化するための機能です。