<!--
Meta Description: # JSON: 자바스크립트에서의 활용과 이해 ## 개요 JSON(JavaScript Object Notation)은 자바스크립트에서 데이터를 교환하기 위한 경량 형식입니다. 인간이 읽고 쓰기 쉬우며 기계가 구문 분석하고 생성하기 용이합니다. ## 문서화 JSON은 자바...
Meta Keywords: json, 데이터, json은, 자바스크립트, const
-->

# JSON: 자바스크립트에서의 활용과 이해

## 개요
JSON(JavaScript Object Notation)은 자바스크립트에서 데이터를 교환하기 위한 경량 형식입니다. 인간이 읽고 쓰기 쉬우며 기계가 구문 분석하고 생성하기 용이합니다.

## 문서화
JSON은 자바스크립트의 객체 표기법을 기반으로 하며, 데이터의 구조화된 표현을 제공합니다. 주로 웹 애플리케이션에서 클라이언트와 서버 간의 데이터 전송에 사용됩니다. JSON은 텍스트 형식으로, 다른 언어에서도 쉽게 사용 가능합니다.

### 목적
- 데이터 교환: 웹 애플리케이션에서 클라이언트와 서버 간의 데이터 전송.
- 데이터 저장: 간단한 파일 형식으로 데이터 저장 및 전송.
  
### 사용법
JSON 데이터는 다음과 같은 형식을 취합니다:
- 객체: `{ "key": "value", "key2": "value2" }`
- 배열: `[ "value1", "value2", "value3" ]`

JSON은 두 가지 주요 메서드로 다루어집니다:
- `JSON.stringify()`: 자바스크립트 객체를 JSON 문자열로 변환합니다.
- `JSON.parse()`: JSON 문자열을 자바스크립트 객체로 변환합니다.

## 예제
```javascript
// 자바스크립트 객체 정의
const person = {
    name: "홍길동",
    age: 30,
    isStudent: false,
    hobbies: ["독서", "여행", "요리"]
};

// 객체를 JSON 문자열로 변환
const jsonString = JSON.stringify(person);
console.log(jsonString); // {"name":"홍길동","age":30,"isStudent":false,"hobbies":["독서","여행","요리"]}

// JSON 문자열을 자바스크립트 객체로 변환
const jsonObject = JSON.parse(jsonString);
console.log(jsonObject.name); // 홍길동
```

## 설명
JSON을 사용할 때 주의할 점은 다음과 같습니다:
- JSON의 키는 항상 문자열이어야 하며, 큰따옴표로 감싸야 합니다.
- 데이터 타입은 객체, 배열, 문자열, 숫자, 불리언, null만 지원됩니다.
- 주석을 포함할 수 없으며, 이는 JSON 형식의 제약입니다.

또한, JSON의 문자열은 UTF-8로 인코딩되어야 하며, 데이터의 크기가 클 경우 성능에 영향을 줄 수 있습니다. 따라서, 필요한 데이터만 간결하게 포함하는 것이 중요합니다.

## 한 줄 요약
JSON은 자바스크립트에서 데이터를 쉽게 교환하고 저장할 수 있는 경량 형식입니다.