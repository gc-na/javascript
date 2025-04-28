<!--
Meta Description: # SVGImageElement: JavaScript에서 SVG 이미지 요소 다루기 ## 개요 `SVGImageElement`는 SVG(Scalable Vector Graphics) 내에서 이미지를 표현하기 위해 사용되는 DOM 요소입니다. JavaScript와 함께 ...
Meta Keywords: svg, 이미지의, svgimageelement, image, 이미지를
-->

# SVGImageElement: JavaScript에서 SVG 이미지 요소 다루기

## 개요
`SVGImageElement`는 SVG(Scalable Vector Graphics) 내에서 이미지를 표현하기 위해 사용되는 DOM 요소입니다. JavaScript와 함께 사용하면 SVG 이미지의 속성을 동적으로 조작할 수 있어 웹 애플리케이션에서 그래픽을 더욱 풍부하게 만들 수 있습니다.

## 문서화
### 목적
`SVGImageElement`는 SVG 문서 내에서 외부 이미지를 포함하기 위해 사용됩니다. 이 요소는 이미지의 위치, 크기, 기타 속성을 조정할 수 있는 방법을 제공합니다.

### 사용법
`SVGImageElement`는 `<image>` 태그로 SVG 내부에 정의되며, `JavaScript`를 사용하여 다음과 같은 속성을 조작할 수 있습니다:
- `href`: 이미지를 불러올 URL
- `width`: 이미지의 너비
- `height`: 이미지의 높이
- `x`: 이미지의 x좌표
- `y`: 이미지의 y좌표

### 세부사항
`SVGImageElement`는 HTML의 `img` 태그와 유사하지만, SVG 문서에서의 사용을 염두에 두고 설계되었습니다. SVG 내에서 배경을 투명하게 유지하며, 이미지의 스케일과 변환을 지원합니다.

## 예제
### 기본 사용 예제
```html
<svg width="200" height="200">
    <image 
        href="https://example.com/image.png" 
        x="10" 
        y="10" 
        width="100" 
        height="100" />
</svg>
```

### JavaScript로 속성 조작하기
```html
<svg id="mySVG" width="200" height="200">
    <image id="myImage" href="https://example.com/image.png" x="10" y="10" width="100" height="100" />
</svg>

<script>
    const img = document.getElementById('myImage');
    img.setAttribute('href', 'https://example.com/new-image.png');
    img.setAttribute('x', '20');
    img.setAttribute('y', '20');
</script>
```

## 설명
`SVGImageElement`를 사용할 때 주의해야 할 사항:
- `href` 속성이 유효한 URL이어야 하며, CORS 정책에 따라 외부 이미지를 불러올 수 있는지 확인해야 합니다.
- SVG 요소는 CSS 스타일이 적용될 수 있으며, 이를 통해 이미지의 시각적 효과를 조정할 수 있습니다.
- 이미지의 크기와 위치는 SVG의 뷰포트에 따라 다르게 보일 수 있으므로, 적절한 설정이 필요합니다.

## 한 줄 요약
`SVGImageElement`는 JavaScript를 통해 SVG 문서 내에서 외부 이미지를 동적으로 조작할 수 있는 요소입니다.