<!--
Meta Description: # DataTransferItem: 자바스크립트에서의 사용법과 예제 ## 개요 `DataTransferItem`은 HTML5의 Drag and Drop API의 일부로, 드래그 앤 드롭 작업 중에 데이터 항목을 표현하는 객체입니다. 이 객체는 드래그된 데이터의 유형과 ...
Meta Keywords: datatransferitem, items, file, event, item
-->

# DataTransferItem: 자바스크립트에서의 사용법과 예제

## 개요
`DataTransferItem`은 HTML5의 Drag and Drop API의 일부로, 드래그 앤 드롭 작업 중에 데이터 항목을 표현하는 객체입니다. 이 객체는 드래그된 데이터의 유형과 내용을 정의하며, 클립보드와의 상호작용에서도 사용됩니다.

## 문서화
### 목적
`DataTransferItem` 객체는 드래그 앤 드롭 이벤트에서 전송되는 데이터 항목을 관리하고 조작하는 데 사용됩니다. 이를 통해 개발자는 사용자가 드래그한 요소의 정보를 쉽게 접근하고 처리할 수 있습니다.

### 사용법
`DataTransferItem`은 `DataTransfer` 객체의 `items` 속성을 통해 접근할 수 있으며, 이 속성은 `DataTransferItemList` 객체를 반환합니다. 각 `DataTransferItem`은 파일, URL, 텍스트 등의 다양한 유형을 지원합니다.

### 주요 속성과 메서드
- **`kind`**: 항목의 종류를 나타냅니다. (예: `file`, `string`)
- **`type`**: 항목의 MIME 유형을 반환합니다.
- **`getAsFile()`**: 항목이 파일일 경우, 해당 파일 객체를 반환합니다.
- **`getAsString()`**: 항목이 문자열일 경우, 해당 문자열을 반환하는 메서드입니다.

### 사용 예
```javascript
document.addEventListener('drop', function(event) {
    event.preventDefault();
    const items = event.dataTransfer.items;

    for (let i = 0; i < items.length; i++) {
        const item = items[i];

        if (item.kind === 'file') {
            const file = item.getAsFile();
            console.log('File name: ' + file.name);
        } else if (item.kind === 'string') {
            item.getAsString(function(str) {
                console.log('Dropped string: ' + str);
            });
        }
    }
});
```

## 설명
### 일반적인 실수 및 주의사항
- **이벤트 처리기에서의 `event.preventDefault()` 호출**: 드롭 이벤트가 발생했을 때, 기본 동작을 방지하기 위해 `event.preventDefault()`를 호출해야 합니다. 그렇지 않으면 드롭이 발생하지 않습니다.
- **비동기 처리**: `getAsString` 메서드는 비동기적으로 동작하므로, 콜백 내에서 값을 사용해야 합니다. 이 점을 간과하면 예상치 못한 결과를 초래할 수 있습니다.
- **지원 브라우저 확인**: `DataTransferItem` API는 모든 브라우저에서 지원되지 않을 수 있으므로, 브라우저 호환성을 확인하는 것이 중요합니다.

## 한 줄 요약
`DataTransferItem`은 드래그 앤 드롭 작업 중 데이터를 표현하고 조작하는 데 사용되는 자바스크립트 객체입니다.