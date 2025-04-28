<!--
Meta Description: # SVGPolylineElement: 자바스크립트에서의 사용법과 예제 ## 개요 `SVGPolylineElement`는 Scalable Vector Graphics (SVG)에서 다각형의 선형 모양을 정의하는 요소입니다. JavaScript를 사용하여 이 요소를 조작...
Meta Keywords: svg, polyline, stroke, points, width
-->

# SVGPolylineElement: 자바스크립트에서의 사용법과 예제

## 개요
`SVGPolylineElement`는 Scalable Vector Graphics (SVG)에서 다각형의 선형 모양을 정의하는 요소입니다. JavaScript를 사용하여 이 요소를 조작함으로써 동적인 그래픽을 생성할 수 있습니다.

## 문서화
### 목적
`SVGPolylineElement`는 다수의 점으로 구성된 다각형을 정의하는 SVG 요소입니다. 이 요소는 여러 개의 좌표를 사용하여 선을 연결하고, 웹 페이지에서 벡터 기반의 그래픽을 표시하는 데 사용됩니다.

### 사용법
`SVGPolylineElement`는 `<polyline>` 태그를 통해 생성됩니다. 이 태그는 `points` 속성을 사용하여 다각형의 각 꼭지점의 좌표를 지정합니다. JavaScript를 통해 이 요소를 동적으로 생성하고 수정할 수 있습니다.

#### 기본 구문
```html
<svg width="200" height="200">
  <polyline points="50,50 100,100 150,50" style="fill:none; stroke:black; stroke-width:2" />
</svg>
```

#### JavaScript를 통한 생성 및 조작
```javascript
// SVG 요소 생성
const svgNamespace = "http://www.w3.org/2000/svg";
const polyline = document.createElementNS(svgNamespace, "polyline");

// 속성 설정
polyline.setAttribute("points", "50,50 100,100 150,50");
polyline.setAttribute("style", "fill:none; stroke:black; stroke-width:2");

// SVG에 추가
document.querySelector("svg").appendChild(polyline);
```

## 예제
### 예제 1: 기본 다각형 그리기
```html
<svg width="300" height="300">
  <polyline points="50,150 100,50 150,150 200,50" style="fill:none; stroke:red; stroke-width:3" />
</svg>
```

### 예제 2: JavaScript로 동적으로 추가하기
```html
<svg width="300" height="300" id="mySvg">
</svg>

<script>
  const svgNamespace = "http://www.w3.org/2000/svg";
  const polyline = document.createElementNS(svgNamespace, "polyline");
  
  polyline.setAttribute("points", "30,30 60,60 90,30");
  polyline.setAttribute("style", "fill:none; stroke:blue; stroke-width:2");
  
  document.getElementById("mySvg").appendChild(polyline);
</script>
```

## 설명
`SVGPolylineElement`를 사용할 때 주의할 점은 `points` 속성에 지정된 좌표의 형식입니다. 각 좌표는 쉼표로 구분되며, 점들은 공백으로 구분되어야 합니다. 잘못된 형식은 요소가 올바르게 렌더링되지 않게 할 수 있습니다. 또한, CSS 스타일을 통해 선의 색상, 두께 및 기타 속성을 조정할 수 있습니다.

### 흔한 실수
- `points` 속성의 좌표 형식 오류: 좌표가 올바르게 구분되어야 합니다.
- SVG namespace를 잊는 경우: JavaScript에서 SVG 요소를 생성할 때 반드시 적절한 namespace를 사용해야 합니다.

## 한 줄 요약
`SVGPolylineElement`는 JavaScript를 통해 다각형 선을 정의하고 조작하는 데 사용되는 SVG 요소입니다.