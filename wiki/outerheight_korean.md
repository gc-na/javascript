<!--
Meta Description: # JavaScript outerHeight: 웹 요소의 전체 높이 측정하기 ## 개요 JavaScript에서 `outerHeight`는 브라우저 창 또는 특정 요소의 전체 높이를 측정하는 데 사용되는 속성입니다. 이 속성은 주로 웹 페이지의 레이아웃을 조정하거나 요소...
Meta Keywords: outerheight, 요소의, 브라우저, 있습니다, 높이를
-->

# JavaScript outerHeight: 웹 요소의 전체 높이 측정하기

## 개요
JavaScript에서 `outerHeight`는 브라우저 창 또는 특정 요소의 전체 높이를 측정하는 데 사용되는 속성입니다. 이 속성은 주로 웹 페이지의 레이아웃을 조정하거나 요소의 크기를 동적으로 처리하는 데 유용합니다.

## 문서화
### 목적
`outerHeight` 속성은 브라우저 창 또는 특정 DOM 요소의 전체 높이를 픽셀 단위로 반환합니다. 이 값은 요소의 콘텐츠 높이, 패딩, 테두리 및 마진을 포함하여 계산됩니다. 이 속성은 주로 사용자 인터페이스(UI)를 조작하거나 특정 조건에 따라 레이아웃을 조정할 때 필요합니다.

### 사용법
`outerHeight` 속성을 사용하려면, JavaScript 내에서 다음과 같은 방식으로 접근할 수 있습니다:

```javascript
window.outerHeight; // 브라우저 창의 전체 높이
document.getElementById('elementId').offsetHeight; // 특정 요소의 전체 높이
```

### 세부 사항
- **브라우저 창의 `outerHeight`**: `window.outerHeight`를 통해 브라우저의 전체 높이를 가져올 수 있습니다. 이는 브라우저 툴바와 주소 표시줄을 포함합니다.
- **요소의 `outerHeight`**: 특정 요소의 높이는 `offsetHeight` 속성을 사용하여 가져올 수 있습니다. 이 값은 요소의 콘텐츠, 패딩, 테두리 크기를 포함하지만 마진은 포함하지 않습니다.
  
## 예제
### 예제 1: 브라우저 창의 전체 높이 가져오기
```javascript
console.log("브라우저 창의 전체 높이: " + window.outerHeight + "px");
```

### 예제 2: 특정 요소의 전체 높이 가져오기
```html
<div id="myElement" style="height: 200px; padding: 20px; border: 5px solid black;">
    Hello, World!
</div>

<script>
    var element = document.getElementById('myElement');
    console.log("요소의 전체 높이: " + element.offsetHeight + "px");
</script>
```

## 설명
- **일반적인 함정**: `outerHeight`는 직접적으로 사용되지 않으며, `window.outerHeight`를 통해 브라우저 창 크기를 가져오는 것이 일반적입니다. 또한, DOM 요소의 전체 높이를 가져오려면 `offsetHeight`를 사용해야 하며, `outerHeight`라는 용어는 혼동을 일으킬 수 있습니다.
- **브라우저 호환성**: 대부분의 현대 브라우저에서 `outerHeight`는 지원되지만, 특정 구형 브라우저에서는 예상한 대로 동작하지 않을 수 있습니다.
- **유용한 팁**: 레이아웃을 동적으로 조정할 경우, 브라우저 창의 크기 변화에 따라 이벤트 리스너를 추가하여 `outerHeight` 값을 사용할 수 있습니다.

## 한줄 요약
JavaScript의 `outerHeight`는 브라우저 창이나 특정 요소의 전체 높이를 측정하는 데 유용한 속성입니다.