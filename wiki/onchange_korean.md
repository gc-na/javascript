<!--
Meta Description: # JavaScript의 onchange 이벤트: 사용법 및 예제 ## 개요 `onchange`는 HTML 폼 요소의 값이 변경될 때 발생하는 이벤트로, JavaScript를 통해 사용자 입력에 반응할 수 있는 기능을 제공합니다. 이 이벤트는 주로 `<input>`, ...
Meta Keywords: onchange, html, 이벤트는, input, option
-->

# JavaScript의 onchange 이벤트: 사용법 및 예제

## 개요
`onchange`는 HTML 폼 요소의 값이 변경될 때 발생하는 이벤트로, JavaScript를 통해 사용자 입력에 반응할 수 있는 기능을 제공합니다. 이 이벤트는 주로 `<input>`, `<select>`, `<textarea>`와 같은 요소에서 사용됩니다.

## 문서화
### 목적
`onchange` 이벤트는 사용자가 입력 필드의 값을 변경하고 포커스를 잃었을 때 발생합니다. 이 이벤트를 활용하면 사용자의 입력을 실시간으로 처리하거나, 특정 작업을 수행할 수 있습니다. 

### 사용법
`onchange` 이벤트는 다음과 같은 형태로 사용됩니다:

```html
<input type="text" onchange="yourFunction()">
```

또는 JavaScript로 이벤트 리스너를 추가할 수도 있습니다:

```javascript
document.getElementById("yourInput").addEventListener("change", yourFunction);
```

### 세부 사항
- 이벤트는 사용자가 값을 변경한 후 포커스를 다른 요소로 이동할 때 발생합니다.
- `onchange` 이벤트는 입력 필드에 대한 변화를 감지하므로, 사용자가 직접 입력한 경우에만 동작합니다.
- `<input type="checkbox">`, `<input type="radio">`와 같은 요소의 경우, 체크 상태의 변화도 이 이벤트로 감지됩니다.

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onchange 예제</title>
</head>
<body>
    <label for="age">나이를 입력하세요:</label>
    <input type="text" id="age" onchange="checkAge()">

    <script>
        function checkAge() {
            const age = document.getElementById("age").value;
            if (age < 18) {
                alert("미성년자입니다.");
            } else {
                alert("성인입니다.");
            }
        }
    </script>
</body>
</html>
```

### 선택 박스 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onchange 선택 박스 예제</title>
</head>
<body>
    <label for="color">좋아하는 색상을 선택하세요:</label>
    <select id="color" onchange="showColor()">
        <option value="red">빨강</option>
        <option value="blue">파랑</option>
        <option value="green">초록</option>
    </select>

    <p id="selectedColor"></p>

    <script>
        function showColor() {
            const color = document.getElementById("color").value;
            document.getElementById("selectedColor").innerText = "선택한 색상: " + color;
        }
    </script>
</body>
</html>
```

## 설명
`onchange` 이벤트를 사용할 때 주의해야 할 점은, 이벤트가 발생하는 시점입니다. 사용자가 입력을 하고 포커스를 이동해야만 이벤트가 발생하므로, 실시간으로 입력을 반영하고 싶다면 `oninput` 이벤트를 사용하는 것이 더 적절합니다. 또한, `<input>` 요소의 초기 값이 변경될 때는 `onchange`가 호출되지 않으므로, 초기 값을 체크할 필요가 있을 수 있습니다.

## 한 줄 요약
`onchange` 이벤트는 사용자가 입력 필드의 값을 변경하고 포커스를 잃을 때 발생하여, 입력값을 처리할 수 있는 기능을 제공합니다.