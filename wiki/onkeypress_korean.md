<!--
Meta Description: # JavaScript onkeypress 이벤트: 키보드 입력 감지하기 ## 개요 `onkeypress`는 JavaScript에서 키보드 입력을 감지하기 위해 사용되는 이벤트 핸들러입니다. 사용자 키 입력 시 특정 동작을 수행하도록 프로그래밍할 수 있습니다. ## 문...
Meta Keywords: onkeypress, event, key, 이벤트는, html
-->

# JavaScript onkeypress 이벤트: 키보드 입력 감지하기

## 개요
`onkeypress`는 JavaScript에서 키보드 입력을 감지하기 위해 사용되는 이벤트 핸들러입니다. 사용자 키 입력 시 특정 동작을 수행하도록 프로그래밍할 수 있습니다.

## 문서화

### 목적
`onkeypress` 이벤트는 사용자가 키를 눌렀을 때 발생합니다. 이 이벤트는 일반적으로 텍스트 입력 필드와 같은 요소에서 사용자 입력을 처리하는 데 사용됩니다.

### 사용법
`onkeypress` 이벤트는 HTML 요소에 직접 추가하거나 JavaScript 코드에서 이벤트 리스너를 통해 설정할 수 있습니다. 

**HTML 예시:**
```html
<input type="text" onkeypress="handleKeyPress(event)">
```

**JavaScript 예시:**
```javascript
const inputField = document.getElementById('myInput');
inputField.onkeypress = function(event) {
    console.log('Key pressed: ', event.key);
};
```

### 세부사항
- `onkeypress` 이벤트는 일반적으로 알파벳, 숫자 및 특수 문자를 포함한 문자 키 입력에 반응합니다.
- 이 이벤트는 `event.key` 프로퍼티를 통해 어떤 키가 눌렸는지 확인할 수 있습니다.
- `onkeypress`는 키가 눌린 순간에만 발생하며, 키가 눌렸다가 떼어질 때는 발생하지 않습니다.

## 예제
1. 기본 키 입력 감지:
```html
<input type="text" onkeypress="alert('Key pressed!')">
```

2. 어떤 키가 눌렸는지 콘솔에 출력:
```html
<input type="text" id="myInput">
<script>
    document.getElementById('myInput').onkeypress = function(event) {
        console.log('Pressed key: ' + event.key);
    };
</script>
```

3. 특정 키 입력 방지:
```html
<input type="text" onkeypress="return event.key !== 'Enter';">
```

## 설명
- `onkeypress`는 모든 키 입력을 감지하지만, 기능 키(예: Shift, Ctrl, Alt)와 같은 비문자 키는 무시합니다.
- 이 이벤트는 현대 웹 브라우저에서 지원되지만, `onkeydown` 및 `onkeyup` 이벤트를 대신 사용하는 것이 좋습니다. 이 이벤트들은 더 넓은 범위의 키 입력을 감지합니다.
- 사용자 경험을 개선하기 위해 입력 필드에 대한 유효성 검사를 수행할 때 유용하게 사용할 수 있습니다.

## 한 줄 요약
`onkeypress`는 JavaScript에서 사용자 키보드 입력을 감지하고 반응하는 이벤트 핸들러입니다.