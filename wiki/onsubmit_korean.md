<!--
Meta Description: # JavaScript onsubmit 이벤트: 폼 전송 처리의 모든 것 ## 개요 `onsubmit` 이벤트는 HTML 폼이 제출될 때 발생하는 이벤트로, JavaScript를 사용하여 폼의 제출을 제어하고, 유효성을 검사하며, 사용자에게 피드백을 제공하는 데 유용합...
Meta Keywords: onsubmit, return, 있습니다, form, email
-->

# JavaScript onsubmit 이벤트: 폼 전송 처리의 모든 것

## 개요
`onsubmit` 이벤트는 HTML 폼이 제출될 때 발생하는 이벤트로, JavaScript를 사용하여 폼의 제출을 제어하고, 유효성을 검사하며, 사용자에게 피드백을 제공하는 데 유용합니다.

## 문서화

### 목적
`onsubmit` 이벤트는 사용자가 HTML 폼을 제출할 때 자동으로 실행되는 JavaScript 코드를 정의하는 데 사용됩니다. 이 이벤트를 활용하면 폼 제출 전에 데이터를 검증하거나, 서버에 전송하기 전에 추가적인 처리를 할 수 있습니다.

### 사용법
`onsubmit` 이벤트는 `<form>` 요소에 직접 정의하거나, JavaScript를 통해 동적으로 추가할 수 있습니다. 아래의 일반적인 구문을 사용하여 이 이벤트를 설정할 수 있습니다.

```html
<form onsubmit="return validateForm()">
  <!-- 폼 내용 -->
  <input type="submit" value="전송">
</form>
```

또는 JavaScript를 통해 다음과 같이 설정할 수 있습니다:

```javascript
document.getElementById("myForm").onsubmit = function() {
  return validateForm();
};
```

### 세부 사항
- `onsubmit` 이벤트 핸들러는 반드시 `true` 또는 `false` 값을 반환해야 합니다. `true`를 반환하면 폼이 정상적으로 제출되며, `false`를 반환하면 제출이 중단됩니다.
- 이 이벤트는 사용자에게 폼 제출 이전에 유효성 검사를 수행할 수 있는 기회를 제공합니다. 예를 들어, 필수 입력란이 비어 있는지 확인하거나, 이메일 형식이 올바른지 검사할 수 있습니다.

## 예제

### 기본 사용법
아래는 `onsubmit` 이벤트를 사용하여 폼 데이터의 유효성을 검사하는 간단한 예제입니다.

```html
<form id="myForm" onsubmit="return validateForm()">
  이름: <input type="text" id="name" required>
  <input type="submit" value="제출">
</form>

<script>
function validateForm() {
  var name = document.getElementById("name").value;
  if (name == "") {
    alert("이름을 입력해주세요.");
    return false; // 폼 제출 중단
  }
  return true; // 폼 제출 허용
}
</script>
```

### AJAX와 함께 사용하기
AJAX를 활용하여 폼을 비동기적으로 제출하는 예제입니다.

```html
<form id="ajaxForm" onsubmit="return submitForm()">
  이메일: <input type="email" id="email" required>
  <input type="submit" value="제출">
</form>

<script>
function submitForm() {
  var email = document.getElementById("email").value;
  if (email == "") {
    alert("이메일을 입력해주세요.");
    return false; // 폼 제출 중단
  }

  // AJAX 요청 보내기
  var xhr = new XMLHttpRequest();
  xhr.open("POST", "submit.php", true);
  xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
  xhr.send("email=" + encodeURIComponent(email));

  // 폼 제출 중단
  return false;
}
</script>
```

## 설명
- **유효성 검사 시점**: `onsubmit` 이벤트는 사용자가 '제출' 버튼을 클릭할 때 발생하므로, 이 시점에서 유효성 검사를 수행할 수 있습니다.
- **버튼 클릭과 이벤트**: 만약 사용자가 'Enter' 키를 눌러서 폼을 제출하는 경우에도 `onsubmit` 이벤트가 발생합니다.
- **기본 제출 방지**: `return false;`를 사용하여 이벤트의 기본 동작(즉, 폼 제출)을 방지할 수 있습니다.

## 한 줄 요약
`onsubmit` 이벤트는 HTML 폼이 제출될 때 발생하며, 이를 통해 데이터 검증 및 전처리를 수행할 수 있습니다.