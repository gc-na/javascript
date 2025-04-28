<!--
Meta Description: # JavaScriptのCanvasPattern: キャンバスのパターン描画 ## 概要 `CanvasPattern`は、HTML5のCanvas APIにおいてビジュアルコンテンツを描画するためのパターンを作成する機能です。この機能を使用することで、繰り返しパターンを簡単にキャンバス上に描画...
Meta Keywords: canvaspattern, createpattern, canvas, repeat, image
-->

# JavaScriptのCanvasPattern: キャンバスのパターン描画

## 概要
`CanvasPattern`は、HTML5のCanvas APIにおいてビジュアルコンテンツを描画するためのパターンを作成する機能です。この機能を使用することで、繰り返しパターンを簡単にキャンバス上に描画することができます。

## ドキュメント
### 目的
`CanvasPattern`は、`CanvasRenderingContext2D.createPattern()`メソッドを使用して生成され、画像や他のキャンバスを背景として繰り返すことができます。これにより、より複雑で視覚的に魅力的なデザインを作成することが可能です。

### 使用法
1. **コンテキストの取得**: 最初に、`<canvas>`要素の2Dコンテキストを取得します。
2. **画像またはキャンバスの準備**: 繰り返したい画像やキャンバスを準備します。
3. **パターンの作成**: `createPattern()`メソッドを使用して新しいパターンを作成します。
4. **描画**: そのパターンを使用して、キャンバス上に図形や画像を描画します。

### 詳細
- **メソッドシグネチャ**: 
  ```javascript
  CanvasPattern createPattern(HTMLImageElement image, string repetition);
  ```
- **引数**:
  - `image`: 描画する画像またはキャンバス。
  - `repetition`: 繰り返しの方法を指定する文字列（例: `"repeat"`, `"repeat-x"`, `"repeat-y"`, `"no-repeat"`）。
  
- **戻り値**: `CanvasPattern`オブジェクト。

## 例
### 基本的な使用例
```javascript
// Canvas要素の取得
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// 画像の読み込み
const img = new Image();
img.src = 'path/to/image.png';
img.onload = function() {
    // パターンの作成
    const pattern = ctx.createPattern(img, 'repeat');
    ctx.fillStyle = pattern;
    ctx.fillRect(0, 0, canvas.width, canvas.height);
};
```

## 説明
- **共通の落とし穴**: 
  - 画像が完全に読み込まれる前に`createPattern()`を呼び出すと、`null`が返されます。必ず`onload`イベント内で呼び出してください。
  
- **パフォーマンス**: 複雑なパターンを描画する際、描画速度が低下する可能性があります。画像サイズやパターンの複雑さに注意が必要です。

- **サポート**: `CanvasPattern`は、モダンなブラウザで広くサポートされていますが、古いブラウザでは動作しない場合があります。

## 一文の要約
`CanvasPattern`は、HTML5のCanvas APIにおいて、画像やキャンバスを繰り返して描画するためのパターンを作成する機能です。