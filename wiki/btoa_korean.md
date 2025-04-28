<!--
Meta Description: # JavaScript의 btoa 함수: 문자열을 Base64로 인코딩하는 방법 ## 개요 `btoa` 함수는 JavaScript에서 문자열을 Base64로 인코딩하는 데 사용됩니다. 이 함수는 주로 데이터 전송 시 이진 데이터를 안전하게 문자열로 변환할 필요가 있을 ...
Meta Keywords: btoa, 문자열을, 함수는, ascii, utf
-->

# JavaScript의 btoa 함수: 문자열을 Base64로 인코딩하는 방법

## 개요
`btoa` 함수는 JavaScript에서 문자열을 Base64로 인코딩하는 데 사용됩니다. 이 함수는 주로 데이터 전송 시 이진 데이터를 안전하게 문자열로 변환할 필요가 있을 때 사용됩니다.

## 문서화
### 목적
`btoa` 함수는 ASCII 문자열을 Base64 형식으로 인코딩합니다. Base64는 이진 데이터를 ASCII 문자열로 변환하는 인코딩 방식으로, 웹에서 안전하게 데이터를 전송할 수 있게 도와줍니다.

### 사용법
`btoa` 함수는 다음과 같은 형식으로 사용됩니다:

```javascript
btoa(string);
```

- **string**: 인코딩할 ASCII 문자열입니다. 이 문자열은 반드시 ASCII 문자로 구성되어야 하며, UTF-8 인코딩된 문자열을 직접 사용할 경우 오류가 발생합니다.

### 반환 값
`btoa` 함수는 입력된 문자열을 Base64로 인코딩한 결과를 반환합니다.

## 예제
기본적인 사용 예는 다음과 같습니다:

```javascript
// 단순 문자열 인코딩
const encoded = btoa("Hello, World!");
console.log(encoded); // SGVsbG8sIFdvcmxkIQ==
```

UTF-8 문자열을 인코딩할 경우, 먼저 UTF-8로 변환해야 합니다:

```javascript
// UTF-8 문자열 인코딩
const utf8String = "안녕하세요";
const encodedUtf8 = btoa(unescape(encodeURIComponent(utf8String)));
console.log(encodedUtf8); // 7JWI64WV7ZWY
```

## 설명
`btoa` 함수 사용 시 주의해야 할 점은 입력 문자열이 ASCII 문자로만 이루어져 있어야 한다는 것입니다. 만약 비ASCII 문자가 포함된 문자열을 입력하면 `DOMException`이 발생합니다. 따라서, UTF-8 문자열을 인코딩할 때는 `encodeURIComponent`와 `unescape`를 조합하여 사용해야 합니다.

### 일반적인 문제
- **비ASCII 문자 처리**: `btoa` 함수는 ASCII 문자만 지원하므로, 비ASCII 문자는 오류를 발생시킵니다. 이를 방지하기 위해 UTF-8로 변환 후 인코딩해야 합니다.
- **특수 문자**: 특수 문자가 포함된 문자열 또한 문제를 일으킬 수 있습니다. 이런 경우에는 적절한 인코딩 절차를 따르는 것이 중요합니다.

## 한 줄 요약
`btoa` 함수는 ASCII 문자열을 Base64로 인코딩하는 JavaScript 내장 함수입니다.