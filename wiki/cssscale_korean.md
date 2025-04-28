<!--
Meta Description: # CSSScale: 자바스크립트에서의 CSS 변환 스케일 기능 ## 개요 CSSScale은 자바스크립트에서 CSS의 transform 속성을 사용하여 요소의 크기를 조정하는 기능입니다. 이 기능은 웹 개발자에게 디자인 요소를 동적으로 조정할 수 있는 유연성을 제공합니...
Meta Keywords: scale, element, transform, myelement, style
-->

# CSSScale: 자바스크립트에서의 CSS 변환 스케일 기능

## 개요
CSSScale은 자바스크립트에서 CSS의 transform 속성을 사용하여 요소의 크기를 조정하는 기능입니다. 이 기능은 웹 개발자에게 디자인 요소를 동적으로 조정할 수 있는 유연성을 제공합니다.

## 문서
### 목적
CSSScale은 HTML 요소의 크기를 비율에 따라 확대하거나 축소할 수 있게 해줍니다. 이를 통해 사용자 인터페이스를 보다 직관적으로 만들고, 반응형 디자인을 구현할 수 있습니다.

### 사용법
CSSScale을 사용하려면, CSS의 `transform` 속성을 수정하여 scale 값을 설정합니다. `scale()` 함수는 두 개의 매개변수를 받습니다: x축과 y축의 크기 비율입니다. 기본적으로 `scale(1, 1)`는 요소의 원래 크기를 유지하며, `scale(2, 2)`는 2배로 확대합니다.

```javascript
// 요소 선택
const element = document.getElementById('myElement');

// 요소 크기 조정
element.style.transform = 'scale(1.5, 1.5)';
```

## 예제
1. **기본 사용 예제**:
    ```html
    <div id="myElement" style="width: 100px; height: 100px; background-color: blue;"></div>
    <script>
        const element = document.getElementById('myElement');
        element.style.transform = 'scale(2, 2)';
    </script>
    ```

2. **비율 조정**:
    ```html
    <div id="myElement" style="width: 100px; height: 100px; background-color: red;"></div>
    <script>
        const element = document.getElementById('myElement');
        element.style.transform = 'scale(1, 0.5)'; // 세로 방향으로 반으로 축소
    </script>
    ```

## 설명
- **커먼 함정**: CSSScale을 사용할 때, 비율이 1보다 작으면 요소가 축소되고, 1보다 크면 확대됩니다. 그러나 비율이 0 이하가 되면 요소가 보이지 않게 됩니다.
- **애니메이션**: 스케일 변환은 CSS의 transition 속성과 함께 사용하면 더욱 부드러운 애니메이션 효과를 제공할 수 있습니다.
- **중복 적용**: 여러 번 스케일을 적용하면 각 변환이 누적됩니다. 예를 들어, `scale(2, 2)`를 두 번 적용하면 최종 크기는 4배가 됩니다.

## 한 줄 요약
CSSScale은 자바스크립트를 사용하여 HTML 요소의 크기를 비율에 따라 조정하는 기능입니다.