<!--
Meta Description: # SVGFEMorphologyElement: JavaScript에서 SVG 형태 변형 요소 사용하기 ## 개요 `SVGFEMorphologyElement`는 SVG(Scalable Vector Graphics)에서 형태 변형을 수행하는 필터 요소를 정의하는 인터페이스...
Meta Keywords: svg, svgfemorphologyelement, filter, 그래픽의, operator
-->

# SVGFEMorphologyElement: JavaScript에서 SVG 형태 변형 요소 사용하기

## 개요
`SVGFEMorphologyElement`는 SVG(Scalable Vector Graphics)에서 형태 변형을 수행하는 필터 요소를 정의하는 인터페이스입니다. JavaScript를 사용하여 이 요소를 조작함으로써 그래픽의 외관을 변화시킬 수 있습니다.

## 문서화
### 목적
`SVGFEMorphologyElement`는 SVG 그래픽의 형태를 변경하는 데 사용됩니다. 주로 두 가지 속성(`operator`와 `radius`)을 통해 그래픽의 모양을 확장하거나 축소하여 시각 효과를 만들어냅니다.

### 사용법
`SVGFEMorphologyElement`는 SVG 필터의 일부로 사용되며, 다음과 같은 속성을 가집니다:
- **operator**: 형태 변형 방법을 지정합니다. `erode` 또는 `dilate`의 두 가지 옵션이 있습니다.
- **radius**: 변형의 강도를 설정합니다. 이 값은 x와 y 방향으로의 반경을 정의합니다.

JavaScript를 사용하여 이 요소를 생성하고 조작할 수 있습니다. 예를 들어, SVG 필터를 정의하고 필터를 그래픽에 적용하는 방식으로 사용됩니다.

### 예제
```javascript
// SVG 필터 요소 생성
const svgNamespace = "http://www.w3.org/2000/svg";
const filter = document.createElementNS(svgNamespace, "filter");
filter.setAttribute("id", "myFilter");

// SVGFEMorphologyElement 생성
const morphology = document.createElementNS(svgNamespace, "feMorphology");
morphology.setAttribute("operator", "dilate");
morphology.setAttribute("radius", "5 5");

// 필터에 형태 변형 요소 추가
filter.appendChild(morphology);
document.querySelector("svg defs").appendChild(filter);

// SVG 그래픽에 필터 적용
const rect = document.querySelector("rect");
rect.setAttribute("filter", "url(#myFilter)");
```

### 설명
`SVGFEMorphologyElement`를 사용할 때 주의해야 할 사항은 다음과 같습니다:
- **속성 값의 유효성**: `operator`와 `radius` 속성이 올바르게 설정되어야 합니다. 잘못된 값은 원하는 효과를 생성하지 않습니다.
- **SVG 환경**: 이 요소는 SVG 문서 내에서만 의미가 있으며, HTML 요소와는 다르게 작동합니다.
- **브라우저 호환성**: 일부 브라우저에서는 SVG 필터의 지원이 제한적일 수 있으므로, 이를 고려하여 코드를 작성해야 합니다.

## 한 줄 요약
`SVGFEMorphologyElement`는 JavaScript를 통해 SVG 그래픽의 형태를 변형하는 필터 요소입니다.