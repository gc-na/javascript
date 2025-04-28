<!--
Meta Description: # CanvasRenderingContext2D: JavaScript에서 2D 그래픽스를 위한 컨텍스트 ## 개요 `CanvasRenderingContext2D`는 HTML5의 `<canvas>` 요소에서 2D 그래픽을 그릴 수 있도록 해주는 JavaScript API...
Meta Keywords: ctx, canvasrenderingcontext2d, canvas, 그리기, 있습니다
-->

# CanvasRenderingContext2D: JavaScript에서 2D 그래픽스를 위한 컨텍스트

## 개요
`CanvasRenderingContext2D`는 HTML5의 `<canvas>` 요소에서 2D 그래픽을 그릴 수 있도록 해주는 JavaScript API입니다. 이 객체를 사용하면 도형, 텍스트, 이미지 등을 캔버스에 그릴 수 있으며, 애니메이션 및 게임 개발에 널리 사용됩니다.

## 문서화

### 목적
`CanvasRenderingContext2D`는 2D 그래픽스를 그리기 위한 다양한 메서드와 속성을 제공합니다. 이를 통해 개발자는 브라우저에서 동적으로 이미지를 생성하고 조작할 수 있습니다.

### 사용법
1. **캔버스 요소 생성**: HTML 문서에 `<canvas>` 요소를 추가합니다.
2. **컨텍스트 가져오기**: JavaScript를 사용하여 캔버스의 2D 컨텍스트를 가져옵니다.
3. **그래픽 작업 수행**: 다양한 메서드를 사용하여 도형, 텍스트 또는 이미지를 그립니다.

### 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CanvasRenderingContext2D 예제</title>
</head>
<body>
    <canvas id="myCanvas" width="500" height="500" style="border:1px solid #000000;"></canvas>
    <script>
        const canvas = document.getElementById('myCanvas');
        const ctx = canvas.getContext('2d');

        // 사각형 그리기
        ctx.fillStyle = '#FF0000';
        ctx.fillRect(20, 20, 150, 100);

        // 원 그리기
        ctx.beginPath();
        ctx.arc(240, 70, 50, 0, Math.PI * 2, true);
        ctx.fillStyle = '#00FF00';
        ctx.fill();

        // 텍스트 그리기
        ctx.font = '30px Arial';
        ctx.fillStyle = '#0000FF';
        ctx.fillText('안녕하세요!', 20, 200);
    </script>
</body>
</html>
```

## 설명
`CanvasRenderingContext2D`를 사용할 때 몇 가지 주의해야 할 점이 있습니다:

- **크기와 비율**: 캔버스의 크기를 설정할 때 CSS 스타일과 실제 해상도가 일치해야 합니다. 그렇지 않으면 그래픽 품질이 저하될 수 있습니다.
- **좌표계**: 캔버스의 좌표계는 왼쪽 상단 모서리 (0, 0)에서 시작합니다. 아래로 갈수록 Y 좌표가 증가합니다.
- **애니메이션**: 매 프레임마다 캔버스를 지우고 새로 그려야 하는 경우, `requestAnimationFrame()`을 사용하여 부드러운 애니메이션을 구현할 수 있습니다.
- **성능 최적화**: 복잡한 그래픽을 처리할 때, 오프스크린 캔버스를 사용하거나 필요한 부분만 다시 그리는 방식으로 성능을 최적화할 수 있습니다.

## 한 줄 요약
`CanvasRenderingContext2D`는 JavaScript에서 2D 그래픽을 그리기 위한 강력한 API로, 다양한 도형과 텍스트를 동적으로 생성할 수 있게 해줍니다.