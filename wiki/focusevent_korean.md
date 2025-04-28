<!--
Meta Description: # FocusEvent: 자바스크립트에서의 포커스 이벤트 ## 개요 FocusEvent는 자바스크립트에서 요소가 포커스를 얻거나 잃을 때 발생하는 이벤트를 다룹니다. 이 이벤트는 사용자 상호작용을 기반으로 하여, 웹 애플리케이션의 접근성과 사용자 경험을 향상시키는 데 ...
Meta Keywords: focus, input, 포커스를, 포커스, addeventlistener
-->

# FocusEvent: 자바스크립트에서의 포커스 이벤트

## 개요
FocusEvent는 자바스크립트에서 요소가 포커스를 얻거나 잃을 때 발생하는 이벤트를 다룹니다. 이 이벤트는 사용자 상호작용을 기반으로 하여, 웹 애플리케이션의 접근성과 사용자 경험을 향상시키는 데 중요한 역할을 합니다.

## 문서화
FocusEvent는 `focus` 및 `blur` 이벤트의 일종으로, HTML 요소가 사용자 입력을 받을 준비가 되었을 때(포커스를 얻었을 때) 또는 입력을 받을 수 없게 되었을 때(포커스를 잃었을 때) 발생합니다. 이 이벤트는 주로 폼 요소, 버튼, 링크 등에서 사용됩니다.

### 사용법
FocusEvent는 다음과 같은 방법으로 사용할 수 있습니다:

```javascript
// 포커스를 얻었을 때
element.addEventListener('focus', function(event) {
    console.log('Element has received focus');
});

// 포커스를 잃었을 때
element.addEventListener('blur', function(event) {
    console.log('Element has lost focus');
});
```

### 속성
FocusEvent에는 다음과 같은 주요 속성이 있습니다:
- `relatedTarget`: 포커스를 잃은 요소와 관련된 요소를 나타냅니다.

## 예제
### 기본 사용 예
```html
<input type="text" id="name" placeholder="이름을 입력하세요">
<script>
    const input = document.getElementById('name');

    input.addEventListener('focus', function() {
        console.log('Input field is focused.');
    });

    input.addEventListener('blur', function() {
        console.log('Input field lost focus.');
    });
</script>
```

### 다른 요소에서 포커스 얻기
```html
<button id="focusButton">Focus the Input</button>
<input type="text" id="nameInput" placeholder="이름을 입력하세요">

<script>
    const button = document.getElementById('focusButton');
    const input = document.getElementById('nameInput');

    button.addEventListener('click', function() {
        input.focus(); // 버튼 클릭 시 입력 필드에 포커스
    });
</script>
```

## 설명
FocusEvent를 사용할 때 주의해야 할 점은 이벤트가 발생하는 대상 요소가 사용자에게 보이거나 활성화되어 있어야 한다는 점입니다. 예를 들어, 숨겨진 요소나 비활성화된 요소에서는 포커스 이벤트가 발생하지 않습니다. 또한, `focus` 이벤트가 발생한 후에 다른 요소가 포커스를 잃게 되면 `blur` 이벤트도 함께 발생합니다.

또한, 포커스 이벤트는 키보드 내비게이션 및 접근성을 고려하여 적절히 사용해야 합니다. 예를 들어, 키보드 사용자에게 입력 필드가 활성화되었음을 나타내는 방법으로 `focus` 이벤트를 활용할 수 있습니다.

## 한 줄 요약
FocusEvent는 자바스크립트에서 요소의 포커스 상태 변화를 감지하는 이벤트입니다.