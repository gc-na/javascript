<!--
Meta Description: # JavaScript의 Map: 효율적인 키-값 데이터 구조 ## 개요 JavaScript의 Map 객체는 키-값 쌍을 저장하는데 최적화된 데이터 구조로, 순서가 있는 데이터를 관리하고, 다양한 타입의 키를 사용할 수 있도록 돕습니다. ## 문서화 ### 목적 Map...
Meta Keywords: fruits, map, map은, 사용할, key
-->

# JavaScript의 Map: 효율적인 키-값 데이터 구조

## 개요
JavaScript의 Map 객체는 키-값 쌍을 저장하는데 최적화된 데이터 구조로, 순서가 있는 데이터를 관리하고, 다양한 타입의 키를 사용할 수 있도록 돕습니다.

## 문서화
### 목적
Map은 JavaScript에서 키-값 쌍을 저장하고 조작하는 데 사용됩니다. 일반 객체와 달리, Map은 키의 순서를 유지하며, 객체와는 달리 어떤 타입의 값도 키로 사용할 수 있는 장점이 있습니다.

### 사용법
Map 객체는 다음과 같이 생성할 수 있습니다:

```javascript
const myMap = new Map();
```

Map 객체는 다음과 같은 메서드를 제공합니다:
- `set(key, value)`: 키와 값을 Map에 추가합니다.
- `get(key)`: 주어진 키에 대한 값을 반환합니다.
- `has(key)`: 주어진 키가 Map에 존재하는지 여부를 확인합니다.
- `delete(key)`: 주어진 키와 그에 해당하는 값을 Map에서 삭제합니다.
- `clear()`: Map의 모든 요소를 제거합니다.
- `size`: Map에 저장된 요소의 수를 반환합니다.
- `forEach(callback)`: 각 요소에 대해 주어진 콜백 함수를 실행합니다.

### 예제
기본적인 Map 사용 예제는 다음과 같습니다:

```javascript
// Map 생성
const fruits = new Map();

// 값 추가
fruits.set('apple', 3);
fruits.set('banana', 5);

// 값 가져오기
console.log(fruits.get('apple')); // 3

// 키 존재 여부 확인
console.log(fruits.has('banana')); // true

// 키와 값 삭제
fruits.delete('apple');

// Map의 크기 확인
console.log(fruits.size); // 1

// 모든 요소 삭제
fruits.clear();
console.log(fruits.size); // 0
```

### 설명
Map을 사용할 때 유의해야 할 몇 가지 사항이 있습니다:
1. **키 타입**: Map의 키는 객체, 함수, 심볼 등 다양한 타입이 가능합니다. 이는 일반 객체에서는 문자열 또는 심볼만 키로 사용할 수 있는 것과 큰 차이입니다.
2. **순서 유지**: Map은 요소를 추가한 순서를 기억합니다. 따라서 이터레이션할 때 삽입된 순서대로 요소를 반환합니다.
3. **성능**: Map은 대량의 데이터를 저장하고 검색하는 데 있어 일반 객체보다 더 나은 성능을 제공합니다.

## 한 줄 요약
JavaScript의 Map은 다양한 타입의 키를 지원하며, 효율적으로 키-값 쌍을 저장하고 관리할 수 있는 데이터 구조입니다.