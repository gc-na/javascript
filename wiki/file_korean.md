<!--
Meta Description: # JavaScript에서 파일(File) 객체 이해하기 ## 개요 JavaScript에서 파일(File) 객체는 웹 애플리케이션이 로컬 파일 시스템의 파일에 접근할 수 있도록 해주는 중요한 기능입니다. 이 객체는 HTML5의 File API의 일환으로 도입되어, 사용...
Meta Keywords: file, firstfile, files, 객체는, 사용자가
-->

# JavaScript에서 파일(File) 객체 이해하기

## 개요
JavaScript에서 파일(File) 객체는 웹 애플리케이션이 로컬 파일 시스템의 파일에 접근할 수 있도록 해주는 중요한 기능입니다. 이 객체는 HTML5의 File API의 일환으로 도입되어, 사용자가 파일을 업로드하거나 다운로드할 때 유용하게 사용됩니다.

## 문서화

### 목적
File 객체는 브라우저 내에서 사용자가 선택한 파일의 정보를 담고 있으며, 해당 파일의 이름, 크기, MIME 타입 등을 제공하여 프로그래밍적으로 파일을 처리할 수 있도록 합니다. 이 객체는 주로 `<input type="file">` 요소와 함께 사용됩니다.

### 사용법
File 객체는 사용자가 파일을 선택할 때 생성됩니다. 일반적으로 `input` 요소의 `files` 속성을 통해 접근할 수 있습니다.

```html
<input type="file" id="fileInput">
```

JavaScript를 사용하여 파일 정보를 가져올 수 있습니다:

```javascript
document.getElementById('fileInput').addEventListener('change', function(event) {
    const files = event.target.files; // FileList 객체
    const firstFile = files[0]; // 첫 번째 파일
    
    console.log('파일 이름:', firstFile.name); // 파일 이름
    console.log('파일 크기:', firstFile.size); // 파일 크기 (바이트)
    console.log('파일 타입:', firstFile.type); // MIME 타입
});
```

## 예제
다음은 사용자가 파일을 선택하고, 선택된 파일의 정보를 출력하는 간단한 예제입니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>File 객체 예제</title>
</head>
<body>
    <input type="file" id="fileInput">
    <script>
        document.getElementById('fileInput').addEventListener('change', function(event) {
            const files = event.target.files;
            const firstFile = files[0];

            if (firstFile) {
                console.log('파일 이름:', firstFile.name);
                console.log('파일 크기:', firstFile.size);
                console.log('파일 타입:', firstFile.type);
            }
        });
    </script>
</body>
</html>
```

## 설명
File 객체를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **브라우저 호환성**: 모든 브라우저가 File API를 완벽하게 지원하지 않을 수 있으므로, 주요 브라우저에서 테스트하는 것이 좋습니다.
- **파일 크기 제한**: 파일 업로드 시, 사용자가 선택할 수 있는 파일의 크기에는 제한이 있을 수 있습니다. 서버 측에서도 이를 검증해야 합니다.
- **보안 정책**: JavaScript는 보안상의 이유로 로컬 파일 시스템에 직접 접근할 수 없으므로, 사용자의 명시적인 파일 선택이 필요합니다.

## 한 줄 요약
JavaScript의 File 객체는 사용자가 선택한 파일에 대한 정보를 제공하며, 웹 애플리케이션에서 파일 처리에 필수적인 요소입니다.