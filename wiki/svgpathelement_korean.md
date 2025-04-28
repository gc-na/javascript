<!--
Meta Description: # JavaScript에서 SVGPathElement 사용하기 ## 개요 `SVGPathElement`는 SVG(Scalable Vector Graphics)에서 경로를 정의하고 조작하기 위해 사용되는 DOM 요소입니다. 이 요소는 복잡한 형태의 그래픽을 생성할 수 있...
Meta Keywords: svg, svgpathelement, document, pathelement, path
-->

# JavaScript에서 SVGPathElement 사용하기

## 개요
`SVGPathElement`는 SVG(Scalable Vector Graphics)에서 경로를 정의하고 조작하기 위해 사용되는 DOM 요소입니다. 이 요소는 복잡한 형태의 그래픽을 생성할 수 있게 해주며, JavaScript와 함께 사용하여 동적으로 SVG 경로를 수정하거나 애니메이션을 추가할 수 있습니다.

## 문서화
### 목적
`SVGPathElement`는 SVG 이미지 내에서 경로를 정의하는 데 사용됩니다. 이 요소는 다양한 도형을 그릴 수 있는 명령어 집합을 포함하고 있으며, 스타일과 애니메이션을 CSS와 JavaScript로 조작할 수 있습니다.

### 사용법
`SVGPathElement`는 HTML 문서 내에서 SVG 태그를 통해 사용됩니다. JavaScript에서 이 요소를 생성하고 수정하기 위해 `document.createElementNS` 메서드를 사용합니다. 기본적인 사용법은 다음과 같습니다:

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const pathElement = document.createElementNS(svgNamespace, "path");
pathElement.setAttribute("d", "M 10 10 H 90 V 90 H 10 L 10 10");
pathElement.setAttribute("fill", "none");
pathElement.setAttribute("stroke", "black");
document.querySelector("svg").appendChild(pathElement);
```

### 세부사항
- `d` 속성: 경로의 데이터를 정의하는 문자열로, M (move to), L (line to), H (horizontal line to), V (vertical line to) 등의 명령어를 포함합니다.
- `fill` 속성: 경로 내부의 색상을 정의합니다.
- `stroke` 속성: 경로의 외곽선 색상을 정의합니다.
- `SVGPathElement`는 `getTotalLength()`, `getPointAtLength()`와 같은 메서드를 제공하여 경로의 길이와 특정 위치의 점을 가져올 수 있습니다.

## 예제
다음은 `SVGPathElement`를 사용하여 간단한 사각형을 그리는 예제입니다:

```html
<svg width="100" height="100">
    <path id="myPath" d="M 10 10 H 90 V 90 H 10 Z" fill="blue" />
</svg>

<script>
    const path = document.getElementById("myPath");
    path.setAttribute("stroke", "red");
    path.setAttribute("stroke-width", "2");
</script>
```

## 설명
`SVGPathElement`를 사용할 때 주의해야 할 점은 경로의 `d` 속성에 사용되는 명령어의 구문입니다. 잘못된 명령어를 사용하면 경로가 의도한 대로 그려지지 않을 수 있습니다. 또한, SVG 요소를 DOM에 추가할 때는 반드시 `createElementNS`를 사용해야 합니다. 일반적인 `document.createElement`는 SVG 요소를 생성하는 데 적합하지 않습니다.

## 한 줄 요약
`SVGPathElement`는 JavaScript에서 SVG 경로를 정의하고 조작할 수 있도록 해주는 핵심 요소입니다.