<!--
Meta Description: # onbeforeinput: JavaScript에서 입력 전 이벤트 처리하기 ## 개요 `onbeforeinput`은 사용자의 입력이 발생하기 전에 실행되는 이벤트로, 입력값을 변경하거나 유효성을 검사하는 데 유용합니다. 이 이벤트는 폼 필드와 같은 입력 요소에서 발...
Meta Keywords: event, onbeforeinput, 이벤트는, 있습니다, 이벤트
-->

# onbeforeinput: JavaScript에서 입력 전 이벤트 처리하기

## 개요
`onbeforeinput`은 사용자의 입력이 발생하기 전에 실행되는 이벤트로, 입력값을 변경하거나 유효성을 검사하는 데 유용합니다. 이 이벤트는 폼 필드와 같은 입력 요소에서 발생하며, 사용자가 키보드, 붙여넣기, 드래그 앤 드롭 등으로 데이터를 입력하기 직전에 트리거됩니다.

## 문서
### 목적
`onbeforeinput` 이벤트는 사용자가 입력을 시작하기 전에 발생하여, 입력값을 사전 처리하거나 특정 조건에 따라 입력을 차단할 수 있습니다. 이 이벤트는 `input` 요소와 같은 다양한 HTML 요소에서 사용할 수 있습니다.

### 사용법
`onbeforeinput` 이벤트는 JavaScript에서 다음과 같이 사용됩니다:

```javascript
element.onbeforeinput = function(event) {
    // 이벤트 처리 로직
};
```

또는 `addEventListener` 메서드를 사용하여 추가할 수도 있습니다:

```javascript
element.addEventListener('beforeinput', function(event) {
    // 이벤트 처리 로직
});
```

### 세부사항
- **이벤트 속성**: `event` 객체는 `data`, `inputType`, `isComposing` 등의 속성을 포함합니다. 이를 통해 입력 데이터에 대한 자세한 정보를 얻을 수 있습니다.
- **지원 브라우저**: 이 이벤트는 최신 브라우저에서 지원되며, 구형 브라우저에서는 지원되지 않을 수 있습니다.

## 예시
### 기본 사용 예제

```html
<input type="text" id="myInput" />

<script>
    document.getElementById('myInput').onbeforeinput = function(event) {
        // 입력값이 숫자인지 확인
        if (isNaN(event.data)) {
            event.preventDefault(); // 숫자가 아닐 경우 입력 차단
            alert("숫자만 입력할 수 있습니다.");
        }
    };
</script>
```

### 붙여넣기 이벤트 처리

```html
<textarea id="myTextarea"></textarea>

<script>
    document.getElementById('myTextarea').addEventListener('beforeinput', function(event) {
        if (event.inputType === 'insertFromPaste') {
            alert("붙여넣기 전에 확인하세요.");
        }
    });
</script>
```

## 설명
`onbeforeinput` 이벤트는 사용자가 입력을 시작하기 전에 발생하기 때문에, 입력값을 미리 검사하고 조정하는 데 매우 유용합니다. 그러나 이 이벤트는 모든 입력 상황에서 발생하지 않으며, 예를 들어 `cut`이나 `delete`와 같은 입력 타입에서는 트리거되지 않을 수 있습니다. 또한, 입력을 차단할 때는 `event.preventDefault()`를 호출하여 기본 동작을 방지해야 합니다.

## 한 줄 요약
`onbeforeinput`은 사용자가 입력을 시작하기 전에 발생하여 입력값을 조작하거나 유효성을 검사할 수 있는 JavaScript 이벤트입니다.