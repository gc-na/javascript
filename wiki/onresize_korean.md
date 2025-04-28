<!--
Meta Description: # JavaScript onresize 이벤트: 창 크기 변경 감지하기 ## 개요 `onresize`는 JavaScript에서 브라우저 창의 크기가 변경될 때 발생하는 이벤트입니다. 이 이벤트를 활용하여 반응형 웹 디자인을 구현하거나, 동적으로 레이아웃을 조정하는 데 ...
Meta Keywords: onresize, window, javascript, 크기를, function
-->

# JavaScript onresize 이벤트: 창 크기 변경 감지하기

## 개요
`onresize`는 JavaScript에서 브라우저 창의 크기가 변경될 때 발생하는 이벤트입니다. 이 이벤트를 활용하여 반응형 웹 디자인을 구현하거나, 동적으로 레이아웃을 조정하는 데 유용합니다.

## 문서화
### 목적
`onresize` 이벤트는 사용자가 브라우저 창의 크기를 조정할 때마다 호출되는 이벤트 리스너를 설정할 수 있게 해줍니다. 이를 통해 개발자는 UI 요소를 실시간으로 조정하거나, 특정 작업을 수행할 수 있습니다.

### 사용법
`onresize` 이벤트는 `window` 객체에 바인딩되며, 다음과 같은 방식으로 사용됩니다:

```javascript
window.onresize = function() {
    // 창 크기 변경 시 실행할 코드
};
```

또는, `addEventListener` 메서드를 사용하여 보다 유연하게 이벤트를 처리할 수 있습니다:

```javascript
window.addEventListener('resize', function() {
    // 창 크기 변경 시 실행할 코드
});
```

### 세부사항
- `onresize` 이벤트는 사용자가 창의 크기를 수동으로 조정할 때 뿐만 아니라, CSS 미디어 쿼리나 JavaScript로 창 크기를 변경할 때도 발생합니다.
- 이벤트 핸들러는 브라우저의 리플로우(Reflow) 과정에 영향을 줄 수 있으므로, 성능을 고려하여 최적화하는 것이 중요합니다.
- 특정 브라우저에서는 이벤트 발생 빈도가 높아질 수 있으므로, 디바운스(debounce) 기술을 사용하는 것이 좋습니다.

## 예제
### 기본 사용 예
다음은 `onresize` 이벤트를 사용하여 창 크기를 출력하는 간단한 예제입니다.

```javascript
window.onresize = function() {
    console.log('창 크기가 변경되었습니다. 현재 크기: ' + window.innerWidth + 'x' + window.innerHeight);
};
```

### 이벤트 리스너 사용 예
```javascript
function handleResize() {
    console.log('창 크기가 변경되었습니다.');
}

window.addEventListener('resize', handleResize);
```

## 설명
- **일반적인 문제점**: `onresize` 이벤트는 사용자가 창 크기를 조정할 때마다 호출되므로, 성능 저하가 발생할 수 있습니다. 이를 방지하기 위해 디바운스 기법을 사용할 수 있습니다.
  
- **디바운스 예제**:
```javascript
let timeout;
window.addEventListener('resize', function() {
    clearTimeout(timeout);
    timeout = setTimeout(function() {
        console.log('창 크기 조정 완료.');
    }, 250);
});
```

- **브라우저 호환성**: 대부분의 최신 브라우저에서 지원하지만, 구형 브라우저에서는 이벤트의 동작이 다를 수 있습니다.

## 한 문장 요약
`onresize` 이벤트는 사용자가 브라우저 창의 크기를 조정할 때 발생하며, 이를 통해 UI를 동적으로 조정할 수 있는 기능을 제공합니다.