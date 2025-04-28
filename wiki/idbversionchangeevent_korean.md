<!--
Meta Description: # IDBVersionChangeEvent: JavaScript의 인덱스DB 버전 변경 이벤트 ## 개요 `IDBVersionChangeEvent`는 인덱스DB의 데이터베이스 버전이 변경될 때 발생하는 이벤트를 나타냅니다. 이 이벤트는 데이터베이스의 구조가 변경될 때,...
Meta Keywords: event, idbversionchangeevent, 데이터베이스, request, 변경될
-->

# IDBVersionChangeEvent: JavaScript의 인덱스DB 버전 변경 이벤트

## 개요
`IDBVersionChangeEvent`는 인덱스DB의 데이터베이스 버전이 변경될 때 발생하는 이벤트를 나타냅니다. 이 이벤트는 데이터베이스의 구조가 변경될 때, 예를 들어 새로운 객체 저장소가 추가되거나 기존 저장소가 변경될 때 발생합니다.

## 문서화

### 목적
`IDBVersionChangeEvent`는 웹 애플리케이션이 인덱스DB의 버전이 변경되었음을 감지하고 이에 따라 적절한 조치를 취할 수 있도록 합니다. 이 이벤트는 주로 데이터베이스를 열거나 업데이트할 때 사용됩니다.

### 사용법
이벤트 리스너를 사용하여 `IDBVersionChangeEvent`를 감지할 수 있습니다. 이 이벤트는 데이터베이스 연결이 변경될 때 발생하며, 일반적으로 `onupgradeneeded` 이벤트와 함께 사용됩니다.

```javascript
let request = indexedDB.open("myDatabase", 2);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    // 새로운 객체 저장소 생성
    db.createObjectStore("newStore");
};

request.onsuccess = function(event) {
    let db = event.target.result;
    console.log("Database opened successfully.");
};

request.onerror = function(event) {
    console.error("Database error: " + event.target.errorCode);
};
```

### 상세 설명
`IDBVersionChangeEvent`는 인덱스DB의 버전 변경을 관리할 수 있는 중요한 이벤트입니다. 이 이벤트는 데이터베이스를 열 때 발생하며, 개발자는 이 이벤트를 통해 데이터베이스의 구조를 업데이트할 수 있습니다. `target` 프로퍼티를 통해 해당 데이터베이스와 관련된 정보를 얻을 수 있으며, `oldVersion`과 `newVersion` 속성을 통해 이전 버전과 새로운 버전을 확인할 수 있습니다.

이벤트가 발생하면 반드시 데이터베이스 스키마를 업데이트해야 하며, 이를 위해 `onupgradeneeded` 이벤트를 사용하여 필요한 조치를 취할 수 있습니다.

## 예제
```javascript
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    // 기존 객체 저장소가 있는 경우 삭제
    if (event.oldVersion < 1) {
        db.deleteObjectStore("oldStore");
    }
    
    // 새로운 객체 저장소 생성
    db.createObjectStore("newStore");
};

request.onsuccess = function(event) {
    console.log("Database version updated to: " + event.target.result.version);
};
```

## 주의 사항
- `IDBVersionChangeEvent`는 데이터베이스 버전이 변경될 때만 발생하므로, 버전이 동일할 경우 이 이벤트는 발생하지 않습니다.
- 데이터베이스를 업데이트하는 과정에서 예외가 발생할 수 있으므로 항상 오류 처리를 구현해야 합니다.
- 여러 탭에서 동일한 데이터베이스를 열 경우, 한 탭에서 데이터베이스 버전을 변경하면 다른 탭에서 `onversionchange` 이벤트가 발생하여 해당 탭이 닫힐 수 있습니다.

## 한 줄 요약
`IDBVersionChangeEvent`는 인덱스DB의 데이터베이스 버전이 변경될 때 발생하는 이벤트로, 데이터베이스 구조를 업데이트하는 데 사용됩니다.