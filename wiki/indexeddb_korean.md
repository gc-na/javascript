<!--
Meta Description: # IndexedDB: 자바스크립트를 위한 비동기 데이터베이스 ## 요약 IndexedDB는 웹 브라우저에서 클라이언트 측 데이터를 저장하고 관리하기 위한 비동기 API입니다. 이를 통해 대량의 구조화된 데이터를 저장할 수 있으며, 오프라인 애플리케이션 개발에 유용합니...
Meta Keywords: let, 데이터베이스, 데이터를, transaction, event
-->

# IndexedDB: 자바스크립트를 위한 비동기 데이터베이스

## 요약
IndexedDB는 웹 브라우저에서 클라이언트 측 데이터를 저장하고 관리하기 위한 비동기 API입니다. 이를 통해 대량의 구조화된 데이터를 저장할 수 있으며, 오프라인 애플리케이션 개발에 유용합니다.

## 문서화
### 목적
IndexedDB는 웹 애플리케이션에서 대용량의 데이터를 효율적으로 저장하고 검색할 수 있도록 설계된 비동기 데이터베이스입니다. 주로 오프라인 지원이 필요한 웹 애플리케이션에서 사용되며, 사용자가 브라우저에 데이터를 저장하여 인터넷 연결 없이도 접근할 수 있게 합니다.

### 사용법
IndexedDB는 다음과 같은 기본적인 절차로 사용됩니다:

1. **데이터베이스 열기**: `indexedDB.open()` 메서드를 사용하여 데이터베이스를 엽니다.
2. **트랜잭션 시작**: `db.transaction()` 메서드를 통해 데이터베이스에 대한 트랜잭션을 시작합니다.
3. **객체 저장소 접근**: 트랜잭션에서 특정 객체 저장소를 선택합니다.
4. **데이터 작업 수행**: 데이터를 추가, 수정, 삭제, 검색하는 작업을 수행합니다.

### 세부사항
- **비동기 처리**: IndexedDB는 비동기 API로, 데이터베이스 작업은 Promise 기반으로 수행됩니다. 이를 통해 UI가 차단되지 않고 부드럽게 작동합니다.
- **객체 저장소**: 데이터는 객체 저장소에 저장되며, 각 객체 저장소는 고유한 키를 가집니다.
- **인덱스 사용**: 인덱스를 만들어 데이터를 효율적으로 검색할 수 있습니다.

## 예제
### 데이터베이스 열기 및 데이터 추가

```javascript
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myObjectStore", "readwrite");
    let objectStore = transaction.objectStore("myObjectStore");
    
    let data = { id: 1, name: "John Doe", age: 30 };
    objectStore.add(data);
};
```

### 데이터 검색

```javascript
let request = indexedDB.open("myDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myObjectStore", "readonly");
    let objectStore = transaction.objectStore("myObjectStore");
    
    let getRequest = objectStore.get(1);
    getRequest.onsuccess = function(event) {
        console.log(getRequest.result);
    };
};
```

## 설명
IndexedDB는 비동기적으로 작동하므로, 데이터베이스 작업을 수행할 때 항상 콜백이나 Promise를 사용해야 합니다. 이를 통해 작업이 완료된 후에 데이터를 처리할 수 있습니다. 또한, 데이터베이스 버전 관리가 필요하며, 버전이 변경될 때마다 `onupgradeneeded` 이벤트가 발생하여 데이터베이스 구조를 수정할 수 있습니다. 

### 일반적인 오류 및 주의사항
- **데이터베이스 버전 관리**: 데이터베이스의 버전을 적절하게 관리하지 않으면 예상치 못한 오류가 발생할 수 있습니다.
- **비동기 처리**: 모든 IndexedDB 작업은 비동기적이므로, 동기적으로 사용할 경우 코드가 예기치 않게 작동할 수 있습니다.
- **브라우저 호환성**: 일부 구형 브라우저에서는 IndexedDB를 지원하지 않을 수 있으므로, 사용하기 전에 호환성을 확인해야 합니다.

## 한 줄 요약
IndexedDB는 웹 애플리케이션에서 클라이언트 측 데이터를 비동기적으로 저장하고 관리할 수 있는 강력한 데이터베이스 API입니다.