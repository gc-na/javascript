<!--
Meta Description: # JavaScript에서 키보드 이벤트 처리하기: 키보드 입력을 다루는 방법 ## 개요 JavaScript에서 키보드 이벤트는 사용자가 키보드로 입력할 때 발생하는 이벤트입니다. 이러한 이벤트를 사용하여 웹 애플리케이션에서 사용자 입력을 감지하고 처리할 수 있습니다....
Meta Keywords: event, 키보드, 이벤트는, 이벤트, keydown
-->

# JavaScript에서 키보드 이벤트 처리하기: 키보드 입력을 다루는 방법

## 개요
JavaScript에서 키보드 이벤트는 사용자가 키보드로 입력할 때 발생하는 이벤트입니다. 이러한 이벤트를 사용하여 웹 애플리케이션에서 사용자 입력을 감지하고 처리할 수 있습니다.

## 문서
키보드 이벤트는 사용자가 키를 눌렀을 때 발생하며, 대표적으로 `keydown`, `keypress`, `keyup` 이벤트가 있습니다. 이들 이벤트는 DOM 요소에 바인딩되어 특정 키 입력에 대해 반응할 수 있도록 합니다.

### 이벤트 종류
1. **keydown**: 키가 눌릴 때 발생합니다. 키가 눌린 상태에서 계속 유지하면 여러 번 발생합니다.
2. **keypress**: 키가 눌리고 그에 따른 문자 입력이 발생할 때 발생합니다. (다만, 이 이벤트는 더 이상 권장되지 않으며, 대신 `input` 이벤트를 사용하는 것이 좋습니다.)
3. **keyup**: 키에서 손을 뗄 때 발생합니다.

### 목적
키보드 이벤트는 사용자의 입력을 실시간으로 처리하고, 다양한 상호작용을 가능하게 합니다. 예를 들어, 게임에서 캐릭터 이동, 폼 유효성 검사, 단축키 제공 등 다양한 기능을 구현할 수 있습니다.

### 사용법
키보드 이벤트를 사용하기 위해서는 JavaScript의 `addEventListener` 메서드를 사용하여 특정 DOM 요소에 이벤트를 바인딩합니다.

```javascript
const inputField = document.getElementById('myInput');

inputField.addEventListener('keydown', function(event) {
    console.log('Key pressed:', event.key);
});
```

## 예제
1. **기본 키보드 이벤트 처리**

```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        console.log('Enter 키가 눌렸습니다.');
    }
});
```

2. **특정 키 조합 처리**

```javascript
document.addEventListener('keydown', function(event) {
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault(); // 기본 저장 동작 방지
        console.log('Ctrl + S가 눌렸습니다.');
    }
});
```

## 설명
- **이벤트 전파**: 키보드 이벤트는 버블링(bubbling) 방식으로 전파되므로, 이벤트 리스너가 부모 요소에 설정되어 있다면 자식 요소에서 발생한 이벤트도 부모 요소에서 감지할 수 있습니다.
- **event.preventDefault()**: 특정 키의 기본 동작을 방지하려면 `event.preventDefault()`를 호출해야 합니다. 예를 들어, Ctrl + S 조합은 기본적으로 브라우저의 저장 기능을 호출하므로, 이를 방지하기 위해 이 메서드를 사용합니다.
- **키 코드**: `event.keyCode`는 deprecated 되었으므로 `event.key`를 사용하는 것이 좋습니다.

## 한 줄 요약
JavaScript에서 키보드 이벤트는 사용자의 키 입력을 감지하고 처리하는 기능으로, 다양한 상호작용을 가능하게 합니다.