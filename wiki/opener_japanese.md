<!--
Meta Description: # JavaScriptにおける「opener」: ウィンドウ操作の基本 ## 概要 JavaScriptの「opener」は、ウィンドウやタブを操作するための重要なプロパティであり、特に新しく開かれたウィンドウがどの親ウィンドウから開かれたのかを示します。この機能は、ポップアップウィンドウやダイア...
Meta Keywords: opener, html, window, head, title
-->

# JavaScriptにおける「opener」: ウィンドウ操作の基本

## 概要
JavaScriptの「opener」は、ウィンドウやタブを操作するための重要なプロパティであり、特に新しく開かれたウィンドウがどの親ウィンドウから開かれたのかを示します。この機能は、ポップアップウィンドウやダイアログボックスを扱う際に役立ちます。

## ドキュメンテーション
### 目的
「opener」プロパティは、現在のウィンドウを開いた元のウィンドウへの参照を提供します。これにより、開いたウィンドウが親ウィンドウの情報や関数にアクセスできるようになります。

### 使用法
「opener」は、ウィンドウオブジェクトの一部として使用されます。新しいウィンドウを開く際に、親ウィンドウからの情報を取得したり、親ウィンドウの関数を呼び出したりすることができます。

```javascript
// 新しいウィンドウを開く
let newWindow = window.open('https://example.com');

// 親ウィンドウにメッセージを送信
if (newWindow.opener) {
    newWindow.opener.alert('新しいウィンドウが開かれました');
}
```

### 詳細
- **型**: Window
- **初期値**: null（親ウィンドウがない場合）
- **ブラウザサポート**: 主なモダンブラウザ（Chrome, Firefox, Safari, Edge）でサポートされています。

## 例
以下の例では、親ウィンドウから新しいウィンドウを開き、そのウィンドウ内から親ウィンドウにメッセージを送信します。

```html
<!-- 親ウィンドウ -->
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>親ウィンドウ</title>
    <script>
        function openChild() {
            let childWindow = window.open('child.html');
        }
    </script>
</head>
<body>
    <button onclick="openChild()">子ウィンドウを開く</button>
</body>
</html>
```

```html
<!-- 子ウィンドウ (child.html) -->
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>子ウィンドウ</title>
    <script>
        window.onload = function() {
            if (opener) {
                opener.alert('親ウィンドウからのメッセージ');
            }
        };
    </script>
</head>
<body>
    <p>このウィンドウは親ウィンドウから開かれました。</p>
</body>
</html>
```

## 説明
- **セキュリティ制限**: 「opener」プロパティは、同一オリジンポリシーに従います。異なるオリジン（ドメイン）から開かれたウィンドウに対しては、親ウィンドウのプロパティやメソッドにアクセスできません。
- **メモリリーク**: 「opener」を使ったウィンドウ間の参照が循環する場合、メモリリークを引き起こす可能性があります。適切にウィンドウを閉じることが重要です。

## 一文要約
JavaScriptの「opener」プロパティは、現在のウィンドウを開いた親ウィンドウへの参照を提供し、ウィンドウ間の相互作用を可能にします。