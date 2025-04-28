<!--
Meta Description: # SVGFilterElement: JavaScript에서 SVG 필터 요소 활용하기 ## 개요 SVGFilterElement는 Scalable Vector Graphics(SVG)에서 필터를 정의하는 데 사용되는 요소로, JavaScript와 함께 사용하여 다양한 시...
Meta Keywords: svg, filter, fegaussianblur, defs, const
-->

# SVGFilterElement: JavaScript에서 SVG 필터 요소 활용하기

## 개요
SVGFilterElement는 Scalable Vector Graphics(SVG)에서 필터를 정의하는 데 사용되는 요소로, JavaScript와 함께 사용하여 다양한 시각적 효과를 창출할 수 있습니다. 이 요소는 특히 그래픽 디자인 및 웹 개발에 있어 이미지 처리 및 효과 적용에 유용합니다.

## 문서화
### 목적
SVGFilterElement는 SVG 이미지에 다양한 필터 효과를 적용하기 위해 사용됩니다. 이러한 필터는 그래픽을 변형하거나, 색상을 조정하거나, 이미지에 블러 효과를 주는 등 다양한 시각적 효과를 추가하는 데 유용합니다.

### 사용법
SVGFilterElement는 `<filter>` 태그를 사용하여 정의됩니다. JavaScript를 통해 동적으로 필터를 생성하거나 수정할 수 있습니다. 기본적인 사용법은 다음과 같습니다:

```html
<svg width="200" height="200">
  <defs>
    <filter id="f1" x="0" y="0">
      <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="blue" filter="url(#f1)" />
</svg>
```

JavaScript를 사용하여 필터를 동적으로 추가하는 방법은 다음과 같습니다:

```javascript
const svgNS = "http://www.w3.org/2000/svg";
const filter = document.createElementNS(svgNS, 'filter');
filter.setAttribute("id", "dynamicFilter");
const feGaussianBlur = document.createElementNS(svgNS, 'feGaussianBlur');
feGaussianBlur.setAttribute("in", "SourceGraphic");
feGaussianBlur.setAttribute("stdDeviation", "5");
filter.appendChild(feGaussianBlur);
document.querySelector('svg defs').appendChild(filter);
```

## 예제
1. **기본 블러 필터 적용하기**
   ```html
   <svg width="200" height="200">
     <defs>
       <filter id="blur">
         <feGaussianBlur stdDeviation="5" />
       </filter>
     </defs>
     <circle cx="100" cy="100" r="80" fill="red" filter="url(#blur)" />
   </svg>
   ```

2. **JavaScript로 필터 동적 생성하기**
   ```javascript
   const svg = document.querySelector('svg');
   const newFilter = document.createElementNS(svgNS, 'filter');
   newFilter.setAttribute('id', 'newBlur');
   const blurEffect = document.createElementNS(svgNS, 'feGaussianBlur');
   blurEffect.setAttribute('stdDeviation', '10');
   newFilter.appendChild(blurEffect);
   svg.querySelector('defs').appendChild(newFilter);
   ```

## 설명
- **일관성 있는 네임스페이스**: SVG 요소는 XML 기반이므로, JavaScript로 SVG 요소를 생성할 때는 항상 적절한 네임스페이스(`http://www.w3.org/2000/svg`)를 사용해야 합니다.
- **필터 ID 중복 방지**: 여러 필터를 사용할 경우, ID가 중복되지 않도록 유의해야 하며, 각 필터의 사용 범위를 명확히 할 필요가 있습니다.
- **브라우저 호환성**: 일부 브라우저에서는 특정 SVG 필터 효과가 다르게 렌더링될 수 있으므로, 다양한 브라우저에서 테스트하는 것이 중요합니다.

## 한 문장 요약
SVGFilterElement는 JavaScript를 사용하여 SVG 그래픽에 필터 효과를 추가하는 강력한 도구입니다.