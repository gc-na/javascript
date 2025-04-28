<!--
Meta Description: # SVGAnimatedTransformList: JavaScript에서의 사용법과 예제 ## 개요 `SVGAnimatedTransformList`는 SVG(Scalable Vector Graphics)에서 사용되는 애니메이션 변환 리스트를 나타내는 객체입니다. Jav...
Meta Keywords: const, svgelement, svg, 변환을, baseval
-->

# SVGAnimatedTransformList: JavaScript에서의 사용법과 예제

## 개요
`SVGAnimatedTransformList`는 SVG(Scalable Vector Graphics)에서 사용되는 애니메이션 변환 리스트를 나타내는 객체입니다. JavaScript를 통해 SVG 요소의 변환을 동적으로 제어하고 애니메이션 효과를 구현할 수 있도록 도와줍니다.

## 문서화
`SVGAnimatedTransformList`는 SVG 요소의 변환을 애니메이션할 수 있게 해주는 객체로, 두 개의 속성 `baseVal`과 `animVal`을 포함합니다. `baseVal`은 기본 변환 리스트를 나타내며, `animVal`은 애니메이션에 의해 현재 적용된 변환 리스트를 나타냅니다.

### 목적
이 객체는 SVG 요소의 위치, 회전, 크기 조절 등의 변환을 애니메이션할 수 있게 하여, 보다 동적인 웹 애플리케이션을 구축할 수 있도록 지원합니다.

### 사용법
`SVGAnimatedTransformList`를 사용하려면, 먼저 SVG 요소에 접근하여 해당 요소의 변환 속성을 수정하거나 애니메이션할 수 있습니다. 다음은 기본적인 사용법입니다:

```javascript
// SVG 요소 선택
const svgElement = document.getElementById('mySvgElement');

// 변환 리스트 생성
const transformList = svgElement.transform.baseVal;

// 변환 추가
const translate = svgElement.ownerSVGElement.createSVGTransform();
translate.setTranslate(10, 20);
transformList.appendItem(translate);
```

## 예제
### 기본 사용 예제
```javascript
// SVG 요소 선택
const svgElement = document.getElementById('myRectangle');

// 변환 리스트 가져오기
const transformList = svgElement.transform.baseVal;

// 회전 변환 추가
const rotateTransform = svgElement.ownerSVGElement.createSVGTransform();
rotateTransform.setRotate(45, 50, 50); // (각도, 중심X, 중심Y)
transformList.appendItem(rotateTransform);

// 스케일 변환 추가
const scaleTransform = svgElement.ownerSVGElement.createSVGTransform();
scaleTransform.setScale(1.5, 1.5); // (X 스케일, Y 스케일)
transformList.appendItem(scaleTransform);
```

### 애니메이션 예제
```javascript
// 애니메이션을 위한 함수
function animate() {
    const svgElement = document.getElementById('myCircle');
    const transformList = svgElement.transform.baseVal;

    // 현재 변환 가져오기
    const currentTransform = transformList.getItem(0);
    
    // 변환을 변경하여 애니메이션 효과 생성
    currentTransform.setTranslate(currentTransform.matrix.e + 1, currentTransform.matrix.f);
    
    requestAnimationFrame(animate); // 다음 프레임 요청
}

// 애니메이션 시작
animate();
```

## 설명
`SVGAnimatedTransformList`를 사용할 때 주의해야 할 점은 `baseVal`과 `animVal`의 차이입니다. `baseVal`은 SVG의 기본 상태를 반영하며, `animVal`은 현재 애니메이션 상태를 반영합니다. 애니메이션이 진행되는 동안 두 값이 다를 수 있으며, 이 점을 이해하고 활용하는 것이 중요합니다.

또한, 변환을 추가할 때는 항상 `appendItem` 메서드를 사용해야 하며, 기존 변환을 수정할 경우 `setTransform` 메서드를 사용하는 것이 좋습니다.

## 한 문장 요약
`SVGAnimatedTransformList`는 JavaScript를 사용하여 SVG 요소의 변환을 애니메이션할 수 있는 객체로, 동적인 시각적 효과를 구현하는 데 유용합니다.