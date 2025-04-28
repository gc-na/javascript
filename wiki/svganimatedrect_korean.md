<!--
Meta Description: # SVGAnimatedRect: JavaScript와 함께하는 애니메이션 사각형 ## 개요 `SVGAnimatedRect`는 SVG(Scalable Vector Graphics)에서 애니메이션을 지원하는 사각형(rect) 요소를 나타내는 객체입니다. JavaScrip...
Meta Keywords: svg, 사각형의, rect, 위치를, svganimatedrect
-->

# SVGAnimatedRect: JavaScript와 함께하는 애니메이션 사각형

## 개요
`SVGAnimatedRect`는 SVG(Scalable Vector Graphics)에서 애니메이션을 지원하는 사각형(rect) 요소를 나타내는 객체입니다. JavaScript를 통해 SVG 애니메이션을 제어하고 조작할 수 있는 강력한 도구입니다.

## 문서화
### 목적
`SVGAnimatedRect`는 SVG 요소의 사각형을 애니메이션화하기 위해 사용됩니다. 이 객체는 사각형의 위치와 크기를 동적으로 변경할 수 있도록 지원합니다. 주요 속성은 `x`, `y`, `width`, `height`로 구성됩니다.

### 사용법
`SVGAnimatedRect`는 SVG 요소의 속성으로 사용되며, 각 속성은 `SVGAnimatedLength` 객체로 반환됩니다. 이를 통해 애니메이션을 적용할 수 있습니다. JavaScript를 사용하여 이러한 속성을 수정하면 애니메이션 효과를 만들 수 있습니다.

### 세부 사항
- `x`: 사각형의 x축 위치를 나타내는 `SVGAnimatedLength` 객체입니다.
- `y`: 사각형의 y축 위치를 나타내는 `SVGAnimatedLength` 객체입니다.
- `width`: 사각형의 너비를 나타내는 `SVGAnimatedLength` 객체입니다.
- `height`: 사각형의 높이를 나타내는 `SVGAnimatedLength` 객체입니다.

이러한 속성을 사용하여 애니메이션을 구현할 수 있으며, `begin`, `dur`, `end`와 같은 애니메이션 속성을 조절하여 다양한 효과를 만들 수 있습니다.

## 예제
### 기본 사용 예제
```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="100" height="100" fill="blue">
    <animate attributeName="x" from="10" to="150" dur="2s" fill="freeze" />
  </rect>
</svg>
```
위의 예제는 사각형의 x 위치를 10에서 150으로 2초 동안 애니메이션화합니다.

### JavaScript를 통한 제어 예제
```html
<svg width="200" height="200">
  <rect id="animatedRect" x="10" y="10" width="100" height="100" fill="red"></rect>
</svg>

<script>
  const rect = document.getElementById("animatedRect");
  rect.setAttribute("x", 50); // x 위치를 50으로 변경
  rect.setAttribute("y", 50); // y 위치를 50으로 변경
</script>
```
이 예제는 JavaScript를 사용하여 사각형의 위치를 변경합니다.

## 설명
`SVGAnimatedRect`를 사용할 때 주의해야 할 점은 애니메이션이 SVG 문서의 구조와 상호작용할 수 있다는 것입니다. 예를 들어, 사각형의 크기나 위치를 동적으로 변경하면 애니메이션의 흐름이 영향을 받을 수 있습니다. 또한, `fill` 속성이 `freeze`로 설정되면 애니메이션이 끝난 후 최종 상태를 유지합니다.

## 한 줄 요약
`SVGAnimatedRect`는 JavaScript를 통해 SVG 사각형의 애니메이션을 제어할 수 있는 객체입니다.