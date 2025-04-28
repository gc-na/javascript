<!--
Meta Description: # EventTarget: JavaScript에서 이벤트를 처리하는 방법 ## 개요 `EventTarget`은 JavaScript에서 이벤트를 처리하고 전파하는 데 사용되는 인터페이스입니다. DOM (Document Object Model)의 요소, XMLHttpReq...
Meta Keywords: 이벤트, 이벤트를, 리스너를, 있습니다, click
-->

# EventTarget: JavaScript에서 이벤트를 처리하는 방법

## 개요
`EventTarget`은 JavaScript에서 이벤트를 처리하고 전파하는 데 사용되는 인터페이스입니다. DOM (Document Object Model)의 요소, XMLHttpRequest, WebSocket 등 다양한 객체가 이 인터페이스를 구현하여 이벤트 리스너를 추가하고 이벤트를 발생시킬 수 있습니다.

## 문서화
### 목적
`EventTarget` 인터페이스는 이벤트를 등록하고 해제하며, 이벤트가 발생할 때 해당 이벤트를 처리하는 메서드를 제공합니다. 이를 통해 개발자는 사용자 상호작용이나 다른 비동기 작업에 대해 반응할 수 있습니다.

### 사용법
`EventTarget`의 주요 메서드는 다음과 같습니다:
- `addEventListener(type, listener, options)`: 특정 유형의 이벤트에 대해 리스너를 추가합니다.
- `removeEventListener(type, listener, options)`: 특정 유형의 이벤트에 대해 리스너를 제거합니다.
- `dispatchEvent(event)`: 지정된 이벤트를 발생시킵니다.

### 세부 사항
- `type`: 문자열로, 이벤트의 종류를 지정합니다 (예: `"click"`, `"load"`).
- `listener`: 이벤트가 발생했을 때 호출되는 함수입니다.
- `options`: 선택적 매개변수로, 이벤트 리스너의 특성을 지정할 수 있습니다 (예: `capture`, `once`).

## 예제
### 기본 사용 예
```javascript
// HTML 요소 선택
const button = document.querySelector('button');

// 클릭 이벤트 리스너 추가
button.addEventListener('click', function() {
    alert('버튼이 클릭되었습니다!');
});

// 클릭 이벤트 리스너 제거
function handleClick() {
    alert('버튼이 클릭되었습니다!');
}
button.addEventListener('click', handleClick);
button.removeEventListener('click', handleClick);
```

### 이벤트 전파 예
```javascript
const parentDiv = document.querySelector('#parent');
const childDiv = document.querySelector('#child');

// 부모 요소에 클릭 이벤트 리스너 추가
parentDiv.addEventListener('click', function() {
    alert('부모 요소 클릭!');
});

// 자식 요소에 클릭 이벤트 리스너 추가
childDiv.addEventListener('click', function(event) {
    alert('자식 요소 클릭!');
    // 이벤트 전파 중지
    event.stopPropagation();
});
```

## 설명
- **이벤트 전파**: 이벤트는 DOM 트리에서 상위 요소로 전파됩니다. 이를 통해 이벤트를 부모 요소에서도 처리할 수 있습니다. `stopPropagation()` 메서드를 사용하여 전파를 중지할 수 있습니다.
- **중복 리스너**: 같은 이벤트에 대해 동일한 리스너를 여러 번 추가하면, 각 호출에 대해 리스너가 중복되어 실행됩니다. `removeEventListener`를 사용하여 정확히 동일한 리스너를 제거해야 합니다.
- **옵션 사용**: `options` 매개변수를 사용하여 리스너의 동작 방식을 제어할 수 있습니다. 예를 들어, `once: true`를 설정하면 이벤트가 한 번만 호출됩니다.

## 한 줄 요약
`EventTarget`은 JavaScript에서 이벤트를 처리하고 전파하기 위한 기본 인터페이스로, 다양한 객체에서 이벤트 리스너를 추가하고 관리하는 데 사용됩니다.