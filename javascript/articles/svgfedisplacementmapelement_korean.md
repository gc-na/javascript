<!--
Meta Description: # SVGFEDisplacementMapElement: JavaScript에서의 사용법과 예제 ## 개요 `SVGFEDisplacementMapElement`는 SVG 필터 효과 중 하나로, 이미지를 변형하여 왜곡된 효과를 생성하는 데 사용됩니다. JavaScript와...
Meta Keywords: svg, svgfedisplacementmapelement, 200, 이미지를, displacementfilter
-->

# SVGFEDisplacementMapElement: JavaScript에서의 사용법과 예제

## 개요
`SVGFEDisplacementMapElement`는 SVG 필터 효과 중 하나로, 이미지를 변형하여 왜곡된 효과를 생성하는 데 사용됩니다. JavaScript와 함께 사용할 수 있어 동적인 SVG 그래픽스를 구현하는 데 유용합니다.

## 문서화
`SVGFEDisplacementMapElement`는 SVG 필터의 일부로, 주로 필터 효과를 통해 이미지의 특정 부분을 변형시키는 데 활용됩니다. 이 요소는 두 개의 입력 이미지를 받아들이고, 하나의 이미지를 다른 이미지의 픽셀에 따라 변형합니다. 이 기능은 주로 그래픽 디자인, 웹 애플리케이션 개발 및 애니메이션 제작에 사용됩니다.

### 목적
- 이미지를 왜곡하여 창의적인 시각적 효과를 제공
- 동적인 SVG 필터 적용을 통해 사용자 인터랙션 향상

### 사용법
`SVGFEDisplacementMapElement`는 SVG 문서 내에서 `<filter>` 태그의 자식 요소로 정의됩니다. JavaScript를 사용하여 필터를 동적으로 조작할 수 있습니다.

### 주요 속성
- `in`: 입력 이미지의 ID를 지정합니다.
- `in2`: 변형에 사용될 두 번째 입력 이미지의 ID를 지정합니다.
- `scale`: 변형의 크기를 설정합니다.
- `xChannelSelector`: X 방향으로 사용할 색상 채널을 지정합니다.
- `yChannelSelector`: Y 방향으로 사용할 색상 채널을 지정합니다.

## 예제
아래는 `SVGFEDisplacementMapElement`를 사용한 기본적인 예제입니다.

```html
<svg width="200" height="200">
  <defs>
    <filter id="displacementFilter">
      <feDisplacementMap in="SourceGraphic" in2="displacementMap" scale="20" />
    </filter>
    <image id="displacementMap" href="map.png" width="200" height="200" />
  </defs>
  <image href="source.png" width="200" height="200" filter="url(#displacementFilter)" />
</svg>
```

### JavaScript를 통한 동적 조작 예제

```javascript
const displacementFilter = document.getElementById('displacementFilter');
displacementFilter.setAttribute('scale', '30'); // scale 속성 동적 변경
```

## 설명
`SVGFEDisplacementMapElement`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **입력 이미지와 변형 맵**: `in`과 `in2` 속성에 지정된 이미지가 올바르게 로드되어 있어야 합니다. 그렇지 않으면 필터가 작동하지 않습니다.
- **성능**: 복잡한 필터 효과는 렌더링 성능에 영향을 줄 수 있으므로, 최적화가 필요할 수 있습니다.
- **브라우저 호환성**: 모든 브라우저에서 일관되게 지원되지 않을 수 있으므로, 호환성을 확인해야 합니다.

## 한 줄 요약
`SVGFEDisplacementMapElement`는 SVG 필터를 통해 이미지를 왜곡하고 변형하는 데 사용되는 요소로, JavaScript와 함께 동적으로 조작할 수 있습니다.