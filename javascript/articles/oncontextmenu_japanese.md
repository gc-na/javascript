<!--
Meta Description: # oncontextmenu: JavaScriptの右クリックメニューイベント ## 概要 `oncontextmenu`は、JavaScriptにおいて右クリックメニュー（コンテキストメニュー）を制御するためのイベントハンドラです。このイベントは、ユーザーが要素上で右クリックしたときに発生し、...
Meta Keywords: oncontextmenu, event, div, style, preventdefault
-->

# oncontextmenu: JavaScriptの右クリックメニューイベント

## 概要
`oncontextmenu`は、JavaScriptにおいて右クリックメニュー（コンテキストメニュー）を制御するためのイベントハンドラです。このイベントは、ユーザーが要素上で右クリックしたときに発生し、カスタムメニューの表示やデフォルトメニューの無効化に使用されます。

## ドキュメンテーション
`oncontextmenu`は、HTML要素に関連付けることができるイベントです。このイベントハンドラは、ユーザーが要素を右クリックしたときに呼び出されます。通常、デフォルトのコンテキストメニューが表示されますが、`event.preventDefault()`を使用することで、これを無効にすることができます。

### 使用方法
```html
<div id="myElement" oncontextmenu="myFunction(event)">右クリックしてみてください</div>

<script>
function myFunction(event) {
    event.preventDefault(); // デフォルトのメニューを無効化
    alert("カスタムメニューを表示します");
}
</script>
```

### 詳細
- **イベントオブジェクト**: `oncontextmenu`イベントには、イベントオブジェクトが渡され、これを通じて位置情報やその他の情報を取得できます。
- **カスタムメニューの実装**: `oncontextmenu`を利用して、独自のコンテキストメニューを作成し、表示することが可能です。

## 例
### 基本的な使用例
以下のコードは、右クリック時にアラートを表示します。

```html
<button oncontextmenu="alert('右クリックされました'); return false;">右クリック</button>
```

### カスタムメニューの例
```html
<div id="customMenu" style="display:none; position:absolute; background-color: white; border: 1px solid #ccc;">
    <ul>
        <li>オプション1</li>
        <li>オプション2</li>
    </ul>
</div>

<div id="myElement" oncontextmenu="showMenu(event)">右クリックしてカスタムメニューを表示</div>

<script>
function showMenu(event) {
    event.preventDefault();
    var menu = document.getElementById('customMenu');
    menu.style.left = event.pageX + 'px';
    menu.style.top = event.pageY + 'px';
    menu.style.display = 'block';
}

window.addEventListener('click', function() {
    document.getElementById('customMenu').style.display = 'none';
});
</script>
```

## 説明
- **デフォルト動作の無効化**: `event.preventDefault()`を使用しないと、ブラウザのデフォルトの右クリックメニューが表示されます。
- **イベントのバブリング**: `oncontextmenu`イベントは、DOMツリーをバブリングするので、親要素にイベントハンドラを設定することもできます。
- **ブラウザ互換性**: ほとんどの現代のブラウザでサポートされていますが、特定の古いブラウザでは動作が異なる場合があります。

## 一文要約
`oncontextmenu`は、JavaScriptで右クリックイベントを管理し、カスタムメニューの表示やデフォルトメニューの無効化を可能にするイベントハンドラです。