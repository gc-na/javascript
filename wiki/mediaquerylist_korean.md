<!--
Meta Description: # MediaQueryList: JavaScript로 미디어 쿼리 관찰하기 ## 개요 `MediaQueryList`는 JavaScript에서 CSS 미디어 쿼리를 매칭하는 방법을 제공하는 인터페이스입니다. 이를 통해 웹 개발자는 특정 조건에 따라 스타일이나 스크립트를 ...
Meta Keywords: mediaquerylist, 미디어, 리스너를, 이벤트, 600px
-->

# MediaQueryList: JavaScript로 미디어 쿼리 관찰하기

## 개요
`MediaQueryList`는 JavaScript에서 CSS 미디어 쿼리를 매칭하는 방법을 제공하는 인터페이스입니다. 이를 통해 웹 개발자는 특정 조건에 따라 스타일이나 스크립트를 동적으로 조정할 수 있습니다.

## 문서
### 목적
`MediaQueryList`는 미디어 쿼리를 사용하여 문서의 현재 상태를 감지하고, 화면 크기나 장치 특성에 따라 다양한 반응형 디자인을 구현하는 데 도움을 줍니다.

### 사용법
`MediaQueryList` 객체는 `window.matchMedia()` 메서드를 통해 생성됩니다. 이 메서드는 주어진 미디어 쿼리가 현재 문서에 적용되는지 여부를 확인할 수 있는 `MediaQueryList` 객체를 반환합니다.

### 속성
- `matches`: 현재 문서가 미디어 쿼리와 일치하는지 여부를 나타내는 불리언 값입니다.
- `media`: 미디어 쿼리 문자열을 반환합니다.
- `addListener()`: 미디어 쿼리의 상태 변화에 대한 이벤트 리스너를 추가합니다.
- `removeListener()`: 추가한 이벤트 리스너를 제거합니다.

### 메서드
- `addEventListener()`: 미디어 쿼리의 변경 사항을 감지하기 위한 이벤트 리스너를 추가합니다. (최신 브라우저에서 사용)
- `removeEventListener()`: 추가한 이벤트 리스너를 제거합니다. (최신 브라우저에서 사용)

## 예제
```javascript
// 미디어 쿼리 정의
const mediaQueryList = window.matchMedia('(max-width: 600px)');

// 현재 상태 확인
if (mediaQueryList.matches) {
    console.log('화면 너비가 600px 이하입니다.');
} else {
    console.log('화면 너비가 600px 초과입니다.');
}

// 리스너 추가
const handleMediaChange = (event) => {
    if (event.matches) {
        console.log('화면 너비가 600px 이하입니다.');
    } else {
        console.log('화면 너비가 600px 초과입니다.');
    }
};

mediaQueryList.addEventListener('change', handleMediaChange);
```

## 설명
`MediaQueryList`를 사용할 때 주의할 점은 이벤트 리스너를 추가하고 제거하는 방법입니다. 이전에는 `addListener`와 `removeListener` 메서드를 사용했으나, 최신 브라우저에서는 `addEventListener`와 `removeEventListener`를 사용하는 것이 권장됩니다. 또한, 리스너를 추가할 때는 같은 함수 참조를 사용해야 하며, 다른 함수 참조를 사용하면 리스너를 제거할 수 없습니다.

## 한 줄 요약
`MediaQueryList`는 JavaScript에서 CSS 미디어 쿼리를 감지하고 반응형 디자인을 적용하기 위해 사용되는 인터페이스입니다.