<!--
Meta Description: # onbeforeinstallprompt: JavaScriptのPWAインストールプロンプトを制御するイベント ## 概要 `onbeforeinstallprompt`は、Progressive Web Apps (PWA) のインストールプロンプトを制御するためのJavaScriptイベ...
Meta Keywords: onbeforeinstallprompt, deferredprompt, installbutton, beforeinstallprompt, window
-->

# onbeforeinstallprompt: JavaScriptのPWAインストールプロンプトを制御するイベント

## 概要
`onbeforeinstallprompt`は、Progressive Web Apps (PWA) のインストールプロンプトを制御するためのJavaScriptイベントです。このイベントを使用すると、ユーザーにアプリケーションをインストールするためのカスタムプロンプトを表示することができます。

## ドキュメンテーション
`onbeforeinstallprompt`イベントは、ユーザーがウェブアプリをインストールできる状態になったときにトリガーされます。このイベントをリッスンすることで、開発者はデフォルトのインストールプロンプトをカスタマイズしたり、ユーザーのアクションに基づいてインストールを促すことができます。

### 使用方法
1. **イベントリスナーの追加**: `beforeinstallprompt`イベントをリッスンするためには、`window`オブジェクトにイベントリスナーを追加します。
2. **イベントの防止**: デフォルトのプロンプトを表示しないように、`event.preventDefault()`を使用します。
3. **プロンプトの表示**: ユーザーのアクションに応じて、プロンプトを表示します。

### 例
以下は、基本的な使用例です。

```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
    // デフォルトのプロンプトを防止
    e.preventDefault();
    // イベントを保存
    deferredPrompt = e;
    
    // カスタムボタンを表示
    const installButton = document.getElementById('installButton');
    installButton.style.display = 'block';

    installButton.addEventListener('click', () => {
        // プロンプトを表示
        deferredPrompt.prompt();
        
        // ユーザーの応答を確認
        deferredPrompt.userChoice.then((choiceResult) => {
            if (choiceResult.outcome === 'accepted') {
                console.log('ユーザーはインストールを承認しました');
            } else {
                console.log('ユーザーはインストールを拒否しました');
            }
            deferredPrompt = null; // リセット
        });
    });
});
```

## 説明
`onbeforeinstallprompt`イベントを使用する際の一般的な落とし穴や注意点を以下に示します。

- **ブラウザの互換性**: このイベントはすべてのブラウザでサポートされているわけではありません。主にChromeおよびその派生ブラウザで利用可能です。
- **ユーザーエクスペリエンス**: デフォルトのプロンプトを表示しない場合、ユーザーがアプリをインストールする機会を逃す可能性があるため、適切なタイミングでカスタムプロンプトを表示することが重要です。
- **イベントの一回性**: `beforeinstallprompt`イベントは一度しか発火しないため、ユーザーがプロンプトを拒否した場合、再度表示するためにはアプリを再訪問する必要があります。

## 一文まとめ
`onbeforeinstallprompt`は、ユーザーにPWAをインストールするためのカスタムプロンプトを表示するJavaScriptイベントです。