<!--
Meta Description: # JavaScript의 innerHeight: 브라우저 창 높이 측정하기 ## 요약 `innerHeight`는 JavaScript에서 현재 브라우저 창의 내부 높이를 픽셀 단위로 반환하는 속성입니다. 이 속성은 주로 웹 페이지의 레이아웃을 동적으로 조정하는 데 사용됩...
Meta Keywords: innerheight, 브라우저, 높이를, 있습니다, window
-->

# JavaScript의 innerHeight: 브라우저 창 높이 측정하기

## 요약
`innerHeight`는 JavaScript에서 현재 브라우저 창의 내부 높이를 픽셀 단위로 반환하는 속성입니다. 이 속성은 주로 웹 페이지의 레이아웃을 동적으로 조정하는 데 사용됩니다.

## 문서화
### 목적
`window.innerHeight`는 사용자가 현재 보고 있는 브라우저 창의 높이를 반환합니다. 이 값은 스크롤바의 높이를 제외한 부분만 포함되며, 주로 반응형 웹 디자인과 관련된 작업에서 유용하게 사용됩니다.

### 사용법
`innerHeight`는 `window` 객체의 속성으로 접근할 수 있습니다. 사용자는 다음과 같이 간단하게 현재 브라우저 창의 높이를 얻을 수 있습니다:

```javascript
const height = window.innerHeight;
console.log(height);
```

### 세부 사항
- **반환 값**: `innerHeight`는 `Number` 타입으로, 픽셀 단위로 브라우저 창의 내부 높이를 반환합니다.
- **동적 업데이트**: 브라우저 창의 크기가 변경되면 `innerHeight` 값도 자동으로 업데이트됩니다.
- **사용처**: 레이아웃 조정, 요소 표시/숨김, 반응형 디자인 구현 등에서 주로 사용됩니다.

## 예제
### 기본 사용 예제
```javascript
// 현재 브라우저 창의 높이를 출력합니다.
console.log("현재 브라우저 창의 높이:", window.innerHeight);
```

### 창 크기 변경 감지
```javascript
window.addEventListener('resize', () => {
    console.log("창의 새로운 높이:", window.innerHeight);
});
```

## 설명
`innerHeight`를 사용할 때 몇 가지 유의해야 할 점이 있습니다:
- **모바일 브라우저**: 모바일 디바이스에서 주소창이나 도구막대의 표시 여부에 따라 `innerHeight` 값이 달라질 수 있습니다. 이로 인해 레이아웃이 예상과 다르게 표시될 수 있습니다.
- **CSS와의 조화**: JavaScript로 측정한 높이를 CSS 스타일과 결합하여 사용할 때, CSS의 `vh` 단위를 함께 고려해야 할 수 있습니다.
- **DOM 업데이트**: DOM 요소가 동적으로 추가되거나 삭제될 경우, `innerHeight` 값을 다시 측정해야 할 수 있습니다.

## 한 줄 요약
`innerHeight`는 JavaScript에서 브라우저 창의 내부 높이를 픽셀 단위로 반환하는 속성입니다.