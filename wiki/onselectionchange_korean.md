<!--
Meta Description: # JavaScript onselectionchange 이벤트: 선택 변경 감지하기 ## 개요 `onselectionchange` 이벤트는 사용자가 선택한 텍스트나 요소가 변경될 때 발생하는 이벤트로, 주로 웹 애플리케이션에서 선택 상태를 감지하고 처리하는 데 사용됩니...
Meta Keywords: 이벤트는, onselectionchange, 선택된, 있습니다, selection
-->

# JavaScript onselectionchange 이벤트: 선택 변경 감지하기

## 개요
`onselectionchange` 이벤트는 사용자가 선택한 텍스트나 요소가 변경될 때 발생하는 이벤트로, 주로 웹 애플리케이션에서 선택 상태를 감지하고 처리하는 데 사용됩니다.

## 문서화
### 목적
`onselectionchange` 이벤트는 사용자가 텍스트를 선택할 때마다 발생하여, 선택된 내용을 기반으로 추가적인 작업을 수행할 수 있도록 돕습니다. 이 이벤트는 DOM Selection API와 함께 사용되어 선택된 내용을 실시간으로 감지할 수 있습니다.

### 사용법
`onselectionchange` 이벤트는 다음과 같은 방식으로 사용할 수 있습니다:

```javascript
document.addEventListener("selectionchange", function() {
    const selection = document.getSelection();
    console.log(selection.toString()); // 선택된 텍스트 출력
});
```

이벤트 리스너는 문서 내에서 선택이 변경될 때마다 호출되며, `document.getSelection()` 메서드를 통해 현재 선택된 내용을 가져올 수 있습니다.

### 세부사항
- `onselectionchange` 이벤트는 선택이 변경될 때마다 발생하므로, 반복적으로 호출될 수 있습니다.
- 이 이벤트는 주로 사용자 인터페이스의 반응성을 높이기 위해 사용됩니다.
- 선택된 텍스트를 다루기 위해서는 `Selection` 객체의 다양한 메서드와 속성을 활용할 수 있습니다.

## 예제
### 기본 사용 예제

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>onselectionchange 예제</title>
</head>
<body>
    <p>여기서 텍스트를 선택해 보세요!</p>
    <script>
        document.addEventListener("selectionchange", function() {
            const selection = document.getSelection();
            if (selection.rangeCount > 0) {
                console.log("선택된 텍스트: ", selection.toString());
            }
        });
    </script>
</body>
</html>
```

위 예제에서는 사용자에게 선택된 텍스트를 콘솔에 출력하는 간단한 기능을 구현하였습니다.

## 설명
- **일반적인 문제점**: `onselectionchange` 이벤트는 매우 자주 발생할 수 있으므로, 이벤트 핸들러 내에서 수행하는 작업이 성능에 영향을 줄 수 있습니다. 따라서 필요한 경우에만 처리하도록 최적화하는 것이 중요합니다.
- **브라우저 호환성**: 이 이벤트는 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 호환성 문제가 발생할 수 있습니다. 따라서 사용하기 전에 브라우저 호환성을 확인하는 것이 좋습니다.
- **사용자 경험**: 이 이벤트를 활용하면 사용자가 텍스트를 선택할 때 실시간으로 피드백을 제공할 수 있어 사용자 경험을 향상시킬 수 있습니다.

## 한 줄 요약
`onselectionchange` 이벤트는 사용자가 텍스트나 요소를 선택할 때 발생하며, 선택된 내용을 실시간으로 처리하는 데 유용합니다.