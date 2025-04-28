<!--
Meta Description: # SVGAnimatedLength: 자바스크립트에서의 활용 ## 개요 `SVGAnimatedLength`는 SVG(Scalable Vector Graphics)에서 길이를 애니메이션으로 표현할 수 있도록 돕는 객체입니다. 이 객체는 SVG 요소의 속성값을 애니메이션 ...
Meta Keywords: width, svganimatedlength, animval, svg, 애니메이션
-->

# SVGAnimatedLength: 자바스크립트에서의 활용

## 개요
`SVGAnimatedLength`는 SVG(Scalable Vector Graphics)에서 길이를 애니메이션으로 표현할 수 있도록 돕는 객체입니다. 이 객체는 SVG 요소의 속성값을 애니메이션 할 때 유용하게 사용됩니다.

## 문서화
`SVGAnimatedLength`는 SVG 요소의 길이 속성을 애니메이션하기 위한 두 가지 속성을 제공합니다:
- `baseVal`: 속성의 기본 값.
- `animVal`: 현재 애니메이션 값.

### 목적
SVG 요소의 길이 속성을 동적으로 변경하고, 애니메이션 효과를 통해 시각적으로 매력적인 그래픽을 생성할 수 있습니다.

### 사용법
`SVGAnimatedLength`는 주로 SVG의 길이 속성에 사용됩니다. 예를 들어, `width`, `height`, `x`, `y`와 같은 속성에서 사용할 수 있습니다. JavaScript를 통해 이러한 속성에 접근하고 조작할 수 있습니다.

## 예제
다음은 `SVGAnimatedLength`를 사용하는 간단한 예입니다.

```html
<svg width="200" height="200">
  <rect id="myRect" width="100" height="100" fill="blue">
    <animate attributeName="width" from="100" to="200" dur="2s" fill="freeze" />
  </rect>
</svg>

<script>
  const rect = document.getElementById('myRect');
  
  // width 속성의 baseVal과 animVal 출력
  console.log(rect.width.baseVal.value); // 100
  console.log(rect.width.animVal.value); // 100 (애니메이션 시작 전)
</script>
```

위 예제에서, `rect` 요소의 `width` 속성이 애니메이션 동안 100에서 200으로 변경됩니다. JavaScript를 사용하여 `baseVal`과 `animVal`을 확인할 수 있습니다.

## 설명
`SVGAnimatedLength` 객체를 사용할 때 주의할 점은 애니메이션이 완료되기 전까지 `animVal`은 애니메이션의 현재 상태를 반영한다는 것입니다. 이로 인해 스크립트에서 `animVal`을 사용할 때, 애니메이션의 진행 상태에 따라 값이 달라질 수 있습니다.

또한, `baseVal`은 속성의 초기 값을 나타내므로, 다른 값을 설정하면 `animVal`이 애니메이션을 통해 변경되는 것을 확인할 수 있습니다. 애니메이션이 완료된 후에도 `baseVal`은 변경되지 않습니다.

## 요약
`SVGAnimatedLength`는 SVG의 길이 속성을 애니메이션할 수 있게 도와주는 JavaScript 객체로, 애니메이션 효과를 통해 동적이고 매력적인 그래픽을 생성하는 데 사용됩니다.