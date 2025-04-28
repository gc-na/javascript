<!--
Meta Description: # SVGCircleElement: JavaScript에서 SVG 원 요소를 다루는 방법 ## 개요 `SVGCircleElement`는 SVG(Scalable Vector Graphics)에서 원을 정의하는 요소를 나타내며, JavaScript를 사용하여 이 요소를 생...
Meta Keywords: circle, svg, svgcircleelement, setattribute, document
-->

# SVGCircleElement: JavaScript에서 SVG 원 요소를 다루는 방법

## 개요
`SVGCircleElement`는 SVG(Scalable Vector Graphics)에서 원을 정의하는 요소를 나타내며, JavaScript를 사용하여 이 요소를 생성하고 조작할 수 있습니다. 이 요소는 SVG 그래픽에서 원을 그리기 위한 기본 구성 요소로 사용됩니다.

## 문서화
`SVGCircleElement`는 SVG 문서 내에서 원을 정의하는 데 사용되는 객체입니다. 이 객체는 `circle` 태그로 생성되며, 다양한 속성을 통해 원의 위치와 크기를 조정할 수 있습니다.

### 주요 속성
- `cx`: 원의 중심 x 좌표
- `cy`: 원의 중심 y 좌표
- `r`: 원의 반지름
- `fill`: 원의 채우기 색상
- `stroke`: 원의 테두리 색상
- `stroke-width`: 테두리 두께

### 사용법
JavaScript를 통해 `SVGCircleElement`를 생성하고 조작할 수 있습니다. 일반적으로 `document.createElementNS` 메서드를 사용하여 SVG 네임스페이스 내에서 `circle` 요소를 생성합니다.

```javascript
const svgNS = "http://www.w3.org/2000/svg"; // SVG 네임스페이스
const circle = document.createElementNS(svgNS, "circle");

// 속성 설정
circle.setAttribute("cx", 50);
circle.setAttribute("cy", 50);
circle.setAttribute("r", 40);
circle.setAttribute("fill", "red");

// SVG 요소에 추가
const svgContainer = document.getElementById("svgContainer");
svgContainer.appendChild(circle);
```

## 예제
기본적인 `SVGCircleElement` 사용 예제는 다음과 같습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SVGCircleElement 예제</title>
</head>
<body>
    <svg id="svgContainer" width="200" height="200"></svg>
    <script>
        const svgNS = "http://www.w3.org/2000/svg";
        const circle = document.createElementNS(svgNS, "circle");
        circle.setAttribute("cx", 100);
        circle.setAttribute("cy", 100);
        circle.setAttribute("r", 50);
        circle.setAttribute("fill", "blue");
        document.getElementById("svgContainer").appendChild(circle);
    </script>
</body>
</html>
```

## 설명
`SVGCircleElement`를 사용할 때 주의할 점:
- SVG 요소는 반드시 SVG 네임스페이스에서 생성되어야 합니다. 그렇지 않으면 올바르게 렌더링되지 않습니다.
- 원의 속성은 숫자형으로 지정해야 하며, 잘못된 형식의 값은 무시됩니다.
- `fill` 및 `stroke` 속성에 사용할 수 있는 색상 값은 다양한 형식이 있으며, CSS 색상 규칙을 따릅니다.

## 한줄 요약
`SVGCircleElement`는 JavaScript를 사용하여 SVG 내에서 원을 생성하고 조작하는 데 사용되는 객체입니다.