<!--
Meta Description: # SVGTransform: JavaScript에서 SVG 변환을 다루는 방법 ## 개요 `SVGTransform`은 Scalable Vector Graphics(SVG)에서 변환을 정의하는 객체로, JavaScript를 통해 SVG 요소의 위치, 크기 및 회전을 조절...
Meta Keywords: svg, svgtransform, svgelement, 변환을, 요소의
-->

# SVGTransform: JavaScript에서 SVG 변환을 다루는 방법

## 개요
`SVGTransform`은 Scalable Vector Graphics(SVG)에서 변환을 정의하는 객체로, JavaScript를 통해 SVG 요소의 위치, 크기 및 회전을 조절할 수 있습니다. 이 객체는 SVG 요소에 변환을 적용할 때 필수적이며, 다양한 변환 함수를 제공합니다.

## 문서화
### 목적
`SVGTransform` 객체는 SVG 요소의 변환을 관리하기 위해 사용됩니다. 이를 통해 사용자들은 그래픽 요소를 이동, 회전, 확대 또는 축소할 수 있으며, 복잡한 시각적 효과를 쉽게 구현할 수 있습니다.

### 사용법
`SVGTransform` 객체는 SVG 요소의 `transform` 속성과 함께 사용됩니다. JavaScript에서는 `createSVGTransform()` 메서드를 통해 새로운 변환 객체를 생성하고, 이 객체를 SVG 요소의 변환 목록에 추가할 수 있습니다.

#### 기본 사용법
```javascript
// SVG 요소 선택
const svgElement = document.getElementById("mySvgElement");

// 변환 객체 생성
const svgTransform = svgElement.ownerSVGElement.createSVGTransform();

// 변환 추가: 이동
svgTransform.setTranslate(10, 20);

// 변환 목록에 추가
svgElement.transform.baseVal.appendItem(svgTransform);
```

### 세부 사항
- `SVGTransform` 객체는 다음과 같은 주요 메서드를 제공합니다:
  - `setTranslate(x, y)`: 지정한 x, y 좌표로 요소를 이동합니다.
  - `setScale(sx, sy)`: 요소를 sx, sy 비율로 확대 또는 축소합니다.
  - `setRotate(angle, cx, cy)`: 지정한 각도만큼 요소를 회전합니다. 선택적으로 회전 중심을 지정할 수 있습니다.
  - `setMatrix(matrix)`: 변환 행렬을 설정하여 복합 변환을 적용합니다.

## 예제
### 이동 변환
```javascript
const svgElement = document.getElementById("mySvgElement");
const translateTransform = svgElement.ownerSVGElement.createSVGTransform();
translateTransform.setTranslate(50, 100);
svgElement.transform.baseVal.appendItem(translateTransform);
```

### 회전 변환
```javascript
const rotateTransform = svgElement.ownerSVGElement.createSVGTransform();
rotateTransform.setRotate(45, 50, 50); // 45도 회전, 중심(50, 50)
svgElement.transform.baseVal.appendItem(rotateTransform);
```

### 확대/축소 변환
```javascript
const scaleTransform = svgElement.ownerSVGElement.createSVGTransform();
scaleTransform.setScale(2, 2); // 2배 확대
svgElement.transform.baseVal.appendItem(scaleTransform);
```

## 설명
`SVGTransform`을 사용할 때 주의해야 할 몇 가지 사항이 있습니다. 
- 변환을 적용할 때는 변환의 순서가 중요합니다. 예를 들어, 회전 후 이동을 하면 이동이 회전된 위치에서 적용됩니다.
- SVG 요소의 `transform.baseVal`은 변환 목록을 관리하며, 변환을 추가하거나 제거할 때 적절한 메서드를 사용해야 합니다.
- 변환이 적용된 SVG 요소는 원본 위치를 잃을 수 있으므로, 각 변환의 결과를 항상 확인하는 것이 좋습니다.

## 한 줄 요약
`SVGTransform`은 JavaScript를 사용하여 SVG 요소의 변환을 정의하고 조작하는 데 사용되는 객체입니다.