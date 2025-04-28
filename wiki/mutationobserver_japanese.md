<!--
Meta Description: # MutationObserver: JavaScriptにおけるDOM変更の監視 ## 概要 MutationObserverは、DOM（Document Object Model）ツリーの変更を非同期で監視するためのJavaScript APIです。この機能を使用することで、要素の追加、削除、...
Meta Keywords: const, observer, callback, config, true
-->

# MutationObserver: JavaScriptにおけるDOM変更の監視

## 概要
MutationObserverは、DOM（Document Object Model）ツリーの変更を非同期で監視するためのJavaScript APIです。この機能を使用することで、要素の追加、削除、属性の変更などをリアルタイムに追跡でき、パフォーマンスを向上させることが可能です。

## ドキュメンテーション

### 目的
MutationObserverは、DOMの変更を効率的に監視するために設計されています。従来、DOMの変更を監視するには、`setInterval`や`setTimeout`を使用してポーリングを行う必要がありましたが、MutationObserverを利用することで、より効率的な方法で変更を検知できます。

### 使用方法
MutationObserverを使用するための基本的な流れは以下の通りです。

1. **Observerのインスタンスを作成する**  
   `MutationObserver`を新しいインスタンスとして生成します。コールバック関数を引数に取ります。

   ```javascript
   const observer = new MutationObserver(callback);
   ```

2. **監視対象のノードを設定する**  
   `observe`メソッドを使って、監視するDOMノードとオプションを指定します。

   ```javascript
   observer.observe(targetNode, config);
   ```

3. **停止する**  
   監視を停止するには、`disconnect`メソッドを使用します。

   ```javascript
   observer.disconnect();
   ```

### 詳細
- **callback**: DOM変更が検知された際に呼び出される関数。引数には、変更の記録（MutationRecordの配列）と、監視対象のノード（対象ノード）が渡されます。
- **config**: 監視する変更の種類を指定するオプションオブジェクト。以下のプロパティを含みます。
  - `childList`: 子ノードの追加または削除を監視する場合は`true`。
  - `attributes`: 属性の変更を監視する場合は`true`。
  - `subtree`: 子孫ノードまで監視する場合は`true`。
  - `characterData`: テキストノードの内容の変更を監視する場合は`true`。

## 例

### 基本的な使用例
以下は、DOM要素の子ノードの追加を監視する簡単な例です。

```javascript
const targetNode = document.getElementById('myElement');
const config = { childList: true };

const callback = function(mutationsList, observer) {
    mutationsList.forEach(mutation => {
        if (mutation.type === 'childList') {
            console.log('子ノードが追加または削除されました。');
        }
    });
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

### 属性の変更を監視する例
次に、要素の属性変更を監視する例です。

```javascript
const targetNode = document.getElementById('myElement');
const config = { attributes: true };

const callback = function(mutationsList, observer) {
    mutationsList.forEach(mutation => {
        if (mutation.type === 'attributes') {
            console.log(`属性が変更されました: ${mutation.attributeName}`);
        }
    });
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

## 説明
MutationObserverを使用する際の注意点として、以下の点があります。

- **パフォーマンス**: 監視する変更の量が多いと、コールバックが頻繁に呼び出されるため、パフォーマンスに影響を与える可能性があります。必要な変更のみを監視するように設定してください。
- **非同期性**: コールバックは非同期で実行されるため、DOMが変更された直後の状態を即座に取得することができません。
- **サポートブラウザ**: MutationObserverは、ほとんどのモダンブラウザでサポートされていますが、古いブラウザ（例えばInternet Explorer）では利用できません。

## 一文要約
MutationObserverは、DOMの変更を効率的に監視するためのJavaScript APIであり、リアルタイムでの反応を可能にします。