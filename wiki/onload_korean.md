<!--
Meta Description: # JavaScript의 onload 이벤트: 웹 페이지 로드 시 실행되는 스크립트 ## 개요 `onload` 이벤트는 웹 페이지가 완전히 로드된 후 특정 작업을 수행하기 위해 사용되는 JavaScript 이벤트입니다. 이 이벤트는 이미지, CSS, JavaScript...
Meta Keywords: onload, html, 페이지가, body, 이벤트는
-->

# JavaScript의 onload 이벤트: 웹 페이지 로드 시 실행되는 스크립트

## 개요
`onload` 이벤트는 웹 페이지가 완전히 로드된 후 특정 작업을 수행하기 위해 사용되는 JavaScript 이벤트입니다. 이 이벤트는 이미지, CSS, JavaScript 파일 등 모든 리소스가 로드된 후에 발생합니다.

## 문서화
### 목적
`onload`는 웹 페이지의 모든 요소가 로드된 후에 실행되는 코드를 작성할 수 있게 해줍니다. 페이지가 로드될 때 초기화 작업이나 사용자 인터페이스 설정 작업을 수행하는 데 유용합니다.

### 사용법
`onload` 이벤트는 주로 `<body>` 태그에 사용되거나 JavaScript에서 `window.onload` 속성을 설정하여 사용할 수 있습니다. 두 가지 주요 사용 방법은 다음과 같습니다.

1. HTML 태그에 직접 사용:
   ```html
   <body onload="myFunction()">
   ```

2. JavaScript에서 설정:
   ```javascript
   window.onload = function() {
     // Your code here
     myFunction();
   };
   ```

## 예제
### HTML 태그에 onload 사용하기
```html
<!DOCTYPE html>
<html>
<head>
    <title>onload 예제</title>
</head>
<body onload="alert('페이지가 로드되었습니다!');">
    <h1>환영합니다!</h1>
</body>
</html>
```

### JavaScript에서 onload 사용하기
```html
<!DOCTYPE html>
<html>
<head>
    <title>onload 예제</title>
    <script>
        window.onload = function() {
            console.log('페이지가 로드되었습니다!');
        };
    </script>
</head>
<body>
    <h1>환영합니다!</h1>
</body>
</html>
```

## 설명
- `onload` 이벤트는 페이지가 완전히 로드된 후에 실행되므로, DOM 요소에 접근할 때 유용합니다. 하지만 `onload`를 사용할 때 몇 가지 주의해야 할 점이 있습니다.
- 여러 개의 `onload` 핸들러를 설정할 경우, 이전 핸들러가 덮어씌워질 수 있습니다. 이를 방지하려면 `addEventListener`를 사용하는 것이 좋습니다.
- `onload`는 이미지나 프레임 등 특정 리소스의 로드 상태에 따라 다르게 작동할 수 있습니다. 이 때문에, 특정 리소스가 로드되지 않으면 `onload` 이벤트가 발생하지 않을 수 있습니다.

## 한 줄 요약
`onload` 이벤트는 웹 페이지가 완전히 로드된 후에 특정 JavaScript 코드를 실행하는 데 사용됩니다.