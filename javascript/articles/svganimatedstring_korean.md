<!--
Meta Description: # SVGAnimatedString: JavaScript에서의 SVG 애니메이션 문자열 처리 ## 개요 `SVGAnimatedString`은 SVG(Scalable Vector Graphics) 요소에서 문자열을 애니메이션할 수 있도록 하는 특수한 타입입니다. 이 타입...
Meta Keywords: svganimatedstring, svg, 애니메이션, 문자열, 애니메이션이
-->

# SVGAnimatedString: JavaScript에서의 SVG 애니메이션 문자열 처리

## 개요
`SVGAnimatedString`은 SVG(Scalable Vector Graphics) 요소에서 문자열을 애니메이션할 수 있도록 하는 특수한 타입입니다. 이 타입은 정적인 문자열과 애니메이션 중인 문자열을 모두 지원하여, SVG 그래픽의 동적 효과를 생성하는 데 유용합니다.

## 문서화
### 목적
`SVGAnimatedString`은 SVG 요소의 속성을 애니메이션 처리하기 위해 사용됩니다. 이 객체는 두 개의 문자열 속성을 포함하고 있으며, 하나는 현재 값(currentValue)이고, 다른 하나는 애니메이션의 목표 값(animations)입니다. 애니메이션이 진행되는 동안 두 문자열 중 하나를 참조할 수 있습니다.

### 사용법
`SVGAnimatedString` 객체는 SVG 요소의 속성에 의해 자동으로 생성되며, JavaScript를 통해 직접 만들 수는 없습니다. 예를 들어, `<animate>` 요소를 사용하여 애니메이션을 정의할 때, 해당 속성은 `SVGAnimatedString` 타입으로 반환됩니다.

#### 속성
- **baseVal**: 정적인 기본 문자열 값을 나타냅니다.
- **animVal**: 현재 애니메이션 값으로, 애니메이션이 진행되는 동안 변경됩니다.

### 예제
다음은 `SVGAnimatedString`을 사용하는 기본적인 예제입니다.

```html
<svg width="200" height="200">
  <rect id="myRect" width="100" height="100" fill="blue">
    <animate attributeName="fill" from="blue" to="red" dur="2s" begin="0s" fill="freeze" />
  </rect>
</svg>

<script>
  const rect = document.getElementById('myRect');
  const animatedFill = rect.getAttribute('fill');

  console.log('기본 값:', animatedFill.baseVal); // "blue"
  console.log('애니메이션 값:', animatedFill.animVal); // 애니메이션이 진행 중일 경우 "red"
</script>
```

### 설명
- `SVGAnimatedString`을 사용할 때 주의해야 할 점은 애니메이션이 완료되기 전에 `animVal`을 참조할 경우, 예상과 다른 값이 나올 수 있다는 것입니다. 애니메이션의 상태에 따라 `animVal`의 값이 동적으로 변경되기 때문입니다.
- 또한, `baseVal`은 항상 정적인 값이므로, 애니메이션이 완료된 후에도 해당 값은 변하지 않습니다.

## 한 줄 요약
`SVGAnimatedString`은 SVG 요소에서 문자열 애니메이션을 처리하기 위한 객체로, 현재 값과 애니메이션 값을 모두 관리합니다.