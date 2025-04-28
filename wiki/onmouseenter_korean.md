<!--
Meta Description: # JavaScript onmouseenter 이벤트: 마우스 오버 효과를 위한 완벽 가이드 ## 개요 `onmouseenter` 이벤트는 사용자가 HTML 요소 위에 마우스를 올렸을 때 발생하는 JavaScript 이벤트입니다. 이 이벤트는 사용자 인터페이스의 상호작...
Meta Keywords: div, onmouseenter, 이벤트, html, 요소에
-->

# JavaScript onmouseenter 이벤트: 마우스 오버 효과를 위한 완벽 가이드

## 개요
`onmouseenter` 이벤트는 사용자가 HTML 요소 위에 마우스를 올렸을 때 발생하는 JavaScript 이벤트입니다. 이 이벤트는 사용자 인터페이스의 상호작용을 향상시키기 위해 자주 사용됩니다.

## 문서화
### 목적
`onmouseenter`는 특정 HTML 요소에 마우스 커서가 들어가면 실행되는 이벤트 리스너를 설정하는 데 사용됩니다. 이 이벤트는 마우스가 요소의 경계에 들어가는 순간에만 발생하며, 자식 요소에 대해서는 발생하지 않습니다.

### 사용법
`onmouseenter` 이벤트는 HTML 요소에 직접 속성으로 추가하거나 JavaScript를 통해 이벤트 리스너로 등록할 수 있습니다.

#### HTML 속성 사용 예
```html
<div onmouseenter="mouseEnterHandler()">Mouse over me!</div>
```

#### JavaScript 사용 예
```javascript
const divElement = document.getElementById('myDiv');
divElement.addEventListener('mouseenter', mouseEnterHandler);

function mouseEnterHandler() {
    console.log('Mouse entered the div!');
}
```

### 세부사항
- **이벤트 전파**: `onmouseenter` 이벤트는 부모 요소에 전파되지 않습니다. 이는 자식 요소에 마우스가 들어가도 부모 요소의 `onmouseenter` 이벤트가 발생하지 않음을 의미합니다.
- **이벤트 취소**: 이 이벤트는 기본적으로 취소할 수 없습니다. 즉, 이벤트가 발생하면 항상 해당 처리기가 호출됩니다.

## 예제
1. 기본적인 사용 예
```html
<div onmouseenter="alert('Mouse entered!')">Hover over me</div>
```

2. JavaScript로 이벤트 리스너 추가
```html
<div id="hoverDiv">Hover over this div!</div>
<script>
    document.getElementById('hoverDiv').addEventListener('mouseenter', function() {
        console.log('Mouse has entered the div!');
    });
</script>
```

3. CSS와 함께 사용
```html
<style>
    .highlight { background-color: yellow; }
</style>
<div id="hoverDiv">Hover over this div!</div>
<script>
    const div = document.getElementById('hoverDiv');
    div.addEventListener('mouseenter', () => div.classList.add('highlight'));
    div.addEventListener('mouseleave', () => div.classList.remove('highlight'));
</script>
```

## 설명
- **성능 문제**: 이벤트 리스너가 많은 요소에 연결되어 있을 경우 성능에 영향을 줄 수 있습니다. 이벤트 리스너는 필요한 최소한의 요소에만 설정하는 것이 좋습니다.
- **다른 이벤트와의 차이**: `onmouseenter`는 `onmouseover`와 비슷하지만, 부모 요소에 대한 이벤트 전파가 없다는 점에서 차이가 있습니다. `onmouseover`는 자식 요소에도 적용됩니다.

## 한 줄 요약
`onmouseenter` 이벤트는 HTML 요소에 마우스가 들어올 때 발생하며, 자식 요소에 대해서는 전파되지 않는 특징이 있습니다.