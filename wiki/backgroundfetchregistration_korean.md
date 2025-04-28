<!--
Meta Description: # BackgroundFetchRegistration: JavaScript에서의 배경 가져오기 등록 ## 개요 `BackgroundFetchRegistration`은 JavaScript의 Fetch API의 일부로, 백그라운드에서 대용량 파일 다운로드를 관리할 수 있는...
Meta Keywords: backgroundfetchregistration, 다운로드, 사용자가, fetch, 다운로드를
-->

# BackgroundFetchRegistration: JavaScript에서의 배경 가져오기 등록

## 개요
`BackgroundFetchRegistration`은 JavaScript의 Fetch API의 일부로, 백그라운드에서 대용량 파일 다운로드를 관리할 수 있는 기능을 제공합니다. 이 API는 웹 애플리케이션이 사용자가 웹 페이지를 떠나더라도 데이터를 지속적으로 다운로드할 수 있도록 해줍니다.

## 문서화
`BackgroundFetchRegistration`은 사용자가 웹 애플리케이션을 사용할 때, 대용량 파일을 백그라운드에서 다운로드하는 기능을 제공합니다. 이 기능은 사용자가 다른 페이지로 이동하거나 웹 브라우저를 종료해도 다운로드가 계속 진행되도록 합니다.

### 목적
- 사용자가 웹 페이지를 이동하더라도 파일 다운로드가 중단되지 않도록 보장합니다.
- 대량의 데이터 다운로드를 효율적으로 처리할 수 있는 방법을 제공합니다.

### 사용법
`BackgroundFetchRegistration`은 `BackgroundFetch` API를 통해 생성됩니다. 사용자는 `BackgroundFetch.fetch()` 메서드를 호출하여 다운로드 작업을 시작할 수 있습니다. 이 작업은 `BackgroundFetchRegistration` 객체를 반환합니다.

### 주요 속성 및 메서드
- `id`: 다운로드 작업의 고유 ID.
- `status`: 다운로드의 현재 상태 (예: "pending", "downloading", "complete", "failed").
- `uploadedBytes`: 업로드된 바이트 수.
- `downloadedBytes`: 다운로드된 바이트 수.
- `abort()`: 현재 다운로드 작업을 중단합니다.

## 예제
```javascript
const registration = await BackgroundFetch.fetch("my-fetch", [
    new Request("https://example.com/large-file.zip"),
]);

registration.onprogress = (progress) => {
    console.log(`다운로드 중: ${progress.downloadedBytes} 바이트`);
};

registration.onsuccess = () => {
    console.log("다운로드 완료!");
};

registration.onerror = () => {
    console.error("다운로드 실패!");
};
```

## 설명
`BackgroundFetchRegistration`을 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **브라우저 지원**: 이 API는 모든 브라우저에서 지원되지 않습니다. 현재 Chrome과 일부 Chromium 기반 브라우저에서만 사용할 수 있으므로, 사용 전에 호환성을 확인해야 합니다.
- **사용자 권한**: 백그라운드 다운로드를 시작하기 위해서는 사용자의 명시적인 허가가 필요합니다.
- **상태 관리**: 다운로드의 상태를 효과적으로 관리하기 위해 이벤트 핸들러를 사용하는 것이 좋습니다. `onprogress`, `onsuccess`, `onerror` 이벤트를 통해 다운로드의 진행 상황을 추적할 수 있습니다.

## 한 줄 요약
`BackgroundFetchRegistration`은 JavaScript에서 사용자가 페이지를 떠나도 대용량 파일 다운로드를 지속적으로 관리할 수 있는 기능을 제공합니다.