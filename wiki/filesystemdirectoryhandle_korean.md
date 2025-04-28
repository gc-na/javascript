<!--
Meta Description: # FileSystemDirectoryHandle: 자바스크립트의 파일 시스템 API ## 개요 `FileSystemDirectoryHandle`는 자바스크립트의 파일 시스템 API의 일부로, 사용자가 파일 시스템에서 디렉토리를 나타내고 조작할 수 있도록 합니다. 이 ...
Meta Keywords: await, filesystemdirectoryhandle, dirhandle, 사용자가, api는
-->

# FileSystemDirectoryHandle: 자바스크립트의 파일 시스템 API

## 개요
`FileSystemDirectoryHandle`는 자바스크립트의 파일 시스템 API의 일부로, 사용자가 파일 시스템에서 디렉토리를 나타내고 조작할 수 있도록 합니다. 이 API는 웹 애플리케이션이 로컬 파일 시스템과 상호작용할 수 있도록 하여, 파일과 폴더를 쉽게 관리할 수 있게 돕습니다.

## 문서화

### 목적
`FileSystemDirectoryHandle`는 사용자가 로컬 디렉토리에 접근하고 파일을 읽고 쓸 수 있도록 하며, 이를 통해 웹 애플리케이션 내에서 파일 작업을 할 수 있는 기능을 제공합니다. 이 API는 사용자에게 파일 시스템에 대한 더 많은 제어 권한을 부여합니다.

### 사용법
`FileSystemDirectoryHandle`는 일반적으로 `showDirectoryPicker()` 메서드와 함께 사용됩니다. 이 메서드는 사용자가 선택한 디렉토리의 핸들을 반환하고, 이를 통해 디렉토리 내의 파일 및 서브디렉토리에 접근할 수 있습니다.

### 주요 기능
- 디렉토리 생성, 삭제, 이름 변경
- 서브디렉토리 및 파일 탐색
- 파일 메타데이터 접근

## 예제

### 기본 사용 예제
```javascript
async function openDirectory() {
    const dirHandle = await window.showDirectoryPicker();
    console.log('선택된 디렉토리:', dirHandle.name);
    
    // 서브디렉토리 및 파일 탐색
    for await (const entry of dirHandle.values()) {
        console.log(entry.name, entry.kind); // entry.kind는 'directory' 또는 'file'입니다.
    }
}

openDirectory().catch(console.error);
```

### 파일 추가 예제
```javascript
async function createFileInDirectory(dirHandle) {
    const fileHandle = await dirHandle.getFileHandle('example.txt', { create: true });
    const writableStream = await fileHandle.createWritable();
    await writableStream.write('안녕하세요, 파일 시스템!');
    await writableStream.close();
}
```

## 설명
`FileSystemDirectoryHandle`을 사용할 때 주의해야 할 점은 다음과 같습니다:

- **사용자 권한**: API를 사용할 때는 항상 사용자의 권한을 요청해야 하며, 사용자가 디렉토리를 선택하지 않으면 오류가 발생합니다.
- **비동기 처리**: 이 API는 비동기 처리 패턴을 따르므로, `async/await` 또는 `.then()`을 사용하여 반환 값을 처리해야 합니다.
- **브라우저 지원**: 현재 이 API는 모든 브라우저에서 지원되지 않으므로, 사용하기 전에 호환성을 확인해야 합니다.

## 한 줄 요약
`FileSystemDirectoryHandle`은 자바스크립트를 통해 웹 애플리케이션이 로컬 파일 시스템의 디렉토리에 접근하고 조작할 수 있게 해주는 API입니다.