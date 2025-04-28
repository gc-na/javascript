<!--
Meta Description: # SVGAnimatedPreserveAspectRatio: 자바스크립트에서의 SVG 비율 유지 애니메이션 ## 개요 `SVGAnimatedPreserveAspectRatio`는 SVG(Scalable Vector Graphics)에서 비율 유지 속성을 애니메이션할 수...
Meta Keywords: 비율을, preserveaspectratio, 맞추어, 유지합니다, svg
-->

# SVGAnimatedPreserveAspectRatio: 자바스크립트에서의 SVG 비율 유지 애니메이션

## 개요
`SVGAnimatedPreserveAspectRatio`는 SVG(Scalable Vector Graphics)에서 비율 유지 속성을 애니메이션할 수 있도록 도와주는 객체입니다. 이 객체는 SVG 요소의 비율을 조정하여 화면 크기에 맞게 그래픽을 적절히 표시할 수 있게 합니다. 자바스크립트와 함께 사용하여 동적인 비율 유지 효과를 구현할 수 있습니다.

## 문서
`SVGAnimatedPreserveAspectRatio`는 `preserveAspectRatio` 속성을 애니메이션화하는 데 필요한 정보를 담고 있는 객체입니다. 이 속성은 SVG 요소가 어떻게 비율을 유지하면서 크기를 조정할지를 정의합니다. `preserveAspectRatio` 속성은 일반적으로 다음과 같은 값을 가질 수 있습니다:

- `none`: 비율을 유지하지 않고 요소를 늘리거나 줄입니다.
- `xMinYMin`: 좌상단에 맞추어 비율을 유지합니다.
- `xMidYMin`: 중앙 상단에 맞추어 비율을 유지합니다.
- `xMaxYMin`: 우상단에 맞추어 비율을 유지합니다.
- `xMinYMid`: 좌측 중앙에 맞추어 비율을 유지합니다.
- `xMidYMid`: 중앙에 맞추어 비율을 유지합니다.
- `xMaxYMid`: 우측 중앙에 맞추어 비율을 유지합니다.
- `xMinYMax`: 좌하단에 맞추어 비율을 유지합니다.
- `xMidYMax`: 중앙 하단에 맞추어 비율을 유지합니다.
- `xMaxYMax`: 우하단에 맞추어 비율을 유지합니다.

이 객체는 `baseVal`과 `animVal` 속성을 가지고 있으며, 각각 현재 값과 애니메이션된 값을 나타냅니다.

## 예제
다음은 `SVGAnimatedPreserveAspectRatio`를 사용하는 간단한 예제입니다.

```javascript
// SVG 요소 선택
const svgElement = document.getElementById('mySVG');

// preserveAspectRatio 속성 얻기
const preserveAspectRatio = svgElement.preserveAspectRatio;

// 현재 값 출력
console.log('현재 비율 유지 값:', preserveAspectRatio.baseVal);

// 비율 유지 값을 변경
preserveAspectRatio.baseVal = 'xMidYMid meet';
console.log('변경된 비율 유지 값:', preserveAspectRatio.baseVal);
```

## 설명
`SVGAnimatedPreserveAspectRatio`를 사용할 때 주의해야 할 점은 `preserveAspectRatio` 속성이 SVG 요소의 크기와 비율에 직접적인 영향을 미친다는 것입니다. 비율을 유지하는 방법을 적절히 설정하지 않으면 그래픽이 왜곡되거나 잘릴 수 있습니다. 또한, SVG 크기를 조정할 때 `baseVal`과 `animVal`의 차이를 이해하는 것이 중요합니다. `animVal`은 애니메이션이 진행되는 동안의 값을 나타내며, 자바스크립트에서 동적으로 애니메이션을 처리할 때 유용합니다.

## 한 줄 요약
`SVGAnimatedPreserveAspectRatio`는 SVG 그래픽의 비율 유지 속성을 애니메이션화하여 동적인 비율 조정을 가능하게 하는 자바스크립트 객체입니다.