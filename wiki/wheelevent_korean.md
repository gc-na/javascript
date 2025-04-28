<!--
Meta Description: # JavaScript의 WheelEvent: 마우스 휠 이벤트 처리 ## 개요 `WheelEvent`는 JavaScript에서 마우스 휠 또는 터치패드의 스크롤 동작을 감지하기 위한 이벤트 객체입니다. 이 이벤트는 사용자 인터페이스에서 스크롤, 확대/축소, 또는 기타...
Meta Keywords: wheelevent, 스크롤, 이벤트, 마우스, wheel
-->

# JavaScript의 WheelEvent: 마우스 휠 이벤트 처리

## 개요
`WheelEvent`는 JavaScript에서 마우스 휠 또는 터치패드의 스크롤 동작을 감지하기 위한 이벤트 객체입니다. 이 이벤트는 사용자 인터페이스에서 스크롤, 확대/축소, 또는 기타 입력 처리를 구현할 때 유용합니다.

## 문서화

### 목적
`WheelEvent`는 사용자가 마우스 휠을 돌리거나 터치패드에서 스크롤 제스처를 수행할 때 발생합니다. 이 이벤트는 `scroll`, `zoom`, 또는 다른 사용자 상호작용을 처리하기 위해 중요합니다.

### 사용법
`WheelEvent`는 `wheel` 이벤트로 발생하며, 이벤트 리스너를 통해 감지할 수 있습니다. 기본적으로 다음과 같은 속성을 포함합니다:

- `deltaX`: 수평 스크롤의 양.
- `deltaY`: 수직 스크롤의 양.
- `deltaZ`: 3D 스크롤의 양 (일반적으로 사용되지 않음).
- `deltaMode`: 스크롤의 단위 (픽셀, 라인, 페이지).

### 예제
다음은 `WheelEvent`를 사용하는 기본 예제입니다.

```javascript
// HTML 요소 선택
const element = document.getElementById('scrollable');

// wheel 이벤트 리스너 추가
element.addEventListener('wheel', (event) => {
    console.log(`X 방향 스크롤: ${event.deltaX}`);
    console.log(`Y 방향 스크롤: ${event.deltaY}`);
    event.preventDefault(); // 기본 스크롤 동작 방지
});
```

위 코드에서는 특정 HTML 요소에 `wheel` 이벤트 리스너를 추가하여 마우스 휠로 스크롤할 때마다 X 및 Y 방향의 스크롤 양을 콘솔에 출력합니다.

## 설명
`WheelEvent`를 사용할 때의 일반적인 주의사항은 다음과 같습니다:

- **기본 동작 방지**: 기본적으로 `wheel` 이벤트는 페이지의 스크롤을 유발합니다. 이를 방지하기 위해 `event.preventDefault()`를 호출해야 합니다.
- **브라우저 호환성**: 다양한 브라우저에서 `WheelEvent`의 동작이 다를 수 있으므로, 테스트가 필요합니다.
- **성능 고려사항**: 많은 양의 데이터를 처리하거나 애니메이션을 동반할 경우, 성능 저하를 방지하기 위해 `throttle` 또는 `debounce` 기법을 사용하는 것이 좋습니다.

## 한 줄 요약
`WheelEvent`는 JavaScript에서 마우스 휠 및 터치패드 스크롤 동작을 처리하기 위한 이벤트 객체입니다.