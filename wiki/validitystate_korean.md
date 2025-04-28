<!--
Meta Description: # ValidityState: 자바스크립트의 유효성 검사 상태 ## 개요 ValidityState는 HTML 폼 요소의 유효성 상태를 나타내는 객체로, 사용자가 입력한 데이터가 유효한지 여부를 평가하는 데 사용됩니다. 이 객체는 주로 폼 유효성 검사 기능과 관련하여 자...
Meta Keywords: 반환합니다, true를, validity, 유효성, 입력값이
-->

# ValidityState: 자바스크립트의 유효성 검사 상태

## 개요
ValidityState는 HTML 폼 요소의 유효성 상태를 나타내는 객체로, 사용자가 입력한 데이터가 유효한지 여부를 평가하는 데 사용됩니다. 이 객체는 주로 폼 유효성 검사 기능과 관련하여 자주 사용됩니다.

## 문서화
ValidityState 객체는 HTMLInputElement, HTMLTextAreaElement, 및 HTMLSelectElement와 같은 HTML 폼 요소에서 사용 가능합니다. 이 객체는 다음과 같은 프로퍼티를 포함하고 있습니다:

- **valid**: 입력값이 유효하면 true를 반환합니다.
- **valueMissing**: 필수 입력 필드가 비어 있을 경우 true를 반환합니다.
- **typeMismatch**: 입력값이 예상되는 타입과 맞지 않을 경우 true를 반환합니다.
- **patternMismatch**: 입력값이 지정된 패턴과 일치하지 않을 경우 true를 반환합니다.
- **tooLong**: 입력값의 길이가 지정된 최대 길이를 초과할 경우 true를 반환합니다.
- **tooShort**: 입력값의 길이가 지정된 최소 길이에 미치지 못할 경우 true를 반환합니다.
- **rangeUnderflow**: 숫자 입력값이 지정된 최소값보다 작을 경우 true를 반환합니다.
- **rangeOverflow**: 숫자 입력값이 지정된 최대값보다 클 경우 true를 반환합니다.

### 사용법
ValidityState 객체는 `checkValidity()` 메서드를 호출하여 얻을 수 있습니다. 예를 들어, 특정 입력 필드의 유효성 상태를 확인하려면 다음과 같은 코드를 사용할 수 있습니다.

```javascript
const inputField = document.querySelector('input[type="email"]');
if (!inputField.checkValidity()) {
    const validity = inputField.validity;
    console.log(validity.valueMissing); // 필수 입력이 비어 있는지 확인
    console.log(validity.typeMismatch); // 타입 불일치 확인
}
```

## 예제
### 기본 사용 예제
```html
<form id="myForm">
    <input type="email" required>
    <input type="submit">
</form>

<script>
    const form = document.getElementById('myForm');
    form.addEventListener('submit', function(event) {
        const emailField = form.querySelector('input[type="email"]');
        if (!emailField.checkValidity()) {
            const validity = emailField.validity;
            if (validity.valueMissing) {
                alert('이메일 필드는 필수입니다.');
            } else if (validity.typeMismatch) {
                alert('유효한 이메일 주소를 입력하세요.');
            }
            event.preventDefault(); // 폼 제출 방지
        }
    });
</script>
```

## 설명
ValidityState를 사용할 때 주의해야 할 점은 다음과 같습니다:

- 필수 입력 필드에 대한 유효성 검사를 할 때 `required` 속성을 사용해야 합니다. 이 속성이 없으면 `valueMissing` 프로퍼티는 항상 false를 반환합니다.
- 입력값의 유효성을 검사하기 위해서는 `checkValidity()` 메서드를 사용해야 하며, 이 메서드는 유효성이 유효하지 않을 경우 false를 반환합니다.
- ValidityState는 브라우저 호환성에 영향을 받을 수 있으므로, 지원되는 브라우저를 확인해야 합니다.

## 한 줄 요약
ValidityState는 HTML 폼 요소의 유효성 검사 상태를 나타내는 객체로, 입력값의 유효성 여부를 확인하는 데 유용합니다.