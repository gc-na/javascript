<!--
Meta Description: # onsecuritypolicyviolation に関する完全ガイド：JavaScriptのセキュリティイベント ## 概要 `onsecuritypolicyviolation` は、Content Security Policy (CSP) で定義されたセキュリティ制約に違反した際に発生す...
Meta Keywords: onsecuritypolicyviolation, event, console, log, script
-->

# onsecuritypolicyviolation に関する完全ガイド：JavaScriptのセキュリティイベント

## 概要
`onsecuritypolicyviolation` は、Content Security Policy (CSP) で定義されたセキュリティ制約に違反した際に発生するイベントを処理するためのJavaScriptのイベントハンドラです。このイベントを利用することで、ウェブアプリケーションのセキュリティを強化し、潜在的な攻撃を検知することができます。

## ドキュメンテーション
`onsecuritypolicyviolation` イベントは、CSPに違反した場合に発生します。このイベントをリッスンすることで、開発者は違反の詳細情報を取得し、適切な対応を取ることができます。

### 目的
ウェブアプリケーションにおけるセキュリティ強化を目的とし、ユーザーをリスクから守るための手段を提供します。

### 使用法
`onsecuritypolicyviolation` イベントは、ドキュメントや特定の要素に追加することができます。イベントリスナーを設定すると、CSPに違反した際にコールバック関数が呼び出されます。

### 詳細
- **プロパティ**:
  - `blockedURI`: ブロックされたリソースのURI。
  - `effectiveDirective`: 適用されたCSPディレクティブ。
  - `originalPolicy`: 適用されたCSPポリシー。
  - `scriptSample`: 違反したスクリプトのサンプル。
  
- **使用例**:
  ```javascript
  document.addEventListener('securitypolicyviolation', function(event) {
      console.log('CSP違反が発生しました:', event);
      console.log('ブロックされたURI:', event.blockedURI);
      console.log('適用されたディレクティブ:', event.effectiveDirective);
  });
  ```

## 例
以下は、`onsecuritypolicyviolation` イベントをリッスンする基本的な例です。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self';">
    <title>CSP違反の例</title>
    <script>
        document.addEventListener('securitypolicyviolation', function(event) {
            console.log('CSP違反が発生しました:');
            console.log('ブロックされたURI:', event.blockedURI);
            console.log('適用されたディレクティブ:', event.effectiveDirective);
        });
    </script>
</head>
<body>
    <script src="http://example.com/malicious-script.js"></script>
</body>
</html>
```

## 説明
`onsecuritypolicyviolation` イベントを使用する際の注意点やよくある落とし穴について説明します。

- **CSPポリシーの設定**: CSPポリシーが適切に設定されていないと、期待通りにイベントが発生しない場合があります。
- **ブラウザのサポート**: 一部の古いブラウザではこのイベントがサポートされていないため、互換性に注意が必要です。
- **ユーザー通知**: CSP違反が発生した場合、ユーザーに通知するかどうかを検討する必要があります。過度な通知はユーザー体験を損なう可能性があります。

## 一行要約
`onsecuritypolicyviolation` は、Content Security Policyに違反した際に発生するイベントで、セキュリティを強化するために使用されます。