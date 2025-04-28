<!--
Meta Description: # getComputedStyle: 자바스크립트에서 CSS 스타일을 가져오는 방법 ## 개요 `getComputedStyle`은 자바스크립트에서 HTML 요소의 최종 계산된 CSS 스타일을 가져오는 메서드입니다. 이 메서드는 요소가 실제로 어떻게 렌더링되는지를 확인할 ...
Meta Keywords: getcomputedstyle, element, 스타일을, css, 요소의
-->

# getComputedStyle: 자바스크립트에서 CSS 스타일을 가져오는 방법

## 개요
`getComputedStyle`은 자바스크립트에서 HTML 요소의 최종 계산된 CSS 스타일을 가져오는 메서드입니다. 이 메서드는 요소가 실제로 어떻게 렌더링되는지를 확인할 수 있도록 도와주며, 동적 스타일 조정이나 반응형 디자인 구현에 유용합니다.

## 문서화

### 목적
`getComputedStyle` 메서드는 특정 요소의 CSS 속성을 읽기 위해 사용됩니다. 이 메서드는 CSS 스타일 시트와 인라인 스타일을 모두 포함한 최종 스타일을 반환합니다.

### 사용법
`getComputedStyle` 메서드는 다음과 같이 사용할 수 있습니다:

```javascript
const element = document.querySelector('selector'); // 선택한 요소
const computedStyle = window.getComputedStyle(element); // 계산된 스타일 가져오기
```

### 세부 사항
- **매개변수**: `getComputedStyle` 메서드는 두 개의 매개변수를 가질 수 있습니다.
  - `element`: 스타일을 가져올 HTML 요소입니다.
  - `pseudoElement` (선택사항): 스타일을 가져올 가상 요소(예: `::before`, `::after`)입니다. 기본값은 `null`입니다.
- **반환 값**: 이 메서드는 `CSSStyleDeclaration` 객체를 반환하며, 이 객체를 통해 스타일 속성을 읽을 수 있습니다.
- **지원 브라우저**: `getComputedStyle` 메서드는 대부분의 현대 브라우저에서 지원됩니다. 구형 브라우저에서는 동작이 다를 수 있으므로 주의가 필요합니다.

## 예시
### 기본 사용 예
```javascript
const element = document.querySelector('.my-element');
const style = window.getComputedStyle(element);
console.log(style.color); // 요소의 텍스트 색상 출력
```

### 가상 요소의 스타일 가져오기
```javascript
const element = document.querySelector('.my-element');
const style = window.getComputedStyle(element, '::after');
console.log(style.content); // 가상 요소의 내용 출력
```

## 설명
`getComputedStyle`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

1. **렌더링 시점**: `getComputedStyle`는 요소가 DOM에 추가된 후에 호출해야 합니다. 그렇지 않으면 `null` 또는 예상치 못한 값을 반환할 수 있습니다.
2. **퍼포먼스**: 자주 호출할 경우 성능에 영향을 미칠 수 있으므로, 필요한 경우에만 호출하는 것이 좋습니다.
3. **CSS 속성 대소문자**: JavaScript에서 CSS 속성은 하이픈 대신 카멜 케이스로 변환되어야 합니다. 예를 들어, `background-color`는 `backgroundColor`로 사용해야 합니다.
4. **가상 요소**: 가상 요소의 스타일을 가져올 때는 반드시 두 번째 매개변수를 지정해야 합니다.

## 한 줄 요약
`getComputedStyle`은 자바스크립트에서 HTML 요소의 최종 계산된 CSS 스타일을 가져오는 메서드입니다.