<!--
Meta Description: # XMLHttpRequestUpload: JavaScript를 통한 파일 업로드 최적화 ## 개요 `XMLHttpRequestUpload`는 JavaScript에서 파일 업로드를 처리하기 위한 객체로, 파일 업로드 과정에서 발생하는 이벤트를 다룰 수 있도록 지원합니다...
Meta Keywords: 업로드, 있습니다, upload, xmlhttprequestupload, const
-->

# XMLHttpRequestUpload: JavaScript를 통한 파일 업로드 최적화

## 개요
`XMLHttpRequestUpload`는 JavaScript에서 파일 업로드를 처리하기 위한 객체로, 파일 업로드 과정에서 발생하는 이벤트를 다룰 수 있도록 지원합니다. 이 객체는 `XMLHttpRequest`와 함께 사용되며, 파일을 서버로 전송하는 동안의 진행 상황을 모니터링하고, 상태 변화에 대한 콜백을 설정할 수 있습니다.

## 문서
### 목적
`XMLHttpRequestUpload`는 웹 애플리케이션에서 파일 업로드 시 사용자에게 피드백을 제공하는 데 필요한 기능을 제공합니다. 이 객체를 사용하면 파일 업로드의 진행 상황, 완료 상태 및 오류를 관리할 수 있습니다.

### 사용법
`XMLHttpRequestUpload` 객체는 `XMLHttpRequest` 인스턴스를 통해 접근할 수 있습니다. 사용자는 `onprogress`, `onload`, `onerror`와 같은 이벤트 리스너를 설정하여 파일 업로드의 상태를 모니터링할 수 있습니다.

#### 기본 사용법
1. `XMLHttpRequest` 객체 생성
2. `XMLHttpRequestUpload` 객체 접근
3. 이벤트 리스너 설정
4. 파일 업로드 수행

### 상세 설명
`XMLHttpRequestUpload`는 다음과 같은 주요 이벤트를 지원합니다:
- `onload`: 파일 업로드가 완료되었을 때 호출됩니다.
- `onerror`: 업로드 중 오류가 발생했을 때 호출됩니다.
- `onprogress`: 업로드 진행 상황을 나타내며, 현재 전송된 바이트 수와 전체 바이트 수를 제공합니다.

## 예제
### 기본 파일 업로드 예제
```javascript
// HTML 파일 입력 요소
const fileInput = document.getElementById('fileInput');
const uploadButton = document.getElementById('uploadButton');
const progressBar = document.getElementById('progressBar');

uploadButton.addEventListener('click', () => {
    const file = fileInput.files[0];
    const xhr = new XMLHttpRequest();
    const upload = xhr.upload;
    
    // 이벤트 리스너 설정
    upload.addEventListener('progress', (event) => {
        if (event.lengthComputable) {
            const percentComplete = (event.loaded / event.total) * 100;
            progressBar.value = percentComplete;
            console.log(`Uploaded ${percentComplete}%`);
        }
    });

    upload.addEventListener('load', () => {
        console.log('Upload complete!');
    });

    upload.addEventListener('error', () => {
        console.error('Upload failed.');
    });

    xhr.open('POST', '/upload', true);
    xhr.send(new FormData().append('file', file));
});
```

## 설명
- **파일 선택**: 사용자가 파일 입력 요소를 통해 선택한 파일이 `fileInput`에 담깁니다.
- **업로드 진행률**: `onprogress` 이벤트를 통해 파일 업로드의 진행률을 실시간으로 업데이트합니다. 이때 `event.lengthComputable`을 사용하여 전체 파일 크기를 확인할 수 있습니다.
- **오류 처리**: `onerror` 이벤트를 통해 업로드 실패 시 적절한 조치를 취할 수 있습니다.

### 일반적인 문제
- **CORS 오류**: 파일 업로드를 다른 도메인으로 전송할 경우 CORS(Cross-Origin Resource Sharing) 정책에 따라 오류가 발생할 수 있습니다. 이 경우 서버에서 적절한 CORS 헤더를 설정해야 합니다.
- **파일 크기 제한**: 서버에서 설정한 파일 크기 제한을 초과하면 업로드가 실패할 수 있습니다. 이를 사전에 사용자에게 안내하는 것이 좋습니다.

## 한 줄 요약
`XMLHttpRequestUpload`는 JavaScript에서 파일 업로드 진행 상황을 모니터링하고 처리하는 객체입니다.