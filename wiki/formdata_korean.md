<!--
Meta Description: # FormData: 자바스크립트에서 폼 데이터를 쉽게 처리하는 방법 ## 개요 `FormData` 객체는 웹 애플리케이션에서 폼 데이터를 손쉽게 생성하고 조작할 수 있도록 도와주는 자바스크립트 API입니다. 이를 통해 비동기 요청을 통해 서버로 데이터를 전송할 수 있...
Meta Keywords: formdata, 데이터를, name, 객체는, 있습니다
-->

# FormData: 자바스크립트에서 폼 데이터를 쉽게 처리하는 방법

## 개요
`FormData` 객체는 웹 애플리케이션에서 폼 데이터를 손쉽게 생성하고 조작할 수 있도록 도와주는 자바스크립트 API입니다. 이를 통해 비동기 요청을 통해 서버로 데이터를 전송할 수 있습니다.

## 문서화

### 목적
`FormData`는 HTML 폼의 데이터를 키-값 쌍으로 구성하여, XMLHttpRequest 또는 Fetch API를 통해 서버로 전송할 수 있게 해줍니다. 이 객체는 파일 업로드와 같은 복잡한 데이터 전송을 간편하게 처리할 수 있도록 설계되었습니다.

### 사용법
`FormData` 객체는 기본적으로 다음과 같이 생성할 수 있습니다:

```javascript
let formData = new FormData();
```

기존의 HTML 폼을 기반으로 `FormData` 객체를 생성하려면, 폼 요소를 매개변수로 전달합니다:

```javascript
let formElement = document.querySelector('form');
let formData = new FormData(formElement);
```

이렇게 생성된 `formData` 객체는 `.append()`, `.delete()`, `.get()`, `.has()` 등의 메서드를 사용하여 데이터를 조작할 수 있습니다.

#### 주요 메서드
- `append(name, value)`: 지정한 이름과 값을 추가합니다.
- `delete(name)`: 지정한 이름의 데이터를 삭제합니다.
- `get(name)`: 지정한 이름의 데이터를 반환합니다.
- `has(name)`: 지정한 이름의 데이터가 존재하는지를 확인합니다.

## 예제

### 기본 사용 예제

```javascript
// 새로운 FormData 객체 생성
let formData = new FormData();

// 데이터 추가
formData.append('username', 'JohnDoe');
formData.append('age', 30);

// 데이터 확인
console.log(formData.get('username')); // JohnDoe
console.log(formData.get('age'));      // 30
```

### HTML 폼을 통한 사용

```html
<form id="myForm">
    <input type="text" name="username" value="JaneDoe">
    <input type="file" name="profilePicture">
    <button type="submit">Submit</button>
</form>

<script>
document.getElementById('myForm').addEventListener('submit', function(event) {
    event.preventDefault(); // 기본 제출 이벤트 방지

    let formData = new FormData(this);

    // 데이터 전송 예시
    fetch('/submit', {
        method: 'POST',
        body: formData
    })
    .then(response => response.json())
    .then(data => console.log(data));
});
</script>
```

## 설명
`FormData` 객체를 사용할 때 주의해야 할 점은 다음과 같습니다:

- `FormData` 객체는 자동으로 Content-Type을 `multipart/form-data`로 설정합니다. 이로 인해 파일 업로드와 같은 복잡한 데이터를 보다 쉽게 처리할 수 있습니다.
- `FormData`를 사용할 때, `get()` 메서드는 배열 값을 지원하지 않으며, 같은 이름의 필드가 여러 개 있을 경우 첫 번째 값만 반환합니다. 모든 값을 가져오려면 `getAll()` 메서드를 사용해야 합니다.
- 브라우저 호환성 문제로 인해 일부 오래된 브라우저에서는 `FormData`를 지원하지 않을 수 있습니다. 이 점을 염두에 두고 사용해야 합니다.

## 한 줄 요약
`FormData`는 자바스크립트로 폼 데이터를 쉽게 조작하고 서버로 전송할 수 있도록 도와주는 객체입니다.