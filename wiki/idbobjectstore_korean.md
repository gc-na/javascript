<!--
Meta Description: # IDBObjectStore: JavaScript의 IndexedDB 객체 저장소 ## 개요 `IDBObjectStore`는 JavaScript의 IndexedDB API에서 사용되는 객체 저장소를 정의하는 인터페이스입니다. 이 객체 저장소는 구조화된 데이터 저장을 ...
Meta Keywords: let, 객체를, idbobjectstore, indexeddb, 데이터
-->

# IDBObjectStore: JavaScript의 IndexedDB 객체 저장소

## 개요
`IDBObjectStore`는 JavaScript의 IndexedDB API에서 사용되는 객체 저장소를 정의하는 인터페이스입니다. 이 객체 저장소는 구조화된 데이터 저장을 가능하게 하며, 비동기적으로 데이터를 CRUD(생성, 읽기, 업데이트, 삭제) 작업을 수행하는 데 사용됩니다.

## 문서화
`IDBObjectStore`는 IndexedDB 데이터베이스로부터 데이터를 저장하고 검색하는 데 중심적인 역할을 합니다. 객체 저장소는 데이터베이스의 데이터 구조를 정의하며, JavaScript 객체를 직접 저장할 수 있어 복잡한 데이터 구조를 쉽게 관리할 수 있게 해줍니다.

### 목적
- 데이터베이스 내에 객체를 저장하고 관리하기 위해 사용됩니다.
- 고유 키를 기반으로 객체를 식별할 수 있습니다.
- 트랜잭션을 통해 데이터의 일관성을 보장합니다.

### 사용법
`IDBObjectStore`는 IndexedDB의 `createObjectStore` 메서드로 생성됩니다. 데이터 저장소에 접근하기 위해서는 먼저 데이터베이스에 연결하고 트랜잭션을 시작해야 합니다.

### 주요 메서드
- `add(value, key)`: 지정된 키와 함께 객체를 저장합니다.
- `put(value, key)`: 객체를 업데이트하거나, 만약 객체가 없다면 새로 생성합니다.
- `get(key)`: 지정된 키에 해당하는 객체를 반환합니다.
- `delete(key)`: 지정된 키의 객체를 삭제합니다.
- `openCursor()`: 객체 저장소의 항목을 순회할 수 있는 커서를 반환합니다.

## 예제
```javascript
// IndexedDB 데이터베이스 열기
let request = indexedDB.open("myDatabase", 1);

// 데이터베이스 생성 및 객체 저장소 정의
request.onupgradeneeded = function(event) {
    let db = event.target.result;
    let objectStore = db.createObjectStore("myObjectStore", { keyPath: "id" });
};

// 데이터 추가
request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myObjectStore", "readwrite");
    let objectStore = transaction.objectStore("myObjectStore");

    let item = { id: 1, name: "JavaScript", type: "Programming Language" };
    let addRequest = objectStore.add(item);

    addRequest.onsuccess = function() {
        console.log("데이터가 성공적으로 추가되었습니다.");
    };
};
```

## 설명
`IDBObjectStore`를 사용할 때 주의해야 할 점은 데이터베이스와 객체 저장소가 비동기적으로 작동한다는 것입니다. 따라서 `onsuccess`와 `onerror` 이벤트 핸들러를 적절히 설정하여 오류를 처리하고 성공적인 작업을 확인해야 합니다. 또한, 객체 저장소의 키 경로를 올바르게 설정하는 것이 중요하며, 중복된 키를 추가하려고 할 경우 예외가 발생할 수 있습니다.

## 한 줄 요약
`IDBObjectStore`는 JavaScript에서 IndexedDB를 통해 객체 데이터를 효율적으로 저장하고 관리하는 인터페이스입니다.