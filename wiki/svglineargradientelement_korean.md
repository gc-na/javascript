<!--
Meta Description: # SVGLinearGradientElement: 자바스크립트에서의 사용법과 예제 ## 개요 `SVGLinearGradientElement`는 SVG(Scalable Vector Graphics)에서 선형 그라디언트를 정의하는 데 사용되는 요소입니다. 자바스크립트를 통...
Meta Keywords: lineargradient, stop, svg, setattribute, 255
-->

# SVGLinearGradientElement: 자바스크립트에서의 사용법과 예제

## 개요
`SVGLinearGradientElement`는 SVG(Scalable Vector Graphics)에서 선형 그라디언트를 정의하는 데 사용되는 요소입니다. 자바스크립트를 통해 SVG 요소를 동적으로 생성하고 수정할 때 이 요소를 활용할 수 있습니다.

## 문서화
`SVGLinearGradientElement`는 SVG의 `linearGradient` 요소를 나타내며, 주로 색상의 변화를 표현하기 위해 사용됩니다. 선형 그라디언트는 두 개 이상의 색상이 일정한 방향으로 부드럽게 변하도록 하여, 다양한 시각적 효과를 제공합니다. 

### 사용 목적
- SVG 그래픽에서 색상 변화를 구현
- 복잡한 시각적 효과를 간편하게 생성
- 자바스크립트를 통해 동적으로 그라디언트를 조작

### 사용법
`SVGLinearGradientElement`는 SVG 문서 내에서 `<linearGradient>` 태그로 정의됩니다. 자바스크립트 내에서 이 요소를 생성하고 수정할 수 있습니다.

### 주요 속성
- `x1`, `y1`: 그라디언트의 시작 점을 정의하는 속성
- `x2`, `y2`: 그라디언트의 끝 점을 정의하는 속성
- `gradientUnits`: 그라디언트의 좌표계 설정
- `spreadMethod`: 그라디언트의 확산 방법 설정

## 예제
### 기본 사용 예제
```html
<svg width="200" height="200">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="200" height="200" fill="url(#grad1)" />
</svg>
```

### 자바스크립트로 그라디언트 생성
```javascript
const svgNS = "http://www.w3.org/2000/svg";
const linearGradient = document.createElementNS(svgNS, "linearGradient");
linearGradient.setAttribute("id", "grad2");
linearGradient.setAttribute("x1", "0%");
linearGradient.setAttribute("y1", "100%");
linearGradient.setAttribute("x2", "100%");
linearGradient.setAttribute("y2", "0%");

const stop1 = document.createElementNS(svgNS, "stop");
stop1.setAttribute("offset", "0%");
stop1.setAttribute("style", "stop-color:rgb(0,255,255);stop-opacity:1");

const stop2 = document.createElementNS(svgNS, "stop");
stop2.setAttribute("offset", "100%");
stop2.setAttribute("style", "stop-color:rgb(0,0,255);stop-opacity:1");

linearGradient.appendChild(stop1);
linearGradient.appendChild(stop2);

document.querySelector("defs").appendChild(linearGradient);
```

## 설명
- **브라우저 호환성**: 모든 주요 브라우저에서 지원되지만, 특정 속성이나 기능에 대한 지원이 다를 수 있습니다. 항상 최신 브라우저에서 테스트하는 것이 좋습니다.
- **SVG 문서 구조**: `<linearGradient>` 요소는 `<defs>` 태그 내에 위치해야 하며, 사용 전 반드시 정의되어 있어야 합니다.
- **자바스크립트 조작**: 자바스크립트를 통해 동적으로 그라디언트를 생성하거나 수정할 수 있지만, DOM 조작 후 SVG를 렌더링하는 데 시간이 걸릴 수 있습니다.

## 한 줄 요약
`SVGLinearGradientElement`는 SVG 그래픽에서 선형 그라디언트를 정의하고 조작하는 데 사용되는 요소입니다.