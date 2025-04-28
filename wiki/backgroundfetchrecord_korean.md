<!--
Meta Description: # BackgroundFetchRecord: JavaScript에서의 배경 가져오기 레코드 ## 개요 `BackgroundFetchRecord`는 웹 애플리케이션이 백그라운드에서 데이터를 비동기적으로 다운로드할 수 있도록 지원하는 API입니다. 이를 통해 사용자 경험을...
Meta Keywords: 다운로드, backgroundfetchrecord, 있습니다, fetch, 다운로드할
-->

# BackgroundFetchRecord: JavaScript에서의 배경 가져오기 레코드

## 개요
`BackgroundFetchRecord`는 웹 애플리케이션이 백그라운드에서 데이터를 비동기적으로 다운로드할 수 있도록 지원하는 API입니다. 이를 통해 사용자 경험을 향상시키고, 네트워크 상태가 불안정할 때도 파일을 원활하게 다운로드할 수 있습니다.

## 문서화
`BackgroundFetchRecord`는 `BackgroundFetch` API의 일부로, 웹 애플리케이션이 대량의 데이터를 다운로드하기 위해 설계되었습니다. 이 API를 사용하면 사용자가 페이지를 떠나도 다운로드가 지속되며, 다운로드 상태를 모니터링할 수 있습니다.

### 목적
이 API의 주요 목적은 대규모 파일을 다운로드할 때 사용자 경험을 개선하고, 웹 애플리케이션의 성능을 향상시키는 것입니다.

### 사용법
`BackgroundFetchRecord`는 `BackgroundFetch` API의 메소드와 함께 작동합니다. 사용자는 다운로드 작업을 생성하고, 이 작업의 상태를 확인하며, 다운로드가 완료된 후의 작업을 정의할 수 있습니다.

### 세부 사항
- **속성**:
  - `id`: 다운로드 작업의 고유 식별자.
  - `status`: 다운로드의 현재 상태를 나타냅니다. (예: 'pending', 'success', 'failed')
  - `uploadedBytes` 및 `downloadedBytes`: 각각 업로드 및 다운로드된 바이트 수를 나타냅니다.
  
- **메소드**:
  - `abort()`: 진행 중인 다운로드를 중단합니다.
  - `pause()`: 다운로드를 일시 중지합니다.
  - `resume()`: 일시 중지된 다운로드를 재개합니다.

## 예제
```javascript
// 배경 가져오기 작업 생성
const fetch = new BackgroundFetch('my-fetch', [
  new Request('/file1.zip'),
  new Request('/file2.zip')
], {
  start: true
});

// 작업 완료 후 처리
fetch.onprogress = (update) => {
  console.log(`다운로드 진행 상황: ${update.downloadedBytes} 바이트`);
};

fetch.onsuccess = () => {
  console.log('모든 파일 다운로드 완료');
};

fetch.onerror = () => {
  console.error('다운로드 중 오류 발생');
};
```

## 설명
`BackgroundFetchRecord`를 사용할 때 몇 가지 주의사항이 있습니다. 

1. **브라우저 호환성**: 모든 브라우저가 이 API를 지원하지 않으므로, 사용하기 전에 호환성을 확인해야 합니다.
2. **네트워크 상태**: 사용자의 네트워크 상태에 따라 다운로드 속도와 성공 여부가 달라질 수 있습니다.
3. **권한 문제**: 특정 작업을 수행하려면 사용자의 권한이 필요할 수 있으며, 이로 인해 다운로드가 실패할 수 있습니다.

## 한 줄 요약
`BackgroundFetchRecord`는 웹 애플리케이션이 백그라운드에서 비동기적으로 데이터를 다운로드할 수 있도록 도와주는 JavaScript API입니다.