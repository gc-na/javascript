<!--
Meta Description: # JavaScript의 location 객체 완벽 가이드 ## 개요 JavaScript의 `location` 객체는 현재 문서의 URL을 포함한 정보를 제공하며, 브라우저에서 URL을 조작하고 탐색하는 데 사용됩니다. ## 문서화 `location` 객체는 `wind...
Meta Keywords: location, url을, 페이지를, url, 있습니다
-->

# JavaScript의 location 객체 완벽 가이드

## 개요
JavaScript의 `location` 객체는 현재 문서의 URL을 포함한 정보를 제공하며, 브라우저에서 URL을 조작하고 탐색하는 데 사용됩니다.

## 문서화
`location` 객체는 `window` 객체의 속성으로, 사용자가 현재 보고 있는 문서의 URL 정보를 담고 있습니다. `location` 객체를 통해 URL의 다양한 구성 요소에 접근하고, URL을 변경하거나 페이지를 새로 고치는 등의 작업을 수행할 수 있습니다. 

### 목적
- 현재 페이지의 URL 정보를 조회하고 조작할 수 있습니다.
- 페이지 이동 및 새로 고침 기능을 제공합니다.

### 사용법
`location` 객체는 다음과 같은 주요 속성과 메서드를 포함합니다:
- **속성**
  - `href`: 전체 URL을 나타냅니다.
  - `protocol`: URL의 프로토콜을 나타냅니다 (예: `http:`, `https:`).
  - `host`: 호스트 이름과 포트를 포함합니다.
  - `hostname`: 호스트 이름만 포함합니다.
  - `port`: 포트 번호를 나타냅니다.
  - `pathname`: URL의 경로 부분을 나타냅니다.
  - `search`: URL의 쿼리 문자열을 반환합니다.
  - `hash`: URL의 해시 부분을 반환합니다.

- **메서드**
  - `assign(url)`: 지정한 URL로 이동합니다.
  - `replace(url)`: 현재 문서를 지정한 URL로 대체합니다.
  - `reload()`: 페이지를 새로 고칩니다.

## 예제
```javascript
// 현재 URL을 출력합니다.
console.log(location.href);

// 프로토콜을 출력합니다.
console.log(location.protocol);

// 새로운 URL로 이동합니다.
location.assign("https://www.example.com");

// 현재 페이지를 새로 고칩니다.
location.reload();
```

## 설명
- `location` 객체의 속성을 잘못 사용하면, 잘못된 URL을 반환하거나 페이지를 잘못 이동할 수 있습니다. 
- `reload()` 메서드는 페이지를 새로 고치지만, 캐시된 버전으로 로드할 수 있으므로, 항상 최신 콘텐츠를 가져오려면 `location.reload(true)`를 사용하여 강제로 새로 고칠 수 있습니다.
- `replace()` 메서드는 현재 페이지를 새 페이지로 대체하기 때문에, 사용자가 뒤로 가기 버튼을 눌러도 이전 페이지로 돌아갈 수 없습니다.

## 한 줄 요약
JavaScript의 `location` 객체는 현재 문서의 URL 정보를 관리하고 탐색하는 데 필수적인 도구입니다.