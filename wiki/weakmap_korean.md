<!--
Meta Description: # JavaScript의 WeakMap: 메모리 관리와 성능 최적화 ## 개요 WeakMap은 JavaScript에서 객체를 키로 사용하여 데이터의 효율적인 저장과 관리가 가능한 컬렉션 타입입니다. WeakMap의 키는 가비지 컬렉션의 영향을 받아 메모리 관리를 최적화...
Meta Keywords: weakmap, weakmap은, 메모리, weakmap의, 가비지
-->

# JavaScript의 WeakMap: 메모리 관리와 성능 최적화

## 개요
WeakMap은 JavaScript에서 객체를 키로 사용하여 데이터의 효율적인 저장과 관리가 가능한 컬렉션 타입입니다. WeakMap의 키는 가비지 컬렉션의 영향을 받아 메모리 관리를 최적화할 수 있습니다.

## 문서화

### 목적
WeakMap은 주로 객체에 대한 메타데이터를 저장하거나, 프라이빗 데이터 저장소로 사용되며, 메모리 누수를 방지할 수 있도록 설계되었습니다.

### 사용법
WeakMap은 다음과 같은 구문으로 생성할 수 있습니다:
```javascript
const weakMap = new WeakMap();
```

WeakMap의 주요 메서드는 다음과 같습니다:
- `set(key, value)`: 키와 값을 WeakMap에 추가합니다.
- `get(key)`: 키에 대한 값을 반환합니다. 키가 존재하지 않으면 `undefined`를 반환합니다.
- `has(key)`: 지정한 키가 WeakMap에 존재하는지 확인합니다.
- `delete(key)`: 지정한 키와 그에 해당하는 값을 WeakMap에서 제거합니다.

WeakMap의 키는 반드시 객체여야 하며, 기본 데이터 타입(문자열, 숫자, 불리언 등)은 사용할 수 없습니다.

### 세부 사항
WeakMap은 다음과 같은 특징을 가집니다:
- **가비지 컬렉션**: WeakMap의 키는 약한 참조로 저장되어, 다른 곳에서 참조되지 않는 경우 자동으로 가비지 컬렉션이 발생합니다.
- **순회 불가**: WeakMap은 키의 순회를 지원하지 않으며, 이로 인해 특정 상황에서 성능을 향상시킬 수 있습니다.
- **비공식 데이터 저장**: WeakMap은 객체에 대한 비공식적인 데이터 저장소로 유용하며, 객체의 상태를 유지하는데 도움을 줍니다.

## 예제

### 기본 사용 예제

```javascript
const weakMap = new WeakMap();

let obj1 = {};
let obj2 = {};

weakMap.set(obj1, '첫 번째 객체');
weakMap.set(obj2, '두 번째 객체');

console.log(weakMap.get(obj1)); // '첫 번째 객체'
console.log(weakMap.has(obj2)); // true

weakMap.delete(obj1);
console.log(weakMap.has(obj1)); // false
```

### 메모리 관리 예제

```javascript
let obj3 = {};
const weakMap2 = new WeakMap();

weakMap2.set(obj3, '메모리 관리 예제');
obj3 = null; // obj3가 더 이상 참조되지 않음

// 다음 코드 실행 후, 강한 참조가 없으므로 가비지 컬렉션이 가능해짐
```

## 설명
WeakMap 사용 시 주의해야 할 점은 다음과 같습니다:
- **키의 제한**: WeakMap의 키는 반드시 객체여야 하므로, 기본 타입을 사용하면 오류가 발생합니다.
- **가비지 컬렉션**: WeakMap의 키가 더 이상 참조되지 않을 경우, 해당 키와 값은 자동으로 삭제되기 때문에, 데이터를 잃을 수 있습니다.
- **순회 불가**: WeakMap은 내부 상태를 외부에서 순회할 수 없으므로, 데이터의 모든 키를 조회하는 것이 필요한 경우에는 적합하지 않습니다.

## 한 줄 요약
WeakMap은 객체를 키로 사용하여 메모리 관리와 성능 최적화를 지원하는 JavaScript의 컬렉션 타입입니다.