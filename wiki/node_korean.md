<!--
Meta Description: # Node.js: 자바스크립트를 위한 서버 사이드 실행 환경 ## 개요 Node.js는 자바스크립트를 서버 사이드에서 실행하기 위한 오픈 소스 실행 환경으로, 비동기 이벤트 기반 프로그래밍 모델을 채택하여 높은 성능과 확장성을 제공합니다. ## 문서화 Node.js는...
Meta Keywords: node, 있습니다, const, port, res
-->

# Node.js: 자바스크립트를 위한 서버 사이드 실행 환경

## 개요
Node.js는 자바스크립트를 서버 사이드에서 실행하기 위한 오픈 소스 실행 환경으로, 비동기 이벤트 기반 프로그래밍 모델을 채택하여 높은 성능과 확장성을 제공합니다.

## 문서화
Node.js는 크로스 플랫폼 JavaScript 런타임으로, Chrome의 V8 JavaScript 엔진을 기반으로 하고 있습니다. 주로 웹 서버 및 네트워크 애플리케이션을 구축하는 데 사용되며, 비동기 I/O를 통해 대량의 동시 연결을 처리할 수 있습니다. Node.js의 주요 특징은 다음과 같습니다:

- **이벤트 기반 아키텍처**: 사용자 요청에 대한 응답을 비동기적으로 처리하여 효율성을 극대화합니다.
- **npm (Node Package Manager)**: 방대한 패키지 생태계를 통해 다양한 모듈과 라이브러리를 쉽게 설치하고 사용할 수 있습니다.
- **단일 스레드**: 이벤트 루프를 사용하여 비동기 작업을 처리함으로써 메모리 사용을 최적화합니다.

### 사용법
Node.js를 사용하기 위해서는 먼저 Node.js를 설치해야 하며, 다음 명령어를 통해 애플리케이션을 실행할 수 있습니다:

1. Node.js 설치: 공식 웹사이트에서 설치 파일을 다운로드하고 설치합니다.
2. 기본 애플리케이션 생성:
   ```javascript
   // app.js
   const http = require('http');

   const hostname = '127.0.0.1';
   const port = 3000;

   const server = http.createServer((req, res) => {
     res.statusCode = 200;
     res.setHeader('Content-Type', 'text/plain');
     res.end('Hello World\n');
   });

   server.listen(port, hostname, () => {
     console.log(`서버가 http://${hostname}:${port}/ 에서 실행 중입니다.`);
   });
   ```
3. 애플리케이션 실행:
   ```bash
   node app.js
   ```

## 예제
```javascript
// 간단한 REST API 서버 예제
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('안녕하세요, Node.js!');
});

app.listen(port, () => {
  console.log(`서버가 http://localhost:${port}에서 실행되고 있습니다.`);
});
```

## 설명
Node.js를 사용할 때 주의해야 할 몇 가지 일반적인 함정은 다음과 같습니다:

- **콜백 헬**: 비동기 함수가 중첩되면서 코드가 복잡해질 수 있습니다. 이를 피하기 위해 `Promise`나 `async/await`를 활용하는 것이 좋습니다.
- **싱글 스레드 제한**: Node.js는 싱글 스레드로 작동하기 때문에 CPU 집약적인 작업을 수행할 경우 성능이 저하될 수 있습니다. 이러한 작업은 `worker threads`나 외부 프로세스에서 처리하는 것이 권장됩니다.
- **모듈 관리**: npm을 통해 패키지를 설치할 때 버전 호환성을 항상 확인해야 하며, `package.json` 파일을 통해 의존성을 관리해야 합니다.

## 한 줄 요약
Node.js는 자바스크립트를 서버 사이드에서 실행할 수 있도록 해주는 비동기 이벤트 기반 런타임 환경입니다.