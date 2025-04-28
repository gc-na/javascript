<!--
Meta Description: # DOMRect: 자바스크립트에서의 DOMRect 객체에 대한 완벽 가이드 ## 개요 DOMRect 객체는 HTML 요소의 크기와 위치 정보를 제공하는 자바스크립트 API입니다. 주로 `getBoundingClientRect()` 메서드와 함께 사용되며, 요소의 경계...
Meta Keywords: rect, 요소의, 사각형의, getboundingclientrect, domrect
-->

# DOMRect: 자바스크립트에서의 DOMRect 객체에 대한 완벽 가이드

## 개요
DOMRect 객체는 HTML 요소의 크기와 위치 정보를 제공하는 자바스크립트 API입니다. 주로 `getBoundingClientRect()` 메서드와 함께 사용되며, 요소의 경계 사각형을 정의하는 데 유용합니다.

## 문서화

### 목적
DOMRect 객체는 웹 페이지에서 요소의 위치와 크기를 수치적으로 표현하는 데 사용됩니다. 이 객체는 요소의 좌표, 너비, 높이 등을 쉽게 접근할 수 있도록 해줍니다.

### 사용법
DOMRect는 주로 `getBoundingClientRect()` 메서드의 결과로 생성됩니다. 이 메서드는 요소의 크기와 뷰포트에 대한 위치 정보를 포함하는 DOMRect 객체를 반환합니다.

**형식:**
```javascript
let rect = element.getBoundingClientRect();
```

### 속성
DOMRect 객체는 다음과 같은 주요 속성을 갖습니다:
- `x`: 사각형의 왼쪽 가장자리의 x 좌표.
- `y`: 사각형의 위쪽 가장자리의 y 좌표.
- `width`: 사각형의 너비.
- `height`: 사각형의 높이.
- `top`: 사각형의 위쪽 가장자리의 y 좌표.
- `right`: 사각형의 오른쪽 가장자리의 x 좌표.
- `bottom`: 사각형의 아래쪽 가장자리의 y 좌표.
- `left`: 사각형의 왼쪽 가장자리의 x 좌표.

## 예제

### 기본 사용법
다음은 DOMRect를 사용하는 기본적인 예제입니다:

```javascript
// 특정 요소 선택
const element = document.querySelector('#myElement');

// 요소의 경계 사각형 정보 가져오기
const rect = element.getBoundingClientRect();

// 경계 사각형 정보 출력
console.log(`Width: ${rect.width}, Height: ${rect.height}`);
console.log(`Top: ${rect.top}, Left: ${rect.left}`);
```

### 화면 크기 변화에 따른 업데이트
화면 크기가 변경될 때 DOMRect를 업데이트하는 예제입니다:

```javascript
window.addEventListener('resize', () => {
    const element = document.querySelector('#myElement');
    const rect = element.getBoundingClientRect();
    console.log(`Updated Width: ${rect.width}, Updated Height: ${rect.height}`);
});
```

## 설명

### 일반적인 오류 및 주의사항
- **변경되지 않는 값**: DOMRect는 요소의 크기나 위치가 변경되면 업데이트되지 않습니다. 항상 `getBoundingClientRect()`를 호출하여 최신 정보를 가져와야 합니다.
- **CSS 변환 효과**: CSS 변환(예: `transform`)이 적용된 요소에 대해 `getBoundingClientRect()`가 반환하는 값은 변환된 후의 위치와 크기를 반영합니다.
- **스크롤 위치**: 반환된 좌표는 뷰포트 기준으로 계산되기 때문에, 요소가 스크롤된 경우 좌표 값이 다를 수 있습니다.

## 한 줄 요약
DOMRect는 자바스크립트를 통해 HTML 요소의 크기와 위치 정보를 쉽게 얻을 수 있게 해주는 API입니다.