<!--
Meta Description: # JavaScriptのontransitionrunイベント: 使用方法と解説 ## 概要 `ontransitionrun`は、CSSトランジションが開始されたときに発火するイベントです。このイベントを使用することで、トランジションの開始時に特定のアクションを実行できます。 ## ドキュメント...
Meta Keywords: ontransitionrun, element, transition, button, const
-->

# JavaScriptのontransitionrunイベント: 使用方法と解説

## 概要
`ontransitionrun`は、CSSトランジションが開始されたときに発火するイベントです。このイベントを使用することで、トランジションの開始時に特定のアクションを実行できます。

## ドキュメント
`ontransitionrun`は、`Element`インターフェースのプロパティであり、トランジションが実行されるときに呼び出される関数を指定します。このイベントは、CSSの`transition`プロパティを使用して視覚的な変化を作成する際に非常に便利です。

### 使用方法
`ontransitionrun`イベントを使用するには、対象の要素にイベントリスナーを設定します。次のように記述します。

```javascript
const element = document.querySelector('.my-element');

element.ontransitionrun = function(event) {
  console.log('トランジションが開始されました。');
};
```

### 詳細
このイベントは、トランジションの開始を検知するために利用され、トランジションが進行する間に何か特別な処理を行いたい場合に役立ちます。例えば、トランジションが始まったことを通知するメッセージを表示したり、アニメーションの進行状況を追跡することが可能です。

## 例
以下に、`ontransitionrun`の基本的な使用例を示します。

```html
<div class="my-element" style="width: 100px; height: 100px; background-color: red; transition: background-color 1s;"></div>
<button id="start-transition">トランジション開始</button>

<script>
  const element = document.querySelector('.my-element');
  const button = document.getElementById('start-transition');

  element.ontransitionrun = function(event) {
    console.log('トランジションが開始されました。');
  };

  button.addEventListener('click', function() {
    element.style.backgroundColor = 'blue';
  });
</script>
```

この例では、ボタンをクリックすると要素の背景色が赤から青に変わり、その際に`ontransitionrun`イベントが発火し、コンソールにメッセージが表示されます。

## 説明
`ontransitionrun`イベントを使用する際の注意点として、トランジションが実行される要素とそのスタイルが正しく設定されていることを確認する必要があります。トランジションが適用されていない場合、このイベントは発火しません。また、複数のトランジションが同時に発生している場合、イベントはそれぞれのトランジションごとに発火しますので、その点に留意する必要があります。

## 一文要約
`ontransitionrun`は、CSSトランジションが開始された際に実行されるイベントで、トランジションの開始時に特定のアクションを実行するために利用されます。