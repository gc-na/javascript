<!--
Meta Description: # IDBTransaction: JavaScript에서의 인덱스드DB 트랜잭션 ## 개요 IDBTransaction은 인덱스드DB(IndexedDB) API의 핵심 구성 요소로, 데이터베이스 작업을 수행하는 동안 데이터의 일관성을 보장하기 위해 사용되는 트랜잭션을 생성...
Meta Keywords: const, transaction, event, 트랜잭션, function
-->

# IDBTransaction: JavaScript에서의 인덱스드DB 트랜잭션

## 개요
IDBTransaction은 인덱스드DB(IndexedDB) API의 핵심 구성 요소로, 데이터베이스 작업을 수행하는 동안 데이터의 일관성을 보장하기 위해 사용되는 트랜잭션을 생성합니다. 이를 통해 여러 데이터베이스 요청을 묶어서 원자성을 보장하며, 데이터의 무결성을 유지할 수 있습니다.

## 문서화

### 목적
IDBTransaction은 인덱스드DB에서 데이터를 읽거나 수정할 때, 여러 작업을 하나의 트랜잭션으로 묶어서 처리할 수 있도록 합니다. 이를 통해 데이터의 일관성을 유지하고, 실패 시 모든 작업을 원래 상태로 되돌릴 수 있습니다.

### 사용법
IDBTransaction은 `IDBDatabase.transaction()` 메서드를 통해 생성됩니다. 다음은 IDBTransaction을 사용하는 기본적인 방법입니다:

```javascript
const request = indexedDB.open("myDatabase", 1);

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("myObjectStore", "readwrite");

    const objectStore = transaction.objectStore("myObjectStore");
    const addRequest = objectStore.add({ id: 1, name: "Sample" });

    addRequest.onsuccess = function() {
        console.log("데이터가 추가되었습니다.");
    };

    transaction.oncomplete = function() {
        console.log("트랜잭션이 완료되었습니다.");
    };

    transaction.onerror = function(event) {
        console.error("트랜잭션 오류:", event.target.error);
    };
};
```

### 세부사항
- **모드**: IDBTransaction은 세 가지 모드를 지원합니다:
  - `readonly`: 읽기 전용 트랜잭션.
  - `readwrite`: 읽기 및 쓰기 가능한 트랜잭션.
  - `versionchange`: 데이터베이스 버전 변경 시 사용되는 트랜잭션.

- **이벤트**: 트랜잭션은 여러 이벤트를 발생시킵니다:
  - `oncomplete`: 트랜잭션이 성공적으로 완료되었을 때 호출됩니다.
  - `onerror`: 트랜잭션 중 오류가 발생했을 때 호출됩니다.
  - `onabort`: 트랜잭션이 중단되었을 때 호출됩니다.

## 예제
```javascript
const request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("myObjectStore", "readwrite");
    const objectStore = transaction.objectStore("myObjectStore");

    const updateRequest = objectStore.put({ id: 1, name: "Updated Sample" });

    updateRequest.onsuccess = function() {
        console.log("데이터가 업데이트되었습니다.");
    };
};
```

## 설명
IDBTransaction을 사용할 때 주의해야 할 사항:
- 트랜잭션의 범위 내에서만 데이터베이스 작업을 수행해야 합니다. 트랜잭션이 완료되거나 오류가 발생하기 전에 작업을 완료해야 합니다.
- 트랜잭션 모드에 따라 사용할 수 있는 메서드가 제한될 수 있으므로, 사용하려는 작업에 적합한 모드를 선택해야 합니다.
- 여러 트랜잭션을 동시에 열면 데이터 충돌이 발생할 수 있으며, 이러한 경우 데이터의 일관성이 보장되지 않을 수 있습니다.

## 한 줄 요약
IDBTransaction은 인덱스드DB에서 데이터베이스 작업을 안전하게 수행하기 위한 트랜잭션을 생성하여 데이터의 무결성과 일관성을 유지합니다.