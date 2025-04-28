<!--
Meta Description: # devicePixelRatio: JavaScriptのデバイスピクセル比の理解 ## 概要 `devicePixelRatio`は、ブラウザで表示される画面の物理的なピクセルとCSSピクセルの比率を示すプロパティです。これにより、異なるデバイスの解像度に応じた最適な表示が可能になります。 #...
Meta Keywords: devicepixelratio, window, const, ratio, canvas
-->

# devicePixelRatio: JavaScriptのデバイスピクセル比の理解

## 概要
`devicePixelRatio`は、ブラウザで表示される画面の物理的なピクセルとCSSピクセルの比率を示すプロパティです。これにより、異なるデバイスの解像度に応じた最適な表示が可能になります。

## ドキュメント
### 目的
`window.devicePixelRatio`プロパティは、デバイスの画面がどの程度の解像度を持っているかを示します。特に、高解像度のディスプレイ（例：Retinaディスプレイ）では、物理的なピクセル数がCSSピクセル数に比べて多くなるため、このプロパティが重要になります。

### 使用法
`devicePixelRatio`は、通常は次のようにアクセスします：

```javascript
const ratio = window.devicePixelRatio;
```

このプロパティは、数値としてデバイスのピクセル比を返します。例えば、通常のディスプレイでは1、Retinaディスプレイでは2や3になることがあります。

### 詳細
- **型**: `Number`
- **初期値**: 通常は1（通常のディスプレイ）
- **変更**: ユーザーがズームを行ったり、デバイスの設定を変更した場合に変更される可能性があります。

`devicePixelRatio`を利用することで、画像やキャンバスのレンダリングをデバイスの解像度に合わせて調整することができます。これにより、視覚的な品質が向上します。

## 例
### 基本的な使用例
```javascript
// デバイスピクセル比を取得
const ratio = window.devicePixelRatio;
console.log(`デバイスピクセル比: ${ratio}`);

// 高解像度画像を使用する例
const img = new Image();
img.src = ratio > 1 ? 'image@2x.png' : 'image.png';
document.body.appendChild(img);
```

### Canvasでの使用例
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// デバイスピクセル比を考慮したキャンバスサイズの設定
canvas.width = 300 * window.devicePixelRatio;
canvas.height = 150 * window.devicePixelRatio;
ctx.scale(window.devicePixelRatio, window.devicePixelRatio);

// 描画内容
ctx.fillStyle = 'blue';
ctx.fillRect(0, 0, 300, 150);
```

## 説明
`devicePixelRatio`を使用する際の一般的な落とし穴として、異なるデバイス間での一貫した表示を確保することが挙げられます。特に、画像やキャンバスを描画する際には、解像度に応じたサイズ調整を行う必要があります。これを怠ると、画像がぼやけたり、キャンバスの描画が不正確になる可能性があります。

また、`devicePixelRatio`は動的に変わることがあるため、ユーザーがズームインまたはズームアウトした際にも再計算が必要です。したがって、ページのリサイズやズームイベントに対してハンドラを設定することが重要です。

## 一文要約
`devicePixelRatio`は、デバイスの物理的ピクセルとCSSピクセルの比率を示し、デバイスに応じた最適な表示を実現するために使用されるJavaScriptのプロパティです。