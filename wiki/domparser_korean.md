<!--
Meta Description: # JavaScript DOMParser: HTML 및 XML 문자열을 DOM으로 변환하는 방법 ## 개요 DOMParser는 HTML 및 XML 문자열을 Document 객체로 변환하는 JavaScript 내장 객체입니다. 이를 통해 웹 개발자는 문자열 형태로 작성된...
Meta Keywords: xml, html, 문자열을, domparser, const
-->

# JavaScript DOMParser: HTML 및 XML 문자열을 DOM으로 변환하는 방법

## 개요
DOMParser는 HTML 및 XML 문자열을 Document 객체로 변환하는 JavaScript 내장 객체입니다. 이를 통해 웹 개발자는 문자열 형태로 작성된 마크업을 손쉽게 DOM으로 변환하여 조작할 수 있습니다.

## 문서화
### 목적
DOMParser는 문자열로 표현된 HTML 또는 XML 데이터를 파싱하여 Document 객체를 생성하는 데 사용됩니다. 이를 통해 웹 페이지의 동적 생성 및 데이터 처리에 유용합니다.

### 사용법
DOMParser 객체를 생성한 후, `parseFromString` 메서드를 호출하여 문자열을 DOM으로 변환합니다. 이 메서드는 두 개의 매개변수를 받습니다:
1. `string`: 파싱할 HTML 또는 XML 문자열.
2. `contentType`: 문자열의 타입을 지정하는 MIME 타입 (예: `"text/html"` 또는 `"application/xml"`).

### 세부사항
- **지원 브라우저**: DOMParser는 대부분의 현대 웹 브라우저에서 지원됩니다.
- **에러 처리**: 잘못된 형식의 문자열을 파싱할 경우, `parseFromString` 메서드는 유효하지 않은 Document 객체를 반환할 수 있으며, 이 경우 오류 처리를 통해 사용자에게 알릴 수 있습니다.

## 예제
### HTML 문자열 파싱 예제
```javascript
const parser = new DOMParser();
const htmlString = "<div><h1>안녕하세요!</h1><p>DOMParser 예제입니다.</p></div>";
const doc = parser.parseFromString(htmlString, "text/html");

console.log(doc.body.innerHTML); // <h1>안녕하세요!</h1><p>DOMParser 예제입니다.</p>
```

### XML 문자열 파싱 예제
```javascript
const parser = new DOMParser();
const xmlString = `<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>전송</heading>
  <body>안녕하세요!</body>
</note>`;
const xmlDoc = parser.parseFromString(xmlString, "application/xml");

console.log(xmlDoc.getElementsByTagName("to")[0].textContent); // Tove
```

## 설명
- **일반적인 함정**: XML 형식의 문자열을 파싱할 때, 잘못된 XML 문법(예: 닫는 태그 누락)으로 인해 파싱 오류가 발생할 수 있습니다. 이 경우 `xmlDoc.getElementsByTagName("parsererror")`를 통해 오류 정보를 조회할 수 있습니다.
- **브라우저 호환성**: 일부 구형 브라우저에서는 DOMParser의 지원이 제한적일 수 있으므로, 지원 여부를 확인해야 합니다.
- **보안**: 외부 소스에서 가져온 HTML 문자열을 직접 파싱할 경우, XSS(교차 사이트 스크립팅) 공격에 유의해야 합니다. 신뢰할 수 없는 데이터를 처리할 때는 반드시 필터링 및 검증을 수행해야 합니다.

## 한 줄 요약
DOMParser는 HTML 및 XML 문자열을 Document 객체로 변환하여 웹 개발에서 DOM 조작을 가능하게 하는 JavaScript 내장 객체입니다.