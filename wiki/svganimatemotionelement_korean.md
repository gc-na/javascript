<!--
Meta Description: # SVGAnimateMotionElement: 자바스크립트와 함께하는 SVG 애니메이션의 기초 ## 개요 `SVGAnimateMotionElement`는 SVG(Scalable Vector Graphics)에서 객체를 특정 경로를 따라 애니메이션할 수 있도록 해주는 ...
Meta Keywords: svg, svganimatemotionelement, path, animatemotion, 200
-->

# SVGAnimateMotionElement: 자바스크립트와 함께하는 SVG 애니메이션의 기초

## 개요
`SVGAnimateMotionElement`는 SVG(Scalable Vector Graphics)에서 객체를 특정 경로를 따라 애니메이션할 수 있도록 해주는 요소입니다. 자바스크립트를 사용하여 SVG 애니메이션을 제어하고 동적으로 생성하는 데 유용합니다.

## 문서화
### 목적
`SVGAnimateMotionElement`는 SVG 내부의 그래픽 요소가 정의된 경로를 따라 이동하도록 하는 데 사용됩니다. 이 기능은 복잡한 애니메이션 효과를 만들기 위해 필수적이며, SVG의 강력한 시각적 표현력을 최대한 활용할 수 있게 합니다.

### 사용법
`SVGAnimateMotionElement`는 `<animateMotion>` 태그를 사용하여 SVG 마크업 내에서 정의됩니다. 이 태그는 다음과 같은 주요 속성을 포함합니다:

- `path`: 애니메이션이 진행될 경로를 정의합니다.
- `dur`: 애니메이션의 지속 시간을 설정합니다.
- `repeatCount`: 애니메이션 반복 횟수를 설정합니다. "indefinite"로 설정하면 무한 반복됩니다.

예제:
```xml
<svg width="200" height="200">
  <circle cx="50" cy="50" r="20" fill="blue">
    <animateMotion dur="2s" repeatCount="indefinite">
      <mpath href="#motionPath" />
    </animateMotion>
  </circle>
  <path id="motionPath" d="M 10 80 Q 95 10 180 80 T 350 80" fill="transparent" stroke="red"/>
</svg>
```

### 세부사항
`SVGAnimateMotionElement`는 웹 표준으로 정의되어 있으며, 다양한 브라우저에서 지원됩니다. SVG의 애니메이션은 CSS 애니메이션이나 JavaScript 애니메이션과 함께 사용할 수 있으며, SVG의 특성으로 인해 벡터 그래픽에 최적화된 성능을 제공합니다.

## 예제
다음은 `SVGAnimateMotionElement`를 활용한 간단한 예시입니다.

### 예제 1: 원이 경로를 따라 이동하기
```xml
<svg width="400" height="200">
  <circle cx="20" cy="100" r="10" fill="green">
    <animateMotion dur="4s" repeatCount="indefinite">
      <mpath href="#path" />
    </animateMotion>
  </circle>
  <path id="path" d="M 20 100 Q 200 0 380 100 T 740 100" fill="transparent" stroke="black"/>
</svg>
```

### 예제 2: 텍스트가 경로를 따라 이동하기
```xml
<svg width="500" height="200">
  <text x="0" y="20" fill="black">
    Hello World!
    <animateMotion dur="5s" repeatCount="indefinite">
      <mpath href="#path" />
    </animateMotion>
  </text>
  <path id="path" d="M 0 20 C 200 0, 200 40, 500 20" fill="transparent" stroke="red"/>
</svg>
```

## 설명
- **공통적인 문제점**: `SVGAnimateMotionElement`를 사용할 때, 애니메이션 경로가 유효하지 않으면 애니메이션이 작동하지 않습니다. 또한, SVG의 뷰포트가 잘못 설정되면 의도한 대로 표시되지 않을 수 있습니다.
- **브라우저 호환성**: 모든 주요 브라우저에서 지원되지만, 구형 브라우저에서는 제한적으로 동작할 수 있습니다. 항상 최신 브라우저에서 테스트하는 것이 좋습니다.
- **자바스크립트와의 통합**: 자바스크립트를 사용하여 애니메이션 속성을 동적으로 변경할 수 있으며, 이벤트 리스너를 추가하여 사용자 상호작용에 반응하게 만들 수 있습니다.

## 한 줄 요약
`SVGAnimateMotionElement`는 SVG 그래픽 요소가 정의된 경로를 따라 부드럽게 애니메이션되도록 하는 기능입니다.