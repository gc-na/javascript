<!--
Meta Description: # SVGFEDiffuseLightingElement: JavaScript에서의 사용 ## 개요 SVGFEDiffuseLightingElement는 SVG(Scalable Vector Graphics)에서 조명 효과를 생성하는 요소로, JavaScript를 통해 SVG...
Meta Keywords: filter, diffuselighting, svg, 있습니다, setattribute
-->

# SVGFEDiffuseLightingElement: JavaScript에서의 사용

## 개요
SVGFEDiffuseLightingElement는 SVG(Scalable Vector Graphics)에서 조명 효과를 생성하는 요소로, JavaScript를 통해 SVG 그래픽에 다양한 조명 효과를 적용할 수 있습니다. 이 요소는 주로 조명 효과를 적용하여 그래픽의 깊이와 질감을 강조하는 데 사용됩니다.

## 문서화
### 목적
SVGFEDiffuseLightingElement는 SVG 필터의 일종으로, 주어진 표면에 대해 확산 조명을 모델링합니다. 이 요소는 조명 원의 위치와 표면의 노멀 벡터를 기반으로 하여 조명 효과를 계산합니다.

### 사용법
SVGFEDiffuseLightingElement는 `<filter>` 요소 내에서 사용되며, 다음과 같은 속성을 가집니다:

- `in`: 입력 이미지를 지정합니다.
- `surfaceScale`: 표면의 스케일을 정의합니다. 기본값은 1입니다.
- `diffuseConstant`: 확산 조명 강도를 조절합니다. 기본값은 1입니다.
- `kernelUnitLength`: 조명의 크기를 설정합니다.
- `lightingColor`: 조명의 색상을 설정합니다.

이 요소는 JavaScript를 통해 동적으로 생성하거나 수정할 수 있습니다.

### 예제
다음은 SVGFEDiffuseLightingElement를 사용하는 기본 예제입니다.

```html
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <filter id="diffuseLighting">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="5" diffuseConstant="1">
        <feDistantLight azimuth="45" elevation="55"/>
      </feDiffuseLighting>
    </filter>
  </defs>
  <rect x="10" y="10" width="180" height="180" fill="blue" filter="url(#diffuseLighting)"/>
</svg>
```

JavaScript를 사용하여 이 필터를 동적으로 생성할 수도 있습니다.

```javascript
const svgNS = "http://www.w3.org/2000/svg";
const filter = document.createElementNS(svgNS, 'filter');
filter.setAttribute('id', 'diffuseLighting');

const diffuseLighting = document.createElementNS(svgNS, 'feDiffuseLighting');
diffuseLighting.setAttribute('in', 'SourceGraphic');
diffuseLighting.setAttribute('surfaceScale', '5');
diffuseLighting.setAttribute('diffuseConstant', '1');

const distantLight = document.createElementNS(svgNS, 'feDistantLight');
distantLight.setAttribute('azimuth', '45');
distantLight.setAttribute('elevation', '55');

diffuseLighting.appendChild(distantLight);
filter.appendChild(diffuseLighting);
document.querySelector('defs').appendChild(filter);
```

## 설명
SVGFEDiffuseLightingElement를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **조명 방향**: `feDistantLight`의 `azimuth`와 `elevation` 속성은 조명의 방향을 결정합니다. 잘못된 값을 설정하면 원하지 않는 조명 효과가 발생할 수 있습니다.
- **입력 이미지**: `in` 속성을 통해 지정한 입력 이미지가 없으면 필터가 제대로 작동하지 않습니다.
- **표면 스케일**: `surfaceScale` 값이 클수록 조명 효과가 더 두드러지지만, 너무 큰 값은 과도한 효과를 초래할 수 있습니다.

## 한 문장 요약
SVGFEDiffuseLightingElement는 SVG 필터로, JavaScript를 통해 조명을 모델링하여 그래픽의 깊이와 질감을 향상시키는 데 사용됩니다.