<!--
Meta Description: # JavaScript CanvasGradient: 캔버스 그라디언트 생성 및 활용 ## 개요 CanvasGradient는 HTML5의 캔버스 API에서 사용되는 객체로, 그래픽에 그라디언트(색의 변화를 주는 효과)를 적용할 수 있는 기능을 제공합니다. 이를 통해 보다...
Meta Keywords: ctx, 그라디언트를, 있습니다, const, addcolorstop
-->

# JavaScript CanvasGradient: 캔버스 그라디언트 생성 및 활용

## 개요
CanvasGradient는 HTML5의 캔버스 API에서 사용되는 객체로, 그래픽에 그라디언트(색의 변화를 주는 효과)를 적용할 수 있는 기능을 제공합니다. 이를 통해 보다 다채롭고 매력적인 그래픽을 쉽게 생성할 수 있습니다.

## 문서화
### 목적
CanvasGradient를 사용하면 선형 또는 방사형 그라디언트를 정의하여 HTML5 캔버스에서 렌더링할 수 있습니다. 이 객체는 주로 캔버스에 그려지는 도형의 색상을 더욱 다채롭게 만들기 위해 사용됩니다.

### 사용법
CanvasGradient 객체는 두 가지 주요 메서드로 생성됩니다:
1. **createLinearGradient(x0, y0, x1, y1)**: 선형 그라디언트를 생성합니다.
2. **createRadialGradient(x0, y0, r0, x1, y1, r1)**: 방사형 그라디언트를 생성합니다.

이 메서드들은 각각 시작점과 끝점 또는 중심과 반지름을 정의하여 다양한 그라디언트를 만들 수 있습니다.

### 세부 사항
- `addColorStop(offset, color)`: 그라디언트의 특정 위치에 색상을 추가합니다. `offset`은 0에서 1 사이의 값으로, 그라디언트의 위치를 나타냅니다.
- 객체는 기본적으로 색상과 투명도를 포함할 수 있습니다.
- 사용 시 반드시 캔버스의 컨텍스트에 적용해야 합니다.

## 예제
### 선형 그라디언트 예제
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

const gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'blue');

ctx.fillStyle = gradient;
ctx.fillRect(10, 10, 200, 100);
```

### 방사형 그라디언트 예제
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

const radialGradient = ctx.createRadialGradient(150, 150, 20, 150, 150, 100);
radialGradient.addColorStop(0, 'yellow');
radialGradient.addColorStop(1, 'green');

ctx.fillStyle = radialGradient;
ctx.fillRect(50, 50, 200, 200);
```

## 설명
- **자주 발생하는 실수**: 그라디언트를 정의한 후, 이를 사용하지 않고 직접 색상을 설정하는 경우가 있습니다. 반드시 `ctx.fillStyle` 또는 `ctx.strokeStyle`에 그라디언트를 설정해야 합니다.
- **성능 고려 사항**: 복잡한 그라디언트를 너무 많이 사용하면 성능 저하를 초래할 수 있습니다. 필요한 만큼만 사용하는 것이 좋습니다.

## 한 줄 요약
CanvasGradient는 HTML5 캔버스에서 다채로운 색상 변화를 통해 그래픽을 풍부하게 만드는 객체입니다.