<!--
Meta Description: # SVGSVGElement: JavaScript에서 SVG 요소를 다루기 위한 인터페이스 ## 개요 `SVGSVGElement`는 SVG(Scalable Vector Graphics) 문서의 최상위 요소를 나타내는 JavaScript 인터페이스입니다. 이 인터페이스는...
Meta Keywords: svg, svgelement, setattribute, document, 요소를
-->

# SVGSVGElement: JavaScript에서 SVG 요소를 다루기 위한 인터페이스

## 개요
`SVGSVGElement`는 SVG(Scalable Vector Graphics) 문서의 최상위 요소를 나타내는 JavaScript 인터페이스입니다. 이 인터페이스는 SVG 그래픽을 생성하고 조작하기 위한 중요한 기능을 제공합니다.

## 문서화
`SVGSVGElement`는 SVG 문서에서 `<svg>` 요소를 나타내며, SVG 그래픽의 컨테이너 역할을 합니다. 이 요소는 SVG의 뷰포트 크기와 비율을 정의하고, 다양한 SVG 요소들(예: `<circle>`, `<rect>`, `<path>`)을 포함할 수 있습니다.

### 용도
- SVG 문서의 기본 구조를 정의합니다.
- SVG 요소의 속성과 메서드에 접근할 수 있는 기반을 제공합니다.
- DOM 메서드를 통해 SVG 요소를 동적으로 조작할 수 있습니다.

### 사용법
`SVGSVGElement`는 JavaScript에서 SVG 요소를 생성하고 조작할 때 사용됩니다. 일반적으로 `document.createElementNS` 메서드를 사용하여 이 요소를 생성합니다.

```javascript
let svgNamespace = "http://www.w3.org/2000/svg";
let svgElement = document.createElementNS(svgNamespace, "svg");
svgElement.setAttribute("width", "100");
svgElement.setAttribute("height", "100");
document.body.appendChild(svgElement);
```

## 예제
### 기본 SVG 생성
```javascript
let svgNamespace = "http://www.w3.org/2000/svg";
let svgElement = document.createElementNS(svgNamespace, "svg");
svgElement.setAttribute("width", "200");
svgElement.setAttribute("height", "200");

let circle = document.createElementNS(svgNamespace, "circle");
circle.setAttribute("cx", "100");
circle.setAttribute("cy", "100");
circle.setAttribute("r", "50");
circle.setAttribute("fill", "red");

svgElement.appendChild(circle);
document.body.appendChild(svgElement);
```

### SVG에 텍스트 추가
```javascript
let svgNamespace = "http://www.w3.org/2000/svg";
let svgElement = document.createElementNS(svgNamespace, "svg");
svgElement.setAttribute("width", "200");
svgElement.setAttribute("height", "200");

let text = document.createElementNS(svgNamespace, "text");
text.setAttribute("x", "10");
text.setAttribute("y", "20");
text.textContent = "안녕하세요, SVG!";

svgElement.appendChild(text);
document.body.appendChild(svgElement);
```

## 설명
`SVGSVGElement`를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:
- SVG 요소를 생성할 때는 항상 `document.createElementNS`를 사용해야 하며, 일반적인 `document.createElement`는 SVG 요소를 생성할 수 없습니다.
- SVG의 속성은 CSS와 HTML 속성과 다르게 다루어질 수 있으며, 이를 이해하고 있어야 합니다.
- SVG 내의 좌표 시스템은 기본적으로 왼쪽 상단 모서리를 원점(0, 0)으로 사용하므로, 좌표 설정 시 주의가 필요합니다.

## 한 줄 요약
`SVGSVGElement`는 JavaScript에서 SVG 문서의 최상위 요소를 생성하고 조작하기 위한 중요한 인터페이스입니다.