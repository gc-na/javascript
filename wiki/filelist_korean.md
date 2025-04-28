<!--
Meta Description: # JavaScript의 FileList: 파일 목록 처리하기 ## 개요 JavaScript에서 `FileList`는 사용자가 파일을 선택할 수 있는 입력 요소와 관련된 API로, 파일의 목록을 다루는 데 사용됩니다. 이는 주로 HTML `<input type="fil...
Meta Keywords: filelist, files, html, fileinput, 파일의
-->

# JavaScript의 FileList: 파일 목록 처리하기

## 개요
JavaScript에서 `FileList`는 사용자가 파일을 선택할 수 있는 입력 요소와 관련된 API로, 파일의 목록을 다루는 데 사용됩니다. 이는 주로 HTML `<input type="file">` 요소와 함께 사용되며, 웹 애플리케이션에서 파일 업로드 기능을 구현할 때 유용합니다.

## 문서화

### 목적
`FileList` 객체는 사용자가 선택한 파일의 목록을 나타내며, 각 파일에 대한 정보(이름, 크기, 타입 등)를 포함합니다. 이 객체는 HTML 파일 입력 요소의 `files` 속성을 통해 접근할 수 있습니다.

### 사용법
`FileList`는 다음과 같이 사용됩니다:

1. HTML 파일 입력 요소 생성:
   ```html
   <input type="file" id="fileInput" multiple>
   ```

2. JavaScript를 통해 파일 목록에 접근:
   ```javascript
   const fileInput = document.getElementById('fileInput');
   fileInput.addEventListener('change', (event) => {
       const files = event.target.files; // FileList 객체
       console.log(files);
   });
   ```

### 세부사항
- `FileList` 객체는 배열과 유사하지만, `length` 속성과 인덱스를 통해 각 파일에 접근할 수 있는 점에서 다릅니다.
- 각 파일은 `File` 객체로 나타나며, 이 객체는 파일의 이름, 크기, 타입, 마지막 수정 날짜 등의 속성을 포함합니다.
- 다중 파일 선택을 지원하기 위해 `multiple` 속성을 사용해야 합니다.

## 예제

### 기본 사용 예제
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>FileList 예제</title>
</head>
<body>
    <input type="file" id="fileInput" multiple>
    <script>
        const fileInput = document.getElementById('fileInput');
        fileInput.addEventListener('change', (event) => {
            const files = event.target.files;
            for (let i = 0; i < files.length; i++) {
                console.log(`파일 이름: ${files[i].name}, 크기: ${files[i].size}바이트`);
            }
        });
    </script>
</body>
</html>
```

## 설명
- **공통 문제**: 브라우저의 보안 정책으로 인해 로컬 파일 시스템에 직접 접근할 수 없으므로, 사용자가 파일을 선택해야만 `FileList` 객체에 접근할 수 있습니다.
- **파일 크기 제한**: 사용자가 선택할 수 있는 파일의 크기와 형식은 브라우저와 설정에 따라 다를 수 있습니다. 따라서 서버 측에서도 파일 크기 및 형식을 검증하는 것이 중요합니다.
- **IE 호환성**: 모든 최신 브라우저에서 지원되지만, Internet Explorer에서는 일부 기능이 제한될 수 있습니다. 가능한 경우 최신 브라우저 사용을 권장합니다.

## 한 줄 요약
JavaScript의 `FileList`는 사용자 파일 입력 요소와 연동되어 선택된 파일의 목록을 다루는 객체입니다.