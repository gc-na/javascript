<!--
Meta Description: # JavaScript onprogress 이벤트: 진행 상황을 추적하는 방법 ## 개요 JavaScript의 `onprogress` 이벤트는 웹 애플리케이션에서 파일 다운로드, 업로드, 또는 다른 비동기 작업의 진행 상황을 추적하는 데 사용됩니다. 이 이벤트는 XML...
Meta Keywords: xhr, event, onprogress, 이벤트는, 상황을
-->

# JavaScript onprogress 이벤트: 진행 상황을 추적하는 방법

## 개요
JavaScript의 `onprogress` 이벤트는 웹 애플리케이션에서 파일 다운로드, 업로드, 또는 다른 비동기 작업의 진행 상황을 추적하는 데 사용됩니다. 이 이벤트는 XMLHttpRequest 및 Fetch API와 함께 자주 사용되며, 사용자에게 실시간 피드백을 제공할 수 있습니다.

## 문서화

### 목적
`onprogress` 이벤트는 데이터 전송 중에 발생하며, 전송된 데이터의 양을 추적하여 사용자가 진행 상황을 이해하도록 돕습니다. 이 이벤트는 사용자가 대기 시간이 긴 작업을 진행하는 동안, 그 진행 상황을 시각적으로 나타내는 데 유용합니다.

### 사용법
`onprogress` 이벤트는 주로 XMLHttpRequest 객체에서 사용됩니다. 이 이벤트는 다음과 같은 속성을 포함하는 ProgressEvent 객체를 반환합니다:

- `loaded`: 현재까지 전송된 바이트 수
- `total`: 전송해야 할 총 바이트 수

이벤트 리스너를 설정하는 방법은 다음과 같습니다:

```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "파일_경로");

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`진행 상황: ${percentComplete}%`);
    }
};

xhr.onload = function() {
    console.log("파일 다운로드 완료!");
};

xhr.send();
```

## 예제

### 기본 사용 예제
1. 파일 다운로드 진행 상황 추적:

```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "https://example.com/largefile.zip", true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`다운로드 진행 상황: ${percentComplete.toFixed(2)}%`);
    }
};

xhr.onload = function() {
    console.log("다운로드 완료!");
};

xhr.send();
```

2. 파일 업로드 진행 상황 추적:

```javascript
const formData = new FormData();
formData.append("file", fileInput.files[0]);

const xhr = new XMLHttpRequest();
xhr.open("POST", "https://example.com/upload", true);

xhr.upload.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`업로드 진행 상황: ${percentComplete.toFixed(2)}%`);
    }
};

xhr.onload = function() {
    console.log("업로드 완료!");
};

xhr.send(formData);
```

## 설명

### 일반적인 문제
- **lengthComputable 속성**: 모든 요청에서 `lengthComputable` 속성이 true로 설정되지 않을 수 있습니다. 이는 서버가 콘텐츠의 전체 길이를 알 수 없을 때 발생합니다. 이 경우 진행 상황을 계산할 수 없습니다.
  
- **호환성**: `onprogress` 이벤트는 대부분의 최신 브라우저에서 지원되지만, 구형 브라우저에서는 작동하지 않을 수 있습니다. 이를 고려하여 기능을 구현하는 것이 중요합니다.

- **UI 업데이트**: 진행 상황을 UI에 반영할 때는 성능을 고려해야 합니다. 너무 자주 업데이트하면 성능 저하가 발생할 수 있습니다. 

## 한 줄 요약
JavaScript의 `onprogress` 이벤트는 비동기 파일 전송의 진행 상황을 추적하여 사용자에게 실시간 피드백을 제공하는 방법입니다.