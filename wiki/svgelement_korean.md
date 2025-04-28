<!--
Meta Description: # SVGElement: 자바스크립트에서의 SVG 요소 ## 개요 `SVGElement`는 JavaScript에서 Scalable Vector Graphics(SVG) 요소를 나타내는 인터페이스입니다. SVG는 XML 기반의 벡터 이미지 형식으로, 웹에서 그래픽을 표현...
Meta Keywords: svg, setattribute, svgelement, rect, document
-->

# SVGElement: 자바스크립트에서의 SVG 요소

## 개요
`SVGElement`는 JavaScript에서 Scalable Vector Graphics(SVG) 요소를 나타내는 인터페이스입니다. SVG는 XML 기반의 벡터 이미지 형식으로, 웹에서 그래픽을 표현할 때 자주 사용됩니다. `SVGElement`를 통해 개발자는 SVG 요소를 생성하고 수정하며 상호작용할 수 있습니다.

## 문서화
### 목적
`SVGElement`는 다양한 SVG 요소를 조작할 수 있는 메서드와 속성을 제공합니다. 이를 통해 개발자는 웹 애플리케이션 내에서 동적이고 인터랙티브한 그래픽을 생성할 수 있습니다.

### 사용법
JavaScript에서 `SVGElement`를 사용하기 위해서는 HTML 문서 내에 `<svg>` 요소가 포함되어 있어야 합니다. SVG 요소를 생성하려면 `document.createElementNS()` 메서드를 사용하여 XML 네임스페이스를 지정해야 합니다.

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const svgElement = document.createElementNS(svgNamespace, "svg");
const circleElement = document.createElementNS(svgNamespace, "circle");

circleElement.setAttribute("cx", "50");
circleElement.setAttribute("cy", "50");
circleElement.setAttribute("r", "40");
circleElement.setAttribute("fill", "red");

svgElement.appendChild(circleElement);
document.body.appendChild(svgElement);
```

### 세부사항
- `SVGElement` 인터페이스는 다양한 서브클래스를 포함하며, 각 서브클래스는 SVG 기본 요소(예: `<circle>`, `<rect>`, `<path>` 등)를 나타냅니다.
- SVG 요소는 HTML DOM과 유사하게 작동하지만, SVG 전용 속성과 메서드가 있습니다.
- CSS와 JavaScript를 통해 SVG 요소의 스타일과 애니메이션을 제어할 수 있습니다.

## 예제
### 기본 사용 예제

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNamespace, "svg");
svg.setAttribute("width", "200");
svg.setAttribute("height", "200");

const rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("x", "10");
rect.setAttribute("y", "10");
rect.setAttribute("width", "100");
rect.setAttribute("height", "100");
rect.setAttribute("fill", "blue");

svg.appendChild(rect);
document.body.appendChild(svg);
```

이 예제는 200x200 크기의 SVG 캔버스에 파란색 사각형을 추가합니다.

## 설명
### 일반적인 주의사항
- SVG 요소는 DOM 요소와 다르게 작동할 수 있으므로, 속성 이름이 대문자로 시작하는 경우가 있습니다(예: `getBBox()`).
- SVG 요소의 크기와 위치는 뷰포트(viewport)와 비례하므로, 해상도에 따라 다르게 보일 수 있습니다.
- 모든 브라우저가 SVG를 동일하게 렌더링하지 않을 수 있으므로, 호환성 테스트가 필요합니다.

## 한 문장 요약
`SVGElement`는 JavaScript에서 SVG 그래픽 요소를 생성하고 조작하기 위한 인터페이스입니다.