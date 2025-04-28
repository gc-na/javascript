<!--
Meta Description: # XMLHttpRequest: 자바스크립트에서의 비동기 HTTP 요청 ## 개요 `XMLHttpRequest`는 자바스크립트에서 비동기 HTTP 요청을 수행할 수 있게 해주는 객체입니다. 이를 통해 웹 페이지가 서버와 데이터를 교환하고, 페이지를 새로 고치지 않고도 ...
Meta Keywords: xhr, xmlhttprequest, 요청을, javascript, 있습니다
-->

# XMLHttpRequest: 자바스크립트에서의 비동기 HTTP 요청

## 개요
`XMLHttpRequest`는 자바스크립트에서 비동기 HTTP 요청을 수행할 수 있게 해주는 객체입니다. 이를 통해 웹 페이지가 서버와 데이터를 교환하고, 페이지를 새로 고치지 않고도 동적으로 내용을 업데이트할 수 있습니다.

## 문서화
`XMLHttpRequest` 객체는 웹 브라우저에서 서버와의 통신을 위한 API입니다. 이 객체를 사용하면 서버에 데이터 요청을 보내고, 응답을 받을 수 있습니다. 주로 AJAX(Asynchronous JavaScript and XML) 요청에 활용되며, JSON, XML, HTML 등의 형식으로 데이터를 주고받을 수 있습니다.

### 사용법
1. **객체 생성**: `XMLHttpRequest` 객체를 생성합니다.
   ```javascript
   var xhr = new XMLHttpRequest();
   ```

2. **요청 초기화**: `open()` 메소드를 사용해 요청을 초기화합니다.
   ```javascript
   xhr.open('GET', 'https://api.example.com/data', true);
   ```

3. **요청 보내기**: `send()` 메소드를 사용해 요청을 보냅니다.
   ```javascript
   xhr.send();
   ```

4. **응답 처리**: `onreadystatechange` 이벤트 핸들러를 설정하여 응답을 처리합니다.
   ```javascript
   xhr.onreadystatechange = function() {
       if (xhr.readyState === 4 && xhr.status === 200) {
           console.log(xhr.responseText);
       }
   };
   ```

### 주요 속성과 메소드
- **readyState**: 요청의 현재 상태를 나타냅니다.
- **status**: HTTP 응답 상태 코드를 반환합니다.
- **responseText**: 서버에서 반환된 응답 텍스트를 포함합니다.
- **open(method, url, async)**: 요청을 초기화합니다.
- **send(data)**: 요청을 서버로 보냅니다.
- **setRequestHeader(header, value)**: 요청 헤더를 설정합니다.

## 예제
### 기본 GET 요청
```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

### POST 요청 예제
```javascript
var xhr = new XMLHttpRequest();
xhr.open('POST', 'https://api.example.com/data', true);
xhr.setRequestHeader('Content-Type', 'application/json;charset=UTF-8');
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log('Response:', xhr.responseText);
    }
};
xhr.send(JSON.stringify({ key: 'value' }));
```

## 설명
`XMLHttpRequest`를 사용할 때 주의해야 할 점은 비동기 요청의 특성으로 인해 응답을 받을 때까지 코드를 계속 실행한다는 것입니다. 따라서 응답이 오기 전에 데이터를 접근하려 하면 오류가 발생할 수 있습니다. 또한, CORS(Cross-Origin Resource Sharing) 정책에 따라 다른 도메인에서 요청을 보낼 경우 서버에서 올바른 CORS 헤더를 설정해야만 요청이 성공합니다.

또한, `XMLHttpRequest`는 비동기 처리를 위한 콜백 패턴을 사용하므로, 복잡한 요청 처리 로직에서는 가독성이 떨어질 수 있습니다. 이 때문에 최근에는 `fetch` API와 같은 현대적인 대안이 널리 사용되고 있습니다.

## 한 줄 요약
`XMLHttpRequest`는 자바스크립트에서 서버와 비동기적으로 데이터를 교환할 수 있게 해주는 객체입니다.