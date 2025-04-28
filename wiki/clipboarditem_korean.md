<!--
Meta Description: # ClipboardItem: 자바스크립트에서 클립보드 항목을 다루는 방법 ## 개요 `ClipboardItem`은 웹 API에서 제공하는 객체로, 클립보드에 데이터를 저장하거나 복사할 때 사용됩니다. 이 객체는 다양한 유형의 미디어 데이터를 클립보드에 추가하는 데 유...
Meta Keywords: 클립보드에, clipboarditem, 데이터를, new, const
-->

# ClipboardItem: 자바스크립트에서 클립보드 항목을 다루는 방법

## 개요
`ClipboardItem`은 웹 API에서 제공하는 객체로, 클립보드에 데이터를 저장하거나 복사할 때 사용됩니다. 이 객체는 다양한 유형의 미디어 데이터를 클립보드에 추가하는 데 유용합니다.

## 문서화
`ClipboardItem`은 사용자가 클립보드에 복사할 수 있는 항목을 생성하는 데 도움을 주는 객체입니다. 이 객체는 MIME 타입을 사용하여 다양한 형식의 데이터를 표현할 수 있으며, 주로 `Clipboard.write()` 및 `Clipboard.writeText()` 메소드와 함께 사용됩니다.

### 목적
- 클립보드에 복사할 데이터를 정의하고 설정합니다.
- 다양한 형식의 데이터를 클립보드에 저장할 수 있도록 지원합니다.

### 사용법
`ClipboardItem`은 다음과 같이 생성할 수 있습니다:

```javascript
const item = new ClipboardItem({
    'image/png': blob, // Blob 객체를 사용하여 PNG 이미지를 클립보드에 추가
    'text/plain': new Blob(['Hello, world!'], { type: 'text/plain' }) // 텍스트 데이터 추가
});
```

이렇게 생성된 `ClipboardItem`은 클립보드에 데이터를 쓰는 데 사용됩니다:

```javascript
navigator.clipboard.write([item]).then(() => {
    console.log('클립보드에 데이터가 성공적으로 쓰였습니다.');
}).catch(err => {
    console.error('클립보드에 데이터를 쓰는 중 오류 발생:', err);
});
```

## 예제
1. 이미지와 텍스트를 클립보드에 복사하기:

```javascript
const imageBlob = new Blob([/* 이미지 데이터 */], { type: 'image/png' });
const textBlob = new Blob(['안녕하세요!'], { type: 'text/plain' });

const clipboardItem = new ClipboardItem({
    'image/png': imageBlob,
    'text/plain': textBlob
});

navigator.clipboard.write([clipboardItem]).then(() => {
    console.log('이미지와 텍스트가 클립보드에 복사되었습니다.');
}).catch(err => {
    console.error('클립보드 복사 실패:', err);
});
```

2. 텍스트만 클립보드에 복사하기:

```javascript
const textBlob = new Blob(['복사할 텍스트'], { type: 'text/plain' });
const clipboardItem = new ClipboardItem({
    'text/plain': textBlob
});

navigator.clipboard.write([clipboardItem]).then(() => {
    console.log('텍스트가 클립보드에 복사되었습니다.');
}).catch(err => {
    console.error('클립보드 복사 실패:', err);
});
```

## 설명
- `ClipboardItem` 객체를 사용할 때는 MIME 타입을 정확하게 지정해야 합니다. 잘못된 MIME 타입을 사용할 경우 클립보드에 데이터가 제대로 저장되지 않을 수 있습니다.
- 이 API는 HTTPS 환경에서만 사용할 수 있으므로 로컬 파일이나 HTTP 환경에서는 사용할 수 없습니다.
- 클립보드 접근은 사용자 인터랙션(예: 클릭 이벤트) 내에서만 허용됩니다.

## 한 줄 요약
`ClipboardItem`은 다양한 형식의 데이터를 클립보드에 복사하기 위한 객체로, 웹 애플리케이션에서 클립보드 작업을 간편하게 수행할 수 있도록 돕습니다.