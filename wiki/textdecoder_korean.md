<!--
Meta Description: # TextDecoder: 자바스크립트에서 텍스트 디코딩의 모든 것 ## 개요 `TextDecoder`는 자바스크립트에서 다양한 문자 인코딩을 사용하여 바이트 데이터를 문자열로 변환하는 데 사용되는 내장 객체입니다. 주로 웹 애플리케이션에서 네트워크 요청이나 파일 처리...
Meta Keywords: textdecoder, 인코딩, const, decoder, new
-->

# TextDecoder: 자바스크립트에서 텍스트 디코딩의 모든 것

## 개요
`TextDecoder`는 자바스크립트에서 다양한 문자 인코딩을 사용하여 바이트 데이터를 문자열로 변환하는 데 사용되는 내장 객체입니다. 주로 웹 애플리케이션에서 네트워크 요청이나 파일 처리 시 유용합니다.

## 문서화

### 목적
`TextDecoder`는 주어진 인코딩 형식에 따라 바이트 시퀀스를 문자열로 변환할 수 있도록 설계되었습니다. 이 객체는 주로 `ArrayBuffer` 또는 `TypedArray`와 함께 사용되어 비 ASCII 문자 및 다양한 언어의 텍스트를 올바르게 디코딩합니다.

### 사용법
`TextDecoder`는 기본 생성자를 사용하여 인스턴스를 생성할 수 있습니다.

```javascript
const decoder = new TextDecoder(encoding, options);
```

- **encoding**: 디코딩할 문자 인코딩 형식입니다. 예: "utf-8", "iso-8859-2", "windows-1252" 등.
- **options** (선택사항): `fatal` (boolean) 및 `ignoreBOM` (boolean) 속성을 포함할 수 있는 객체입니다.

### 메서드
- **decode()**: `decode()` 메서드는 주어진 `ArrayBuffer` 또는 `TypedArray`를 문자열로 변환합니다.

```javascript
const result = decoder.decode(input, options);
```

- **input**: 디코딩할 바이트 데이터입니다.
- **options** (선택사항): `stream` 속성이 포함될 수 있습니다.

## 예제

### 기본 사용 예제

```javascript
const buffer = new Uint8Array([72, 101, 108, 108, 111]);
const decoder = new TextDecoder('utf-8');
const text = decoder.decode(buffer);

console.log(text); // "Hello"
```

### 다양한 인코딩 사용

```javascript
const buffer = new Uint8Array([0xe3, 0x81, 0x82, 0xe3, 0x81, 0x84]); // "あ"
const decoder = new TextDecoder('utf-8');
const text = decoder.decode(buffer);

console.log(text); // "あ"
```

## 설명
`TextDecoder` 사용 시 주의해야 할 점은 다음과 같습니다.

1. **인코딩 형식의 일치**: 디코딩할 데이터의 인코딩 형식과 `TextDecoder`에 지정한 인코딩 형식이 일치해야 합니다. 그렇지 않으면 잘못된 문자열이 생성될 수 있습니다.
2. **비동기 처리**: 네트워크 요청이나 파일 읽기와 같이 비동기적으로 데이터를 가져오는 경우, 데이터가 완전히 수신된 후에 디코딩해야 합니다.
3. **지원되는 인코딩**: 모든 브라우저가 모든 인코딩을 지원하는 것은 아닙니다. 최신 브라우저에서 지원하는 인코딩 형식을 확인하는 것이 좋습니다.

## 한 줄 요약
`TextDecoder`는 다양한 문자 인코딩을 사용하여 바이트 데이터를 문자열로 변환하는 자바스크립트의 내장 객체입니다.