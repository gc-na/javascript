<!--
Meta Description: # JavaScript WeakSet: 메모리 관리 및 객체 참조 최적화 ## 개요 WeakSet은 JavaScript에서 객체를 저장하는 컬렉션으로, 객체에 대한 약한 참조를 제공합니다. 메모리 관리와 성능 향상을 위해 설계된 WeakSet은 가비지 컬렉션과 함께 작...
Meta Keywords: weakset, weakset은, 객체를, obj1, 메모리
-->

# JavaScript WeakSet: 메모리 관리 및 객체 참조 최적화

## 개요
WeakSet은 JavaScript에서 객체를 저장하는 컬렉션으로, 객체에 대한 약한 참조를 제공합니다. 메모리 관리와 성능 향상을 위해 설계된 WeakSet은 가비지 컬렉션과 함께 작동하여 사용하지 않는 객체를 자동으로 청소합니다.

## 문서화
WeakSet은 ES6(ECMAScript 2015)에서 도입된 객체로, 다음과 같은 주요 특징이 있습니다:

- **목적**: WeakSet은 객체의 약한 참조를 유지하여, 해당 객체가 더 이상 필요하지 않으면 자동으로 가비지 컬렉터에 의해 수거될 수 있도록 합니다.
- **사용법**: WeakSet은 객체를 요소로 가질 수 있으며, 원시 값(숫자, 문자열, 불리언 등)은 저장할 수 없습니다. WeakSet의 모든 요소는 반드시 객체여야 하며, 중복된 값을 허용하지 않습니다.
- **메서드**:
  - `add(value)`: WeakSet에 객체를 추가합니다.
  - `delete(value)`: WeakSet에서 객체를 삭제합니다.
  - `has(value)`: 특정 객체가 WeakSet에 존재하는지 여부를 확인합니다.

## 사용 예시
```javascript
// WeakSet 생성
const weakset = new WeakSet();

// 객체 생성
let obj1 = {};
let obj2 = {};

// 객체 추가
weakset.add(obj1);
weakset.add(obj2);

// 객체 존재 여부 확인
console.log(weakset.has(obj1)); // true
console.log(weakset.has(obj2)); // true

// 객체 삭제
weakset.delete(obj1);
console.log(weakset.has(obj1)); // false
```

## 설명
WeakSet의 주요 장점은 메모리 사용을 최적화하는 것입니다. 객체에 대한 강한 참조가 없기 때문에, 다른 코드에서 WeakSet에 저장된 객체를 참조하지 않으면 가비지 컬렉터가 해당 객체를 자동으로 수거합니다. 하지만 다음과 같은 주의사항이 있습니다:

- **원시값 저장 불가**: WeakSet은 객체만 저장할 수 있으며, 원시값(숫자, 문자열, 불리언 등)은 저장할 수 없습니다.
- **반복 불가**: WeakSet은 iterable하지 않기 때문에, forEach 또는 for..of 루프를 사용하여 요소를 반복할 수 없습니다.
- **WeakSet의 크기 확인 불가**: WeakSet은 size 속성을 제공하지 않으므로, 현재 저장된 객체의 수를 직접 확인할 수 없습니다.

## 한 줄 요약
WeakSet은 JavaScript에서 객체에 대한 약한 참조를 제공하여 메모리 관리와 성능을 최적화하는 컬렉션입니다.