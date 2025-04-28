<!--
Meta Description: # JavaScript의 FileReader: 파일 읽기 API ## 개요 JavaScript의 FileReader API는 웹 애플리케이션에서 파일 객체를 비동기적으로 읽을 수 있게 해주는 기능입니다. 이를 통해 사용자는 로컬 파일 시스템의 파일을 선택하고, 그 내용...
Meta Keywords: reader, 파일을, file, const, filereader
-->

# JavaScript의 FileReader: 파일 읽기 API

## 개요
JavaScript의 FileReader API는 웹 애플리케이션에서 파일 객체를 비동기적으로 읽을 수 있게 해주는 기능입니다. 이를 통해 사용자는 로컬 파일 시스템의 파일을 선택하고, 그 내용을 읽어들일 수 있습니다.

## 문서화
### 목적
FileReader는 사용자가 선택한 파일을 클라이언트 측에서 읽어들일 수 있도록 도와줍니다. 이 API는 이미지, 텍스트, JSON 등 다양한 형식의 파일을 처리하는 데 유용합니다.

### 사용법
FileReader는 JavaScript의 내장 객체로, 다음과 같은 메서드를 제공합니다:
- `readAsText(file)`: 파일을 텍스트로 읽습니다.
- `readAsDataURL(file)`: 파일을 데이터 URL 형식으로 변환합니다.
- `readAsArrayBuffer(file)`: 파일을 ArrayBuffer로 읽습니다.
- `readAsBinaryString(file)`: 파일을 이진 문자열로 읽습니다. (이 메서드는 더 이상 권장되지 않음)

FileReader를 사용하기 위해서는 먼저 FileReader 객체를 생성하고, 파일 선택 이벤트를 통해 파일을 전달해야 합니다.

### 세부사항
```javascript
const fileInput = document.querySelector('input[type="file"]');
const reader = new FileReader();

fileInput.addEventListener('change', (event) => {
    const file = event.target.files[0];

    reader.onload = (e) => {
        console.log(e.target.result); // 파일 내용 출력
    };

    reader.onerror = (error) => {
        console.error('파일 읽기 오류:', error);
    };

    reader.readAsText(file); // 텍스트로 파일 읽기
});
```

## 예제
### 기본 사용 예제
1. 텍스트 파일 읽기
```javascript
const inputFile = document.getElementById('fileInput');
const reader = new FileReader();

inputFile.addEventListener('change', (event) => {
    const file = event.target.files[0];
    reader.readAsText(file);
    
    reader.onload = function() {
        console.log(reader.result); // 파일 내용 출력
    };
});
```

2. 이미지 파일 읽기
```javascript
const imgInput = document.getElementById('imageInput');
const imgPreview = document.getElementById('imgPreview');
const reader = new FileReader();

imgInput.addEventListener('change', (event) => {
    const file = event.target.files[0];
    reader.readAsDataURL(file);
    
    reader.onload = function() {
        imgPreview.src = reader.result; // 미리보기 이미지 설정
    };
});
```

## 설명
- **비동기 처리**: FileReader는 비동기적으로 작동하여 파일을 읽는 동안 UI가 중단되지 않습니다.
- **파일 크기 제한**: 브라우저에 따라 파일 크기 제한이 있을 수 있으므로, 큰 파일을 처리할 때 주의해야 합니다.
- **읽기 오류 처리**: 파일 읽기 중 오류가 발생할 수 있으므로, `onerror` 이벤트 핸들러를 지정하여 오류를 처리하는 것이 좋습니다.
- **보안 제한**: 사용자가 선택한 파일만 읽을 수 있으며, 웹사이트의 서버 파일에 접근할 수 없습니다.

## 한 줄 요약
FileReader API는 JavaScript를 사용하여 클라이언트 측에서 파일을 비동기적으로 읽을 수 있게 해주는 기능입니다.