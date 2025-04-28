<!--
Meta Description: # JavaScript의 헤더(Headers): HTTP 요청과 응답의 이해 ## 개요 JavaScript에서 헤더는 HTTP 요청 및 응답의 중요한 부분으로, 클라이언트와 서버 간의 데이터 교환 시 메타 정보를 전달합니다. 이러한 헤더는 API 통신, 웹 애플리케이션...
Meta Keywords: xhr, 헤더는, http, error, api
-->

# JavaScript의 헤더(Headers): HTTP 요청과 응답의 이해

## 개요
JavaScript에서 헤더는 HTTP 요청 및 응답의 중요한 부분으로, 클라이언트와 서버 간의 데이터 교환 시 메타 정보를 전달합니다. 이러한 헤더는 API 통신, 웹 애플리케이션 개발 및 보안 관리에서 필수적인 역할을 합니다.

## 문서화
헤더는 HTTP 프로토콜의 구성 요소로, 클라이언트가 서버에 요청을 보낼 때와 서버가 클라이언트에 응답을 보낼 때 사용됩니다. 각 헤더는 특정 정보를 담고 있으며, 요청의 성격이나 응답의 형식 등을 정의합니다.

### 목적
헤더의 주요 목적은 클라이언트와 서버 간의 통신을 최적화하고, 데이터 전송 시 필요한 정보(예: 콘텐츠 유형, 인증 정보 등)를 제공하는 것입니다.

### 사용법
JavaScript에서 HTTP 요청을 만들기 위해 `fetch` API 또는 `XMLHttpRequest` 객체를 사용할 수 있으며, 이 둘 모두 헤더를 설정하는 방법을 제공합니다.

- **Fetch API**:
  ```javascript
  fetch('https://api.example.com/data', {
    method: 'GET',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer YOUR_TOKEN'
    }
  })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
  ```

- **XMLHttpRequest**:
  ```javascript
  const xhr = new XMLHttpRequest();
  xhr.open('GET', 'https://api.example.com/data', true);
  xhr.setRequestHeader('Content-Type', 'application/json');
  xhr.setRequestHeader('Authorization', 'Bearer YOUR_TOKEN');
  xhr.onload = () => {
    if (xhr.status === 200) {
      console.log(JSON.parse(xhr.responseText));
    } else {
      console.error('Error:', xhr.statusText);
    }
  };
  xhr.send();
  ```

## 설명
헤더를 설정할 때 주의해야 할 점은 다음과 같습니다:

- **CORS(Cross-Origin Resource Sharing)**: 다른 출처의 API에 요청을 보낼 경우, 서버가 `Access-Control-Allow-Origin` 헤더를 설정해야 합니다. 그렇지 않으면 요청이 차단될 수 있습니다.
  
- **헤더의 대소문자**: HTTP 헤더는 대소문자를 구분하지 않지만, 일관된 스타일을 유지하는 것이 좋습니다.

- **비어 있는 값**: 일부 헤더는 비어 있는 값을 가질 수 없으므로, 적절한 값을 제공해야 합니다.

- **보안**: 민감한 정보(예: 인증 토큰)는 HTTPS를 통해 전송해야 하며, 가능하면 HTTPOnly 및 Secure 플래그를 설정한 쿠키를 사용하는 것이 좋습니다.

## 한 줄 요약
JavaScript의 헤더는 클라이언트와 서버 간의 HTTP 통신에서 메타 정보를 전달하는 필수 요소입니다.