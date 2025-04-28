<!--
Meta Description: # GPUExternalTexture: JavaScriptでのGPU外部テクスチャの利用法 ## 概要 `GPUExternalTexture`は、WebGPU APIにおけるテクスチャオブジェクトで、GPU外部からのテクスチャデータを扱うための機能です。この機能を利用することで、WebGLや...
Meta Keywords: gpuexternaltexture, const, source, createexternaltexture, device
-->

# GPUExternalTexture: JavaScriptでのGPU外部テクスチャの利用法

## 概要
`GPUExternalTexture`は、WebGPU APIにおけるテクスチャオブジェクトで、GPU外部からのテクスチャデータを扱うための機能です。この機能を利用することで、WebGLやCanvasなど、他のレンダリングコンテキストで作成したテクスチャをWebGPUにインポートし、高速なグラフィックス処理を実現できます。

## ドキュメント
### 目的
`GPUExternalTexture`は、異なるグラフィックスAPI間でテクスチャデータを効率的に共有するために設計されています。特に、WebGPUを使用する際に、他の技術で生成されたテクスチャを容易に利用できるようになります。

### 使用法
`GPUExternalTexture`を生成するには、`GPUDevice`の`createExternalTexture`メソッドを使用します。以下に基本的な構文を示します。

```javascript
const externalTexture = device.createExternalTexture({
    source: externalSource, // 外部ソースとなるテクスチャ
    // オプションで他のプロパティを指定可能
});
```

`source`には、HTMLImageElement、HTMLCanvasElement、または他のGPU外部データを指定できます。

### 詳細
- **プロパティ**:
  - `source`: テクスチャとして使用する外部データを指定します。
  
- **メソッド**:
  - `createExternalTexture`: 新しい外部テクスチャを作成します。

- **互換性**: `GPUExternalTexture`は、WebGPU APIをサポートするブラウザでのみ利用可能です。ブラウザのバージョンによっては、機能が制限される場合があります。

## 例
以下に、`GPUExternalTexture`の基本的な使用例を示します。

```javascript
// GPUデバイスの取得
const adapter = await navigator.gpu.requestAdapter();
const device = await adapter.requestDevice();

// 外部テクスチャの作成
const img = document.getElementById('myImage');
const externalTexture = device.createExternalTexture({
    source: img,
});

// シェーダーやパイプラインで使用
```

## 説明
- **共通の落とし穴**:
  - `source`で指定するオブジェクトが、GPUに適切に認識されない場合があります。特に、HTMLCanvasElementやHTMLImageElementがまだ読み込まれていない状態で指定すると、エラーが発生する可能性があります。

- **注意点**:
  - テクスチャの更新が必要な場合、外部ソースも更新されることを確認してください。更新が反映されない場合、古いデータが表示されることがあります。

## 一文要約
`GPUExternalTexture`は、WebGPUにおいて異なるグラフィックスAPIからのテクスチャデータを効率的に利用するための機能です。