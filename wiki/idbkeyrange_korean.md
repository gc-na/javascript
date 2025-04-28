<!--
Meta Description: # IDBKeyRange: JavaScript에서 인덱스드DB 키 범위 생성하기 ## 개요 `IDBKeyRange`는 IndexedDB API의 일부로, 데이터베이스에서 특정 키 범위를 정의하는 데 사용됩니다. 이를 통해 쿼리와 데이터를 효과적으로 검색할 수 있습니다....
Meta Keywords: idbkeyrange, 범위를, open, lower, upper
-->

# IDBKeyRange: JavaScript에서 인덱스드DB 키 범위 생성하기

## 개요
`IDBKeyRange`는 IndexedDB API의 일부로, 데이터베이스에서 특정 키 범위를 정의하는 데 사용됩니다. 이를 통해 쿼리와 데이터를 효과적으로 검색할 수 있습니다.

## 문서화
### 목적
`IDBKeyRange`는 IndexedDB에서 데이터의 특정 범위를 정의하여 데이터베이스 쿼리의 효율성을 높이는 역할을 합니다. 이를 통해 개발자는 최소값, 최대값, 또는 두 값 사이의 범위를 설정할 수 있습니다.

### 사용법
`IDBKeyRange` 객체는 다음과 같은 메서드를 통해 생성할 수 있습니다:
- `IDBKeyRange.lowerBound(lower, open)`
- `IDBKeyRange.upperBound(upper, open)`
- `IDBKeyRange.bound(lower, upper, lowerOpen, upperOpen)`
- `IDBKeyRange.only(value)`

각 메서드는 다양한 옵션을 제공하여 범위를 설정할 수 있습니다.

### 세부사항
- `lowerBound(lower, open)`: 지정된 `lower` 값 이상인 모든 키를 포함하는 범위를 생성합니다. `open`이 `true`일 경우 `lower` 값은 포함되지 않습니다.
- `upperBound(upper, open)`: 지정된 `upper` 값 이하인 모든 키를 포함하는 범위를 생성합니다. `open`이 `true`일 경우 `upper` 값은 포함되지 않습니다.
- `bound(lower, upper, lowerOpen, upperOpen)`: `lower`와 `upper` 사이의 범위를 생성합니다. 각 경계에 대한 포함 여부를 설정할 수 있습니다.
- `only(value)`: 주어진 `value`와 정확하게 일치하는 키만 포함하는 범위를 생성합니다.

## 예제
```javascript
// IndexedDB를 열기
let request = indexedDB.open("myDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myObjectStore", "readonly");
    let objectStore = transaction.objectStore("myObjectStore");

    // lowerBound 사용 예
    let keyRange = IDBKeyRange.lowerBound(10);
    let request = objectStore.openCursor(keyRange);

    request.onsuccess = function(event) {
        let cursor = event.target.result;
        if (cursor) {
            console.log(cursor.value);
            cursor.continue();
        }
    };
};
```

## 설명
`IDBKeyRange`를 사용할 때 주의해야 할 점은 다음과 같습니다:
- 범위 설정 시 `open` 플래그를 잘못 설정하면 기대와 다른 결과를 초래할 수 있습니다.
- `IDBKeyRange`를 사용할 때는 항상 데이터베이스의 버전과 스토어를 정확히 지정해야 합니다.
- 복잡한 쿼리를 실행할 때 성능이 저하될 수 있으므로, 필요한 범위만을 지정하는 것이 중요합니다.

## 한 줄 요약
`IDBKeyRange`는 IndexedDB에서 데이터 검색 시 특정 키 범위를 정의하는 데 사용되는 유용한 도구입니다.