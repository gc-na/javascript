<!--
Meta Description: # HTMLSourceElement: JavaScriptでのHTMLソース要素の操作 ## 概要 `HTMLSourceElement`は、HTML `<source>` 要素を表すインターフェースであり、JavaScriptを用いてメディアコンテンツのソースを指定するために使用されます。この...
Meta Keywords: audio, video, htmlsourceelement, src, type
-->

# HTMLSourceElement: JavaScriptでのHTMLソース要素の操作

## 概要
`HTMLSourceElement`は、HTML `<source>` 要素を表すインターフェースであり、JavaScriptを用いてメディアコンテンツのソースを指定するために使用されます。この要素は、`<video>` や `<audio>` タグ内で、異なるフォーマットのメディアファイルを提供することができます。

## ドキュメンテーション
### 目的
`HTMLSourceElement`は、メディア要素に対して異なるソースを指定し、ブラウザが最適なフォーマットを選択できるようにするために使用されます。これにより、ユーザーの環境に応じたメディアコンテンツの再生が可能になります。

### 使用法
`HTMLSourceElement`は主に`<audio>`や`<video>`要素内で使用されます。以下は、一般的な構造です：

```html
<video controls>
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.ogg" type="video/ogg">
    お使いのブラウザはvideoタグに対応していません。
</video>
```

### プロパティ
- `src`: メディアファイルのURLを指定します。
- `type`: メディアファイルのMIMEタイプを指定します。

### メソッド
`HTMLSourceElement`自体にはメソッドはありませんが、親要素である`HTMLMediaElement`（`<audio>`や`<video>`）でメディアの制御が可能です。

## 例
基本的な使用例は以下の通りです：

```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    お使いのブラウザはaudioタグに対応していません。
</audio>
```

この例では、ブラウザは最初に`audio.mp3`を試行し、それがサポートされていない場合は`audio.ogg`にフォールバックします。

## 説明
- **共通の落とし穴**: `src`や`type`が正しく指定されていない場合、ブラウザがメディアを再生できないことがあります。また、ファイルへのパスが正しいか確認することが重要です。
- **互換性**: 各ブラウザがサポートするコーデックが異なるため、複数のフォーマットを提供することが推奨されます。
- **アクセシビリティ**: メディア要素に適切なテキストを提供することで、アクセシビリティを向上させることができます。`<track>`要素を使って字幕を追加することも考慮してください。

## 一文要約
`HTMLSourceElement`は、JavaScriptを利用してHTMLのメディア要素内で異なるメディアソースを指定するためのインターフェースです。