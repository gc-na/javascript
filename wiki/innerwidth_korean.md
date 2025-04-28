<!--
Meta Description: # JavaScript innerWidth: 브라우저 뷰포트의 너비를 측정하는 방법 ## 개요 `innerWidth`는 현재 창의 뷰포트 너비를 픽셀 단위로 반환하는 JavaScript 프로퍼티입니다. 이 값은 스크롤 바를 포함한 현재 브라우저 창의 콘텐츠 영역 너비를...
Meta Keywords: innerwidth, 너비를, 브라우저, javascript, 뷰포트
-->

# JavaScript innerWidth: 브라우저 뷰포트의 너비를 측정하는 방법

## 개요
`innerWidth`는 현재 창의 뷰포트 너비를 픽셀 단위로 반환하는 JavaScript 프로퍼티입니다. 이 값은 스크롤 바를 포함한 현재 브라우저 창의 콘텐츠 영역 너비를 측정하는 데 사용됩니다.

## 문서화

### 목적
`innerWidth` 프로퍼티는 웹 페이지에서 현재 뷰포트의 너비를 쉽게 확인할 수 있도록 해줍니다. 반응형 웹 디자인을 구현할 때 매우 유용하며, 화면 크기에 따라 콘텐츠를 조정하는 데 사용됩니다.

### 사용법
`innerWidth`는 `window` 객체의 프로퍼티로 사용됩니다. 다음과 같이 호출할 수 있습니다:

```javascript
let viewportWidth = window.innerWidth;
```

이 코드는 현재 브라우저 창의 내부 너비를 변수 `viewportWidth`에 저장합니다.

### 세부사항
- **타입**: `innerWidth`는 정수 값을 반환하며, 픽셀 단위로 측정됩니다.
- **읽기 전용**: 이 프로퍼티는 읽기 전용이며, 직접 수정할 수 없습니다.
- **반응형 디자인**: CSS 미디어 쿼리와 함께 사용할 때, 뷰포트 너비에 따라 다른 스타일을 적용할 수 있습니다.

## 예제

### 기본 사용 예제

```javascript
// 뷰포트 너비를 콘솔에 출력
console.log("현재 뷰포트 너비:", window.innerWidth);
```

### 반응형 디자인 적용 예제

```javascript
function adjustLayout() {
    if (window.innerWidth < 600) {
        // 작은 화면에 대한 스타일 적용
        document.body.style.backgroundColor = "lightblue";
    } else {
        // 큰 화면에 대한 스타일 적용
        document.body.style.backgroundColor = "lightgreen";
    }
}

// 윈도우 크기 변경 시 레이아웃 조정
window.onresize = adjustLayout;
adjustLayout(); // 초기 호출
```

## 설명
`innerWidth`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **스크롤 바 포함**: `innerWidth`는 스크롤 바를 포함한 너비를 반환합니다. 따라서 스크롤 바가 있는 경우 실제 콘텐츠 영역 너비는 `innerWidth`보다 작을 수 있습니다.
- **브라우저 호환성**: 대부분의 현대 브라우저에서 지원되지만, 구형 브라우저에서는 올바르게 작동하지 않을 수 있습니다. 이 점을 고려하여 코드 작성 시 브라우저 호환성을 체크해야 합니다.
- **반응형 이벤트**: 뷰포트 크기가 변경될 때 `onresize` 이벤트를 사용하여 레이아웃을 조정하는 것이 중요합니다. 이 이벤트는 브라우저 창 크기가 변경될 때마다 호출됩니다.

## 한 줄 요약
`innerWidth`는 JavaScript에서 현재 브라우저 뷰포트의 너비를 픽셀 단위로 반환하는 프로퍼티입니다.