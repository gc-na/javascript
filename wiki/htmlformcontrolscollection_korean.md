<!--
Meta Description: # HTMLFormControlsCollection: JavaScript에서의 HTML 폼 컨트롤 컬렉션 ## 개요 `HTMLFormControlsCollection`은 HTML 폼 내의 모든 폼 요소들을 집합적으로 다룰 수 있게 해주는 JavaScript 객체입니다....
Meta Keywords: 있습니다, htmlformcontrolscollection, html, form, 요소의
-->

# HTMLFormControlsCollection: JavaScript에서의 HTML 폼 컨트롤 컬렉션

## 개요
`HTMLFormControlsCollection`은 HTML 폼 내의 모든 폼 요소들을 집합적으로 다룰 수 있게 해주는 JavaScript 객체입니다. 이를 통해 개발자는 폼 요소에 접근하고, 조작하며, 유효성 검사를 수행하는 등 다양한 작업을 수행할 수 있습니다.

## 문서화
`HTMLFormControlsCollection`은 HTML `<form>` 요소에 포함된 모든 폼 컨트롤(예: `<input>`, `<select>`, `<textarea>` 등)을 포함하는 컬렉션입니다. 이 컬렉션은 배열과 유사한 형태로, 각 폼 요소에 인덱스를 통해 접근할 수 있습니다.

### 주요 기능
- **접근성**: `form.elements` 프로퍼티를 통해 폼 내의 모든 컨트롤에 접근할 수 있습니다.
- **조작**: 각 폼 컨트롤의 값을 읽거나 변경할 수 있습니다.
- **유효성 검사**: 폼 요소의 유효성 검사 및 상태를 쉽게 확인할 수 있습니다.

### 사용법
`HTMLFormControlsCollection`은 HTML 폼과 연결된 JavaScript 코드에서 주로 사용됩니다. 다음은 기본적인 사용 예제입니다.

## 예제
```html
<form id="myForm">
    <input type="text" name="username" />
    <input type="password" name="password" />
    <input type="submit" value="Submit" />
</form>

<script>
    const form = document.getElementById('myForm');
    const controls = form.elements;

    // 모든 폼 요소의 이름과 값을 출력
    for (let i = 0; i < controls.length; i++) {
        console.log(`${controls[i].name}: ${controls[i].value}`);
    }
</script>
```

위 코드에서는 `myForm`이라는 ID를 가진 폼 요소를 가져와 내부의 모든 폼 컨트롤에 접근하여 각 요소의 이름과 값을 출력합니다.

## 설명
`HTMLFormControlsCollection`을 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **폼 요소의 타입**: 각 요소의 타입에 따라 접근 방법이 달라질 수 있습니다. 예를 들어, `<input>`의 타입이 'checkbox'인 경우, `checked` 프로퍼티를 사용하여 체크 여부를 확인해야 합니다.
- **폼 제출 처리**: 폼을 제출할 때 폼 컨트롤의 값이 올바른지 검증하는 로직을 추가하면 좋습니다.
- **명명 규칙**: 폼 요소의 `name` 속성을 적절히 설정하면, `HTMLFormControlsCollection`을 통해 더 쉽게 요소를 찾을 수 있습니다.

## 한 줄 요약
`HTMLFormControlsCollection`은 HTML 폼 내의 모든 컨트롤을 집합적으로 관리할 수 있는 JavaScript 객체입니다.