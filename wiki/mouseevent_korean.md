<!--
Meta Description: # JavaScript MouseEvent: 클릭 및 마우스 상호작용 처리하기 ## 개요 JavaScript의 `MouseEvent`는 사용자가 마우스를 클릭하거나 이동할 때 발생하는 이벤트를 다루기 위한 객체입니다. 이 객체는 마우스의 행동에 대한 정보를 제공하며, ...
Meta Keywords: 마우스, mouseevent, event, 이벤트, 있습니다
-->

# JavaScript MouseEvent: 클릭 및 마우스 상호작용 처리하기

## 개요
JavaScript의 `MouseEvent`는 사용자가 마우스를 클릭하거나 이동할 때 발생하는 이벤트를 다루기 위한 객체입니다. 이 객체는 마우스의 행동에 대한 정보를 제공하며, 웹 애플리케이션에서 사용자 인터랙션을 보다 풍부하게 구현할 수 있게 해줍니다.

## 문서화
### 목적
`MouseEvent`는 웹 페이지에서 발생하는 다양한 마우스 관련 이벤트를 처리하기 위한 목적으로 사용됩니다. 이러한 이벤트에는 클릭, 더블 클릭, 마우스 이동, 마우스 버튼 클릭 등이 포함됩니다.

### 사용법
`MouseEvent`는 이벤트 리스너 함수의 인자로 제공되며, 이를 통해 이벤트의 세부 정보를 확인하고 처리할 수 있습니다. 주로 `addEventListener()` 메서드를 사용하여 이벤트 리스너를 등록합니다.

### 세부 정보
- **생성**: `MouseEvent` 객체는 `new MouseEvent(type, options)` 형태로 생성할 수 있습니다. 여기서 `type`은 이벤트의 종류(예: 'click', 'mousemove'), `options`는 이벤트에 대한 추가 정보를 담은 객체입니다.
- **속성**:
  - `clientX`, `clientY`: 뷰포트 내에서의 마우스 커서 위치.
  - `button`: 클릭된 마우스 버튼의 인덱스(0: 왼쪽, 1: 가운데, 2: 오른쪽).
  - `ctrlKey`, `shiftKey`, `altKey`, `metaKey`: 이벤트 발생 시 눌린 수정 키의 상태.

## 예제
### 기본 사용 예제
```javascript
document.addEventListener('click', function(event) {
    console.log('클릭 좌표: ', event.clientX, event.clientY);
    console.log('누른 버튼: ', event.button);
});
```

### 마우스 이동 예제
```javascript
document.addEventListener('mousemove', function(event) {
    console.log('마우스 위치: ', event.clientX, event.clientY);
});
```

## 설명
`MouseEvent`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **이벤트 전파**: 기본적으로 마우스 이벤트는 버블링(bubbling) 방식으로 전파됩니다. 이를 제어하려면 `event.stopPropagation()` 메서드를 사용할 수 있습니다.
- **브라우저 호환성**: 다양한 브라우저에서 `MouseEvent`의 동작이 약간 다를 수 있습니다. 특히 구형 브라우저에서는 호환성 문제를 고려해야 합니다.
- **성능 문제**: `mousemove`와 같은 이벤트는 매우 자주 발생하므로, 성능 최적화를 위해 이벤트 디바운싱(debouncing) 기법을 사용하는 것이 좋습니다.

## 한줄 요약
JavaScript의 `MouseEvent`는 사용자의 마우스 클릭 및 이동과 관련된 이벤트 정보를 제공하여 웹 애플리케이션의 사용자 상호작용을 향상시키는 데 사용됩니다.