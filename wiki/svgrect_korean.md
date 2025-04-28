<!--
Meta Description: # JavaScript의 SVGRect: SVG 사각형 요소 생성 및 조작 ## 개요 SVGRect는 SVG(Scalable Vector Graphics)에서 사각형을 정의하고 조작하는 데 사용되는 객체입니다. JavaScript와 함께 사용하여 동적으로 SVG 사각형...
Meta Keywords: svg, setattribute, 사각형의, rect, 요소를
-->

# JavaScript의 SVGRect: SVG 사각형 요소 생성 및 조작

## 개요
SVGRect는 SVG(Scalable Vector Graphics)에서 사각형을 정의하고 조작하는 데 사용되는 객체입니다. JavaScript와 함께 사용하여 동적으로 SVG 사각형을 생성하거나 수정할 수 있습니다.

## 문서화
### 목적
SVGRect는 SVG 내에서 사각형을 생성하고, 그 속성을 조정하여 시각적 요소를 동적으로 관리하는 데 활용됩니다. HTML 문서에 SVG 요소를 추가하고, JavaScript를 통해 이 사각형의 크기, 위치 및 스타일을 조정할 수 있습니다.

### 사용법
SVGRect는 일반적으로 아래와 같은 방식으로 사용됩니다:

1. **사각형 생성**: `document.createElementNS()` 메서드를 사용하여 SVG 사각형 요소를 생성합니다.
2. **속성 설정**: `setAttribute()` 메서드를 통해 사각형의 너비, 높이, 위치 등을 설정합니다.
3. **SVG에 추가**: 생성된 사각형 요소를 SVG 컨테이너에 추가합니다.

### 세부사항
- **이름공간**: SVG 요소는 XML 기반이므로, SVG 요소를 생성할 때는 XML 이름공간을 지정해야 합니다.
- **속성**:
  - `x`: 사각형의 왼쪽 상단 모서리의 X 좌표
  - `y`: 사각형의 왼쪽 상단 모서리의 Y 좌표
  - `width`: 사각형의 너비
  - `height`: 사각형의 높이
  - `fill`: 사각형의 채우기 색상

## 예제
### 기본 사용 예제
```javascript
// SVG 네임스페이스 정의
const svgNS = "http://www.w3.org/2000/svg";

// SVG 요소 생성
const svg = document.createElementNS(svgNS, "svg");
svg.setAttribute("width", 200);
svg.setAttribute("height", 200);
document.body.appendChild(svg);

// 사각형 요소 생성
const rect = document.createElementNS(svgNS, "rect");
rect.setAttribute("x", 10);
rect.setAttribute("y", 10);
rect.setAttribute("width", 100);
rect.setAttribute("height", 50);
rect.setAttribute("fill", "blue");

// 사각형을 SVG에 추가
svg.appendChild(rect);
```

## 설명
- **네임스페이스**: SVG 요소를 생성할 때는 항상 올바른 네임스페이스를 사용하는 것이 중요합니다. 그렇지 않으면 요소가 생성되지 않거나 브라우저에서 오류가 발생할 수 있습니다.
- **스타일 적용**: CSS를 사용하여 SVG 사각형의 스타일을 추가할 수 있지만, JavaScript에서 `setAttribute()`로 직접 속성을 설정하는 것이 더 직관적일 수 있습니다.
- **브라우저 호환성**: 대부분의 최신 브라우저는 SVG를 잘 지원하지만, 구형 브라우저에서는 SVG 기능이 제한적일 수 있습니다.

## 한 문장 요약
JavaScript의 SVGRect는 SVG 사각형 요소를 생성하고 조작하는 데 사용되는 객체로, 동적인 그래픽을 구현하는 데 유용합니다.