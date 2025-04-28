<!--
Meta Description: # IDBDatabase: JavaScript의 IndexedDB 데이터베이스 객체 ## 개요 `IDBDatabase`는 JavaScript에서 IndexedDB API의 핵심 객체로, 웹 애플리케이션이 클라이언트 측에서 대량의 구조화된 데이터를 저장하고 검색할 수 있...
Meta Keywords: 데이터베이스, idbdatabase, transaction, indexeddb, 데이터베이스의
-->

# IDBDatabase: JavaScript의 IndexedDB 데이터베이스 객체

## 개요
`IDBDatabase`는 JavaScript에서 IndexedDB API의 핵심 객체로, 웹 애플리케이션이 클라이언트 측에서 대량의 구조화된 데이터를 저장하고 검색할 수 있도록 지원합니다. 이 객체는 비동기적으로 작동하며, 데이터베이스의 생성, 트랜잭션, 데이터 조작을 관리합니다.

## 문서화
### 목적
`IDBDatabase` 객체는 IndexedDB의 데이터베이스를 나타내며, 데이터베이스의 스키마를 정의하고, 데이터를 읽고 쓰는 트랜잭션을 생성하는 데 사용됩니다. 이를 통해 브라우저에 데이터를 저장하여 오프라인에서도 애플리케이션을 사용할 수 있습니다.

### 사용법
`IDBDatabase` 객체는 `indexedDB.open()` 메서드를 호출하여 생성된 데이터베이스에 대한 참조를 제공합니다. 이는 주로 다음과 같은 방식으로 사용됩니다:

1. **데이터베이스 열기**: `indexedDB.open()` 메서드를 호출하여 데이터베이스를 연다.
2. **버전 변경 처리**: 데이터베이스의 버전이 변경되면 `onupgradeneeded` 이벤트 핸들러가 호출되어 데이터베이스 스키마를 업데이트할 수 있다.
3. **트랜잭션 생성**: `transaction()` 메서드를 사용하여 데이터베이스에서 트랜잭션을 생성하고, 데이터를 추가, 삭제, 수정할 수 있다.

### 세부 사항
- `IDBDatabase` 객체의 주요 속성:
  - `name`: 데이터베이스의 이름.
  - `version`: 현재 데이터베이스의 버전.
  - `objectStoreNames`: 데이터베이스에 포함된 객체 저장소의 이름 목록.
  
- 주요 메서드:
  - `transaction(storeNames, mode)`: 지정된 객체 저장소에 대한 트랜잭션을 생성합니다.
  - `close()`: 데이터베이스 연결을 닫습니다.
  
이 객체는 비동기적으로 작동하므로, 데이터베이스 작업의 결과는 프로미스를 통해 처리됩니다.

## 예제
```javascript
// 데이터베이스 열기
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    // 객체 저장소 생성
    db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    // 트랜잭션 시작
    let transaction = db.transaction("myObjectStore", "readwrite");
    let objectStore = transaction.objectStore("myObjectStore");

    // 데이터 추가
    objectStore.add({ id: 1, name: "John Doe" });

    transaction.oncomplete = function() {
        console.log("Transaction completed");
    };
};

request.onerror = function(event) {
    console.error("Database error: " + event.target.errorCode);
};
```

## 설명
`IDBDatabase`를 사용할 때 주의해야 할 점은 다음과 같습니다:
- **비동기 처리**: 모든 데이터베이스 작업은 비동기적으로 실행되므로, 결과를 사용하기 전에 `onsuccess` 또는 `onerror` 핸들러 내에서 처리해야 합니다.
- **버전 관리**: 데이터베이스의 버전이 변경될 때 스키마 업데이트를 위해 `onupgradeneeded` 이벤트를 적절히 처리해야 합니다. 이를 통해 데이터베이스 변경 사항을 안전하게 반영할 수 있습니다.
- **트랜잭션 범위**: 트랜잭션은 특정 객체 저장소에 대해 제한되므로, 여러 저장소에서 작업하려면 별도의 트랜잭션을 생성해야 합니다.

## 한 줄 요약
`IDBDatabase`는 JavaScript에서 IndexedDB API를 사용하여 클라이언트 측에 구조화된 데이터를 저장하고 관리하는 핵심 객체입니다.