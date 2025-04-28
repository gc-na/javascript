<!--
Meta Description: # SVGSymbolElement: 자바스크립트에서의 사용법과 예제 ## 개요 `SVGSymbolElement`는 SVG(Scalable Vector Graphics)에서 심볼을 정의하고 재사용할 수 있도록 하는 요소입니다. JavaScript를 사용하여 동적으로 SV...
Meta Keywords: svg, svgsymbolelement, 있습니다, symbol, use
-->

# SVGSymbolElement: 자바스크립트에서의 사용법과 예제

## 개요
`SVGSymbolElement`는 SVG(Scalable Vector Graphics)에서 심볼을 정의하고 재사용할 수 있도록 하는 요소입니다. JavaScript를 사용하여 동적으로 SVG 심볼을 생성하고 조작할 수 있습니다.

## 문서화
`SVGSymbolElement`는 SVG 문서 내에서 심볼을 정의하는 데 사용되는 요소입니다. 이 요소는 `<symbol>` 태그로 정의되며, 각 심볼은 고유한 ID를 가질 수 있습니다. 심볼은 그래픽 요소를 재사용할 수 있게 해 주어 웹 페이지의 성능을 개선합니다.

### 사용 목적
- SVG 내에서 복잡한 그래픽을 간단하게 재사용할 수 있습니다.
- 다양한 위치에 여러 번 사용되는 그래픽 요소의 정의를 중앙 집중화합니다.

### 사용 방법
`SVGSymbolElement`를 사용하려면 다음과 같이 `<symbol>` 태그를 정의합니다:

```html
<svg>
  <symbol id="mySymbol" viewBox="0 0 100 100">
    <circle cx="50" cy="50" r="40" fill="blue" />
  </symbol>
</svg>
```

이후 JavaScript를 사용하여 이 심볼을 페이지의 다른 곳에서 참조할 수 있습니다:

```javascript
const svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
const use = document.createElementNS("http://www.w3.org/2000/svg", "use");
use.setAttribute("href", "#mySymbol");
svg.appendChild(use);
document.body.appendChild(svg);
```

## 예제
다음은 `SVGSymbolElement`를 사용하는 기본 예제입니다:

### 심볼 정의 및 사용
```html
<svg style="display:none;">
  <symbol id="icon-star" viewBox="0 0 24 24">
    <polygon points="12 17.27 18.18 21 16.54 13.97 22 9.24 14.81 8.63 12 2 9.19 8.63 2 9.24 7.46 13.97 5.82 21" fill="gold"/>
  </symbol>
</svg>

<svg width="100" height="100">
  <use href="#icon-star" x="0" y="0" />
</svg>
```

## 설명
`SVGSymbolElement`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **ID 중복**: 동일한 ID를 가진 심볼이 여러 개 존재할 수 없으므로, 각 심볼에 대해 고유한 ID를 부여해야 합니다.
- **뷰포트 설정**: `viewBox` 속성을 올바르게 설정하지 않으면 심볼이 올바르게 표시되지 않을 수 있습니다.
- **CSS 스타일링**: 심볼은 CSS로 스타일링할 수 있지만, 직접적인 스타일이 아닌 `use` 요소에 적용해야 합니다.

## 한 줄 요약
`SVGSymbolElement`는 SVG 그래픽에서 심볼을 정의하고 재사용하는 요소로, JavaScript로 동적으로 조작할 수 있습니다.