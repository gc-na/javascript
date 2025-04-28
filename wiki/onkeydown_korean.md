<!--
Meta Description: # JavaScript onkeydown 이벤트: 키보드 입력 처리의 기본 ## 개요 `onkeydown` 이벤트는 사용자가 키보드를 눌렀을 때 발생하는 이벤트로, 웹 애플리케이션에서 키보드 입력을 처리하는 데 사용됩니다. 이 이벤트는 사용자가 특정 키를 누를 때마다 ...
Meta Keywords: event, onkeydown, 이벤트는, 이벤트, 키보드
-->

# JavaScript onkeydown 이벤트: 키보드 입력 처리의 기본

## 개요
`onkeydown` 이벤트는 사용자가 키보드를 눌렀을 때 발생하는 이벤트로, 웹 애플리케이션에서 키보드 입력을 처리하는 데 사용됩니다. 이 이벤트는 사용자가 특정 키를 누를 때마다 실행할 수 있는 함수를 정의할 수 있게 해줍니다.

## 문서화
`onkeydown` 이벤트는 HTML 요소에 부착할 수 있으며, 키보드 키가 눌릴 때마다 호출됩니다. 이 이벤트는 일반적으로 사용자 입력을 처리하거나, 특정 키 조합에 대한 반응을 정의하는 데 유용합니다. 사용자는 이 이벤트를 통해 입력 필드, 버튼, 또는 다른 요소에 대한 키보드 상호작용을 제어할 수 있습니다.

### 사용법
`onkeydown` 이벤트는 HTML 요소에 직접 속성으로 추가하거나, JavaScript를 통해 이벤트 리스너로 등록할 수 있습니다. 

#### HTML 속성 사용 예:
```html
<input type="text" onkeydown="handleKeyDown(event)" />
```

#### JavaScript를 통한 이벤트 리스너 등록:
```javascript
const inputField = document.querySelector('input[type="text"]');
inputField.addEventListener('keydown', handleKeyDown);

function handleKeyDown(event) {
    console.log(event.key);
}
```

### 세부 사항
- **이벤트 객체**: `onkeydown` 이벤트가 발생하면 이벤트 객체가 생성되며, 이 객체를 통해 눌린 키에 대한 정보 (예: `event.key`, `event.code`)를 얻을 수 있습니다.
- **키 코드**: `event.key` 속성은 눌린 키의 값을 반환하며, `event.keyCode`는 과거에 사용되던 키 코드를 반환하지만, 현재는 비추천됩니다.
- **버블링 및 캡처링**: `onkeydown` 이벤트는 DOM 트리에서 버블링 방식으로 발생하며, 이벤트 리스너를 부모 요소에 추가하여 하위 요소의 키 입력을 처리할 수 있습니다.

## 예제
### 기본 사용 예
```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        console.log('Enter 키가 눌렸습니다.');
    }
});
```

### 여러 키 조합 처리
```javascript
document.addEventListener('keydown', function(event) {
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault(); // 기본 동작 방지
        console.log('Ctrl + S가 눌렸습니다.');
    }
});
```

## 설명
- **키 누름 이벤트 중복 처리**: `onkeydown` 이벤트는 키가 눌린 상태에서 여러 번 발생할 수 있으므로, 필요한 경우 `event.preventDefault()`를 사용하여 기본 동작을 방지할 수 있습니다.
- **비추천된 `event.keyCode`**: `event.keyCode`는 비추천된 속성으로, 가능한 한 `event.key`를 사용하는 것이 좋습니다. 최신 브라우저에서는 `event.key`가 더 일관된 결과를 제공합니다.
- **모바일 장치**: 모바일 장치에서는 키보드 입력 이벤트가 다르게 처리될 수 있으므로, 키보드 이벤트를 테스트할 때 다양한 환경에서 확인하는 것이 중요합니다.

## 요약
`onkeydown` 이벤트는 키보드 입력을 처리하는 데 유용한 JavaScript 이벤트로, 사용자 상호작용을 보다 풍부하게 만들어줍니다.