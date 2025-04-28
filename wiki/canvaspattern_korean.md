<!--
Meta Description: # JavaScript의 CanvasPattern: 캔버스 패턴 생성 및 사용 ## 개요 `CanvasPattern`은 HTML5의 `<canvas>` 요소와 관련된 JavaScript API로, 반복되는 이미지나 색상 패턴을 생성하여 캔버스에 그릴 수 있도록 합니다....
Meta Keywords: canvas, const, ctx, image, repeat
-->

# JavaScript의 CanvasPattern: 캔버스 패턴 생성 및 사용

## 개요
`CanvasPattern`은 HTML5의 `<canvas>` 요소와 관련된 JavaScript API로, 반복되는 이미지나 색상 패턴을 생성하여 캔버스에 그릴 수 있도록 합니다. 이를 통해 복잡한 배경 및 텍스처를 손쉽게 추가할 수 있습니다.

## 문서화
`CanvasPattern`은 `CanvasRenderingContext2D.createPattern()` 메서드를 통해 생성됩니다. 이 메서드는 이미지, 비트맵, 또는 색상 패턴을 기반으로 반복 가능한 패턴을 만들어내며, 이를 캔버스에 적용하여 스타일링할 수 있습니다.

### 생성 방법
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
const image = new Image();
image.src = 'path/to/image.png';

image.onload = function() {
    const pattern = ctx.createPattern(image, 'repeat');
    ctx.fillStyle = pattern;
    ctx.fillRect(0, 0, canvas.width, canvas.height);
};
```

### 매개변수 설명
- `image`: 패턴을 생성할 때 사용할 이미지 객체입니다.
- `repeat`: 패턴의 반복 방식으로 `'repeat'`, `'repeat-x'`, `'repeat-y'`, `'no-repeat'` 중 하나를 지정할 수 있습니다.

## 예제
### 기본 사용 예제
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
const img = new Image();
img.src = 'pattern.png';

img.onload = function() {
    const pattern = ctx.createPattern(img, 'repeat');
    ctx.fillStyle = pattern;
    ctx.fillRect(0, 0, canvas.width, canvas.height);
};
```

### 반복 방식 예제
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
const img = new Image();
img.src = 'pattern.png';

img.onload = function() {
    const repeatXPattern = ctx.createPattern(img, 'repeat-x');
    ctx.fillStyle = repeatXPattern;
    ctx.fillRect(0, 0, canvas.width, canvas.height);
};
```

## 설명
`CanvasPattern`을 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **이미지 로딩**: 패턴을 생성하기 전에 이미지가 완전히 로드되어야 합니다. 이를 위해 `onload` 이벤트를 활용해야 합니다.
- **메모리 관리**: 사용하지 않는 패턴은 메모리 누수를 방지하기 위해 삭제하는 것이 좋습니다. 패턴을 더 이상 사용하지 않으면, `null`로 설정하여 참조를 제거할 수 있습니다.
- **지원 브라우저**: 모든 최신 브라우저에서 지원되지만, 구형 브라우저에서는 문제가 발생할 수 있습니다.

## 한 문장 요약
`CanvasPattern`은 JavaScript에서 캔버스에 반복 가능한 이미지나 색상 패턴을 생성하고 적용할 수 있는 기능입니다.