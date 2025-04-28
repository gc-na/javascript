<!--
Meta Description: # JavaScript onblur 이벤트: 사용법과 예제 ## 개요 `onblur` 이벤트는 사용자가 요소의 포커스를 잃을 때 발생하는 이벤트입니다. 주로 입력 필드와 같은 포커스를 받을 수 있는 요소에서 사용되며, 사용자 인터페이스(UI)에서 중요한 역할을 합니다....
Meta Keywords: onblur, 이벤트는, 포커스를, html, input
-->

# JavaScript onblur 이벤트: 사용법과 예제

## 개요
`onblur` 이벤트는 사용자가 요소의 포커스를 잃을 때 발생하는 이벤트입니다. 주로 입력 필드와 같은 포커스를 받을 수 있는 요소에서 사용되며, 사용자 인터페이스(UI)에서 중요한 역할을 합니다.

## 문서화
### 목적
`onblur` 이벤트는 사용자가 입력 필드에서 클릭하거나 키보드를 사용할 때 포커스를 잃는 경우에 반응하여 특정 동작을 정의하는 데 사용됩니다. 이 이벤트는 데이터 유효성 검사, UI 업데이트 등 다양한 용도로 활용될 수 있습니다.

### 사용법
`onblur` 이벤트는 HTML 요소에 직접 속성으로 추가하거나 JavaScript를 통해 이벤트 리스너를 등록하는 방식으로 사용할 수 있습니다.

#### HTML 속성 사용
```html
<input type="text" onblur="handleBlur()" />
```

#### JavaScript로 이벤트 리스너 등록
```javascript
const inputField = document.querySelector('input');
inputField.addEventListener('blur', handleBlur);

function handleBlur() {
    console.log('Input field lost focus');
}
```

### 세부사항
- `onblur` 이벤트는 포커스를 잃은 요소에 대해서만 발생합니다.
- 이 이벤트는 `focus` 이벤트와 짝을 이루며, 사용자가 요소에 포커스를 주었을 때 `focus` 이벤트가 발생합니다.
- 이벤트가 발생할 때, `this` 키워드를 사용하여 현재 요소에 접근할 수 있습니다.

## 예제
### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>onblur 예제</title>
</head>
<body>
    <input type="text" id="username" onblur="validateUsername()" />
    <script>
        function validateUsername() {
            const input = document.getElementById('username');
            if (input.value === '') {
                alert('사용자 이름을 입력해주세요.');
            }
        }
    </script>
</body>
</html>
```

## 설명
### 일반적인 함정 및 주의사항
1. **이벤트 전파**: `onblur` 이벤트는 버블링되지 않기 때문에, 부모 요소에서 이 이벤트를 감지할 수 없습니다. 필요시 다른 방법으로 이벤트를 처리해야 합니다.
2. **포커스 이동**: 사용자가 다른 입력 필드로 포커스를 이동할 때, 해당 필드의 `onblur` 이벤트가 발생합니다. 따라서, 여러 필드가 있는 경우 이벤트가 다수 발생할 수 있습니다.
3. **브라우저 호환성**: 대부분의 현대 브라우저에서 지원되지만, 특정 구형 브라우저에서는 일부 문제가 발생할 수 있습니다.

## 한 줄 요약
`onblur` 이벤트는 사용자가 요소의 포커스를 잃을 때 발생하며, 데이터 유효성 검사와 UI 업데이트에 활용됩니다.