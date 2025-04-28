<!--
Meta Description: # onpagehide イベント：JavaScript におけるページ非表示の処理 ## 概要 `onpagehide` イベントは、ブラウザのタブやウィンドウが非表示になる際に発生するイベントです。このイベントは、ユーザーがページを移動したり、タブを閉じたりしたときに、特定の処理を実行するのに役...
Meta Keywords: onpagehide, event, javascript, イベントは, window
-->

# onpagehide イベント：JavaScript におけるページ非表示の処理

## 概要
`onpagehide` イベントは、ブラウザのタブやウィンドウが非表示になる際に発生するイベントです。このイベントは、ユーザーがページを移動したり、タブを閉じたりしたときに、特定の処理を実行するのに役立ちます。

## ドキュメンテーション
`onpagehide` イベントは、`PageTransitionEvent` オブジェクトを引数として受け取ります。このイベントは、ウェブページが非表示になったときに発生し、特に Single Page Application (SPA) や動的なコンテンツを持つサイトでのユーザー体験を向上させるために重要です。

### 目的
- ページが非表示になる際の処理をカスタマイズする。
- ユーザーがページを離れた際にデータを保存する。
- アニメーションや効果を実行するためのトリガーとして使用する。

### 使用法
`onpagehide` イベントは、`window` オブジェクトまたは特定の DOM 要素に対して設定できます。以下のように、イベントリスナーを追加します。

```javascript
window.onpagehide = function(event) {
    console.log("ページが非表示になりました。");
};
```

## サンプル
### 基本的な使用例
```javascript
window.onpagehide = function(event) {
    // ページが非表示になったときの処理
    console.log("ページが非表示になりました。");
    // ユーザーの進行状況を保存する
    localStorage.setItem("userProgress", JSON.stringify(progressData));
};
```

### SPA での使用例
```javascript
const navLinks = document.querySelectorAll('a');

navLinks.forEach(link => {
    link.addEventListener('click', function(event) {
        // SPA でのページ遷移を防ぐ
        event.preventDefault();
        // 新しいページコンテンツを読み込む
        loadPageContent(link.href);
    });
});

window.onpagehide = function(event) {
    // ページが非表示になったときの処理
    console.log("ページが非表示になりました。");
};
```

## 説明
`onpagehide` イベントを使用する際の一般的な落とし穴には、以下のようなものがあります。

- **イベントのオーバーライド**: 同じオブジェクトに複数のリスナーを追加すると、最後に追加したリスナーだけが実行されるため、注意が必要です。複数の処理を必要とする場合は、`addEventListener` メソッドを使用してリスナーを追加してください。

- **非表示状態の誤解**: ページが非表示になったからといって、必ずしもタブが閉じられたわけではありません。`visibilitychange` イベントと組み合わせて使うと、より正確な状態管理が可能です。

- **ブラウザの互換性**: すべてのブラウザが `onpagehide` イベントをサポートしているわけではないため、互換性を確認することが重要です。

## 1行要約
`onpagehide` イベントは、ブラウザのタブやウィンドウが非表示になる際に発生し、ユーザーの状態を管理するために利用される重要なイベントです。