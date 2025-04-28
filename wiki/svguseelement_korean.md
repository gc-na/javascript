<!--
Meta Description: # SVGUseElement: JavaScript에서 SVG 재사용 요소 다루기 ## 개요 `SVGUseElement`는 SVG(Scalable Vector Graphics) 문서 내에서 그래픽 요소를 재사용할 수 있게 해주는 DOM 인터페이스입니다. JavaScrip...
Meta Keywords: svg, symbol, svguseelement, 요소를, href
-->

# SVGUseElement: JavaScript에서 SVG 재사용 요소 다루기

## 개요
`SVGUseElement`는 SVG(Scalable Vector Graphics) 문서 내에서 그래픽 요소를 재사용할 수 있게 해주는 DOM 인터페이스입니다. JavaScript를 통해 SVG 요소를 동적으로 조작할 수 있어, 개발자들이 SVG 리소스를 효율적으로 관리하고 활용할 수 있도록 도와줍니다.

## 문서화

### 목적
`SVGUseElement`는 SVG 문서에서 정의된 그래픽 요소를 반복적으로 사용할 수 있게 하여, 코드의 재사용성과 유지보수성을 높입니다. 이 요소는 `<use>` 태그를 통해 구현되며, 다른 SVG 요소를 참조하여 DOM에 삽입합니다.

### 사용법
`SVGUseElement`는 `<use>` 태그 내에서 `href` 속성을 통해 참조할 SVG 요소의 ID를 지정합니다. JavaScript를 이용하여 이 요소를 생성하거나 조작할 수 있으며, 이를 통해 SVG 그래픽을 동적으로 변경하거나 애니메이션할 수 있습니다.

#### 기본 문법
```html
<svg>
  <symbol id="icon-star" viewBox="0 0 24 24">
    <path d="M12 2l3.09 6.26L22 9.27l-5 4.87L18.18 22 12 18.77 5.82 22 7 14.14l-5-4.87 6.91-1.01z"/>
  </symbol>
  <use href="#icon-star" x="0" y="0" width="24" height="24"/>
</svg>
```

### 세부 사항
- **속성**: `href`, `x`, `y`, `width`, `height`
- **메서드**: `getBBox()`, `getCTM()`, `getScreenCTM()`, `setAttribute()`
- **이벤트**: SVG 요소와 동일한 이벤트 처리 가능

## 예제

### 예제 1: 기본 SVG 아이콘 사용
```html
<svg width="100" height="100">
  <symbol id="icon-heart" viewBox="0 0 24 24">
    <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c2.54 0 4.5 1.92 4.5 1.92S13.96 3 16.5 3C19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
  </symbol>
  <use href="#icon-heart" x="10" y="10" width="50" height="50"/>
</svg>
```

### 예제 2: JavaScript로 SVG 변경
```html
<svg id="mySVG" width="100" height="100">
  <symbol id="icon-circle" viewBox="0 0 24 24">
    <circle cx="12" cy="12" r="10"/>
  </symbol>
  <use href="#icon-circle" x="10" y="10" width="30" height="30" id="circleUse"/>
</svg>

<script>
  const circleUse = document.getElementById('circleUse');
  circleUse.setAttribute('fill', 'blue'); // 동적으로 색상 변경
</script>
```

## 설명
`SVGUseElement`를 사용할 때 주의할 점은 `href` 속성의 값이 정확하게 참조하고자 하는 요소의 ID와 일치해야 한다는 것입니다. 또한, `<symbol>` 요소 내의 경로 데이터는 사용하기 전에 올바르게 정의되어야 합니다. 브라우저 호환성 문제로 인해 일부 오래된 브라우저에서는 SVG 기능이 제한될 수도 있습니다.

## 한 줄 요약
`SVGUseElement`는 SVG 그래픽 요소를 효율적으로 재사용하고 JavaScript를 통해 동적으로 조작할 수 있도록 지원하는 DOM 인터페이스입니다.