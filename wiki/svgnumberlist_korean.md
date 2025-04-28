<!--
Meta Description: # SVGNumberList: JavaScript에서 SVG 숫자 리스트 다루기 ## 개요 `SVGNumberList`는 SVG(SCALABLE VECTOR GRAPHICS)에서 숫자 값을 저장하고 관리하는 객체입니다. 이 객체는 JavaScript를 통해 SVG 속성...
Meta Keywords: svg, svgnumberlist, numberlist, 리스트를, 속성을
-->

# SVGNumberList: JavaScript에서 SVG 숫자 리스트 다루기

## 개요
`SVGNumberList`는 SVG(SCALABLE VECTOR GRAPHICS)에서 숫자 값을 저장하고 관리하는 객체입니다. 이 객체는 JavaScript를 통해 SVG 속성에서 숫자 리스트를 쉽게 조작할 수 있도록 돕습니다.

## 문서화
`SVGNumberList`는 여러 개의 숫자를 포함하는 리스트를 제공하여 SVG 그래픽에서 다양한 속성을 설정하는 데 사용됩니다. 이 객체는 주로 `SVGAnimatedNumberList`와 함께 사용되며, 애니메이션 효과 및 동적 변경이 가능합니다. 

### 목적
- SVG 요소의 숫자 속성을 동적으로 조작할 수 있도록 지원합니다.
- 다양한 SVG 속성(예: `stroke-dasharray`, `transform`)을 효과적으로 설정하고 변경할 수 있습니다.

### 사용법
`SVGNumberList`는 일반적으로 `getSVGNumberList()` 메서드를 통해 SVG 요소에서 생성됩니다. 이 메서드는 특정 SVG 속성에 대한 숫자 리스트를 반환합니다.

### 세부사항
- **속성**: `numberOfItems`, `appendItem()`, `removeItem()`, `clear()`, `initialize()`, `getItem()`, `replaceItem()`과 같은 메서드를 제공합니다.
- **호환성**: 모든 주요 웹 브라우저에서 지원되며, SVG를 사용하는 모든 프로젝트에서 활용 가능합니다.

## 예제
### 1. SVGNumberList 생성 및 사용
```javascript
// SVG 요소 선택
const svgElement = document.getElementById("mySVG");
const pathElement = svgElement.getElementById("myPath");

// SVGNumberList 가져오기
const numberList = pathElement.getTotalLength();

// 숫자 항목 추가
numberList.appendItem(10);
numberList.appendItem(20);

// 숫자 항목 출력
console.log(numberList.numberOfItems); // 2
console.log(numberList.getItem(0).value); // 10
```

### 2. 숫자 항목 제거
```javascript
// 첫 번째 항목 제거
numberList.removeItem(0);

// 남은 항목 출력
console.log(numberList.numberOfItems); // 1
```

## 설명
`SVGNumberList`를 사용할 때 주의할 점은 다음과 같습니다:
- **항목 인덱스**: 인덱스는 0부터 시작하므로, 잘못된 인덱스를 사용하면 `DOMException`이 발생할 수 있습니다.
- **브라우저 호환성**: 모든 브라우저에서 지원되지만, 구형 브라우저에서는 예외가 있을 수 있으므로, 항상 호환성을 확인하는 것이 중요합니다.
- **비어 있는 리스트**: 초기화되지 않은 `SVGNumberList`의 경우, 항목을 추가하기 전에 반드시 리스트가 비어 있음을 확인해야 합니다.

## 한 줄 요약
`SVGNumberList`는 JavaScript를 사용하여 SVG 요소의 숫자 속성을 동적으로 관리할 수 있는 객체입니다.