<!--
Meta Description: # HTMLCanvasElement: 자바스크립트에서의 활용 ## 개요 HTMLCanvasElement는 HTML `<canvas>` 요소를 JavaScript에서 조작하기 위한 인터페이스로, 그래픽을 그리거나 애니메이션을 만들고 이미지 및 비디오를 처리하는 데 사용됩...
Meta Keywords: canvas, ctx, html, 그래픽을, 있습니다
-->

# HTMLCanvasElement: 자바스크립트에서의 활용

## 개요
HTMLCanvasElement는 HTML `<canvas>` 요소를 JavaScript에서 조작하기 위한 인터페이스로, 그래픽을 그리거나 애니메이션을 만들고 이미지 및 비디오를 처리하는 데 사용됩니다. 이 요소는 동적인 그래픽을 생성할 수 있도록 해줍니다.

## 문서화
HTMLCanvasElement는 HTML 문서 내에서 `<canvas>` 태그로 정의된 캔버스를 나타내며, 자바스크립트를 통해 접근하고 조작할 수 있습니다. 이 요소는 2D 및 3D 그래픽을 그릴 수 있는 다양한 메서드를 제공합니다.

### 목적
- 웹 기반 그래픽 콘텐츠의 생성 및 조작
- 게임 및 데이터 시각화와 같은 동적 비주얼 구현

### 사용법
1. HTML 내에서 `<canvas>` 요소 정의:
   ```html
   <canvas id="myCanvas" width="500" height="500"></canvas>
   ```

2. JavaScript를 통해 캔버스 접근 및 조작:
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   ```

3. 그래픽 그리기:
   ```javascript
   ctx.fillStyle = 'blue';
   ctx.fillRect(20, 20, 150, 100);
   ```

### 세부 사항
- `getContext()` 메서드를 사용해 2D 또는 WebGL 컨텍스트를 얻을 수 있습니다.
- 다양한 메서드와 속성: `fillRect()`, `strokeRect()`, `drawImage()`, `fillText()` 등.
- 캔버스는 픽셀 기반의 그래픽을 다루므로 해상도와 스케일에 유의해야 합니다.

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Canvas 예제</title>
</head>
<body>
    <canvas id="myCanvas" width="500" height="500"></canvas>
    <script>
        const canvas = document.getElementById('myCanvas');
        const ctx = canvas.getContext('2d');

        // 사각형 그리기
        ctx.fillStyle = 'red';
        ctx.fillRect(50, 50, 200, 150);

        // 원 그리기
        ctx.beginPath();
        ctx.arc(150, 150, 50, 0, Math.PI * 2); // (x, y, radius, startAngle, endAngle)
        ctx.fillStyle = 'green';
        ctx.fill();
    </script>
</body>
</html>
```

## 설명
- **해상도**: 캔버스의 해상도가 낮으면 그래픽이 뭉개질 수 있습니다. 좋은 품질의 그래픽을 위해 적절한 해상도를 설정하세요.
- **비동기적 작업**: 애니메이션을 만들 때, 캔버스의 내용을 매 프레임마다 새로 그려야 합니다. `requestAnimationFrame`을 사용하여 부드러운 애니메이션을 구현할 수 있습니다.
- **컨텍스트**: 2D와 WebGL 컨텍스트가 다르므로, 적절한 컨텍스트를 선택하는 것이 중요합니다.

## 한 줄 요약
HTMLCanvasElement는 웹 페이지에서 동적인 그래픽을 생성하고 조작하기 위해 JavaScript에서 사용되는 HTML 요소입니다.