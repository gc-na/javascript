<!--
Meta Description: # SVGLineElement: JavaScript에서 SVG 선 요소 다루기 ## 개요 `SVGLineElement`는 SVG(Scalable Vector Graphics)에서 선을 생성하고 조작하기 위한 JavaScript 객체입니다. 이 객체는 SVG 문서 내에서...
Meta Keywords: svg, line, svglineelement, stroke, setattribute
-->

# SVGLineElement: JavaScript에서 SVG 선 요소 다루기

## 개요
`SVGLineElement`는 SVG(Scalable Vector Graphics)에서 선을 생성하고 조작하기 위한 JavaScript 객체입니다. 이 객체는 SVG 문서 내에서 선을 정의하고, 스타일링하며, 동적으로 수정할 수 있는 다양한 속성과 메서드를 제공합니다.

## 문서화

### 목적
`SVGLineElement`는 SVG 문서에서 선을 표현하는 기본 요소입니다. 이 요소는 두 개의 점(시작점과 끝점)을 연결하여 직선을 생성합니다. 웹 애플리케이션에서 그래픽을 표시할 때 유용하게 사용됩니다.

### 사용법
`SVGLineElement`를 사용하려면 먼저 SVG 문서 내에 `line` 요소를 생성해야 합니다. JavaScript를 통해 이 요소를 생성하고 조작할 수 있습니다.

#### 속성
- `x1`: 시작점의 x좌표.
- `y1`: 시작점의 y좌표.
- `x2`: 끝점의 x좌표.
- `y2`: 끝점의 y좌표.
- `stroke`: 선의 색상.
- `stroke-width`: 선의 두께.

### 예제
다음은 JavaScript를 사용하여 SVG 선 요소를 생성하고 추가하는 기본적인 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>SVGLineElement 예제</title>
</head>
<body>
    <svg width="500" height="500" style="border: 1px solid black;">
        <!-- 선 요소는 여기에 추가됩니다 -->
    </svg>

    <script>
        // SVG 요소 선택
        const svg = document.querySelector('svg');

        // 새로운 선 요소 생성
        const line = document.createElementNS('http://www.w3.org/2000/svg', 'line');
        line.setAttribute('x1', 50);
        line.setAttribute('y1', 50);
        line.setAttribute('x2', 200);
        line.setAttribute('y2', 200);
        line.setAttribute('stroke', 'blue');
        line.setAttribute('stroke-width', 2);

        // SVG에 선 요소 추가
        svg.appendChild(line);
    </script>
</body>
</html>
```

### 설명
- **좌표 설정**: 선의 시작점과 끝점을 설정할 때, 좌표 값이 SVG의 뷰포트 내에서 올바르게 지정되어야 합니다. 잘못된 좌표를 사용하면 선이 화면에 나타나지 않을 수 있습니다.
- **스타일링**: `stroke`와 `stroke-width` 속성으로 선의 색상과 두께를 조정할 수 있습니다. CSS로도 스타일을 지정할 수 있지만, SVG 속성을 통해 직접 설정하면 더 간편합니다.
- **동적 수정**: JavaScript를 이용해 선의 속성을 동적으로 변경할 수 있습니다. 예를 들어 마우스 이벤트에 따라 선의 색상을 변경하는 등의 인터랙티브한 기능을 구현할 수 있습니다.

## 한 줄 요약
`SVGLineElement`는 JavaScript를 사용하여 SVG에서 선을 생성하고 조작하는데 유용한 요소입니다.