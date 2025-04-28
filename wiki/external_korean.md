<!--
Meta Description: # JavaScript의 "external": 외부 스크립트와 관련된 기능 ## 개요 JavaScript에서 "external"은 외부 JavaScript 파일을 HTML 문서에 연결하는 방법을 설명합니다. 이를 통해 코드의 재사용성을 높이고, 웹 페이지의 로딩 속도를...
Meta Keywords: html, script, src, external, javascript
-->

# JavaScript의 "external": 외부 스크립트와 관련된 기능

## 개요
JavaScript에서 "external"은 외부 JavaScript 파일을 HTML 문서에 연결하는 방법을 설명합니다. 이를 통해 코드의 재사용성을 높이고, 웹 페이지의 로딩 속도를 개선할 수 있습니다.

## 문서화
### 목적
"external" 스크립트는 HTML 문서와 별도로 존재하는 JavaScript 파일을 사용하여 페이지의 기능을 확장할 수 있게 합니다. 이를 통해 코드의 구조를 깔끔하게 유지하고, 여러 HTML 파일에서 동일한 스크립트를 재사용할 수 있습니다.

### 사용법
외부 JavaScript 파일을 HTML에 포함시키려면 `<script>` 태그의 `src` 속성을 사용합니다. 아래는 기본적인 문법입니다:

```html
<script src="path/to/your/script.js"></script>
```

### 세부사항
- **파일 경로**: `src` 속성에는 외부 JavaScript 파일의 경로를 지정해야 합니다. 이 경로는 절대 경로 또는 상대 경로일 수 있습니다.
- **비동기 및 지연 로딩**: `<script>` 태그에 `async` 또는 `defer` 속성을 추가하여 스크립트의 로딩 방식을 조절할 수 있습니다.
  - `async`: 스크립트를 비동기적으로 로드하며, 페이지의 나머지 요소들이 로드되는 동안 실행됩니다.
  - `defer`: 스크립트를 비동기적으로 로드하되, HTML 문서가 완전히 파싱된 후에 실행됩니다.

## 예제
### 기본 사용 예
HTML 문서에 외부 JavaScript 파일을 포함하는 가장 간단한 방법은 다음과 같습니다:

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>External Script Example</title>
    <script src="script.js"></script>
</head>
<body>
    <h1>안녕하세요!</h1>
</body>
</html>
```

### 비동기 및 지연 로딩 예
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>External Script Async and Defer</title>
    <script src="script.js" async></script>
    <script src="script2.js" defer></script>
</head>
<body>
    <h1>안녕하세요!</h1>
</body>
</html>
```

## 설명
외부 스크립트를 사용할 때의 일반적인 문제는 다음과 같습니다:
- **경로 오류**: `src` 속성에 지정된 경로가 잘못되면 스크립트가 로드되지 않습니다. 경로를 항상 확인해야 합니다.
- **스크립트 순서**: 여러 개의 외부 스크립트를 포함할 때, 스크립트의 실행 순서가 중요할 수 있습니다. `defer` 속성을 사용하면 순서를 보장할 수 있습니다.
- **브라우저 호환성**: 일부 오래된 브라우저에서는 `async`와 `defer` 속성이 제대로 지원되지 않을 수 있으므로, 사용자 기반에 따라 확인이 필요합니다.

## 한 줄 요약
JavaScript의 "external"은 외부 JavaScript 파일을 HTML 문서에 연결하여 코드의 재사용성을 높이고 페이지 로딩 속도를 개선하는 기능입니다.