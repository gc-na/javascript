<!--
Meta Description: # JavaScript DOMRectList: DOMRectList 객체에 대한 완벽 가이드 ## 개요 `DOMRectList`는 JavaScript에서 DOM 요소의 크기와 위치를 나타내는 `DOMRect` 객체의 리스트를 제공하는 인터페이스입니다. 이 객체는 주로 ...
Meta Keywords: domrectlist, domrect, 요소의, getclientrects, rect
-->

# JavaScript DOMRectList: DOMRectList 객체에 대한 완벽 가이드

## 개요
`DOMRectList`는 JavaScript에서 DOM 요소의 크기와 위치를 나타내는 `DOMRect` 객체의 리스트를 제공하는 인터페이스입니다. 이 객체는 주로 `getClientRects()` 메서드와 함께 사용되며, HTML 요소의 여러 사각형 정보를 손쉽게 다룰 수 있도록 돕습니다.

## 문서화

### 목적
`DOMRectList`는 여러 개의 `DOMRect` 객체를 포함하고 있으며, 각 객체는 특정 DOM 요소의 크기(너비, 높이)와 위치(좌표)를 나타냅니다. 이를 통해 개발자는 요소의 시각적 배치 및 크기를 보다 쉽게 관리할 수 있습니다.

### 사용법
`DOMRectList` 객체는 `getClientRects()` 메서드를 통해 생성됩니다. 이 메서드는 특정 요소에 대한 모든 클라이언트 사각형의 리스트를 반환합니다.

### 속성
- **length**: `DOMRect` 객체의 개수를 반환합니다.
- **item(index)**: 주어진 인덱스에 해당하는 `DOMRect` 객체를 반환합니다.

### 메서드
- **forEach(callback)**: 각 `DOMRect` 객체에 대해 주어진 콜백 함수를 실행합니다.

## 예제

### 기본 사용 예제
```javascript
// 특정 요소 선택
const element = document.getElementById('myElement');

// DOMRectList 가져오기
const rects = element.getClientRects();

// DOMRectList의 각 DOMRect 객체 출력
rects.forEach(rect => {
    console.log(`위치: (${rect.left}, ${rect.top}), 크기: ${rect.width}x${rect.height}`);
});
```

### DOMRectList의 길이 확인
```javascript
const element = document.getElementById('myElement');
const rects = element.getClientRects();

console.log(`DOMRectList의 길이: ${rects.length}`);
```

## 설명
`DOMRectList`를 사용할 때 주의해야 할 점은 `getClientRects()` 메서드가 반환하는 `DOMRectList`가 항상 비어있지 않다는 것입니다. 요소가 화면에 렌더링되지 않거나, 오프스크린 상태일 경우 빈 리스트를 반환할 수 있습니다. 또한, 다양한 CSS 속성이나 변형에 따라 여러 개의 사각형이 생성될 수 있으며, 이 경우 `DOMRectList`의 길이는 1보다 클 수 있습니다.

이 외에도 `DOMRectList`는 배열과 유사한 형태이지만, 완벽하게 배열은 아닙니다. 따라서 `map`, `filter`와 같은 배열 메서드를 사용하려면 변환이 필요합니다.

## 한 줄 요약
`DOMRectList`는 JavaScript에서 DOM 요소의 여러 사각형 정보를 손쉽게 관리하는 객체입니다.