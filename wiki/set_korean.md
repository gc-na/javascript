<!--
Meta Description: # JavaScript의 Set: 중복 없는 데이터 집합 관리하기 ## 개요 JavaScript의 Set은 중복되지 않는 값을 저장하는 데 사용되는 객체입니다. 이 데이터 구조는 배열과 유사하지만, 모든 값이 유일하다는 특징이 있습니다. Set을 사용하면 데이터를 효과...
Meta Keywords: set, fruits, set은, console, log
-->

# JavaScript의 Set: 중복 없는 데이터 집합 관리하기

## 개요
JavaScript의 Set은 중복되지 않는 값을 저장하는 데 사용되는 객체입니다. 이 데이터 구조는 배열과 유사하지만, 모든 값이 유일하다는 특징이 있습니다. Set을 사용하면 데이터를 효과적으로 관리하고, 중복을 제거하는 데 유용합니다.

## 문서화

### 목적
Set은 데이터의 유일성을 보장하고, 효율적인 데이터 조작을 가능하게 합니다. 특히, 중복된 값을 허용하지 않기 때문에 데이터의 정확성을 유지하는 데 큰 도움이 됩니다.

### 사용법
Set은 다음과 같은 방식으로 생성하고 사용할 수 있습니다:

```javascript
// Set 생성
const mySet = new Set([1, 2, 2, 3]);

// 값 추가
mySet.add(4);

// 값 삭제
mySet.delete(2);

// 값 존재 여부 확인
const hasValue = mySet.has(3); // true

// Set의 크기
const size = mySet.size; // 3

// 모든 값 순회
mySet.forEach(value => {
    console.log(value);
});
```

### 세부사항
- **생성자**: `new Set(iterable)` 형태로 생성합니다. iterable은 배열 또는 유사 배열 객체입니다.
- **중복 제거**: Set은 자동으로 중복된 값을 제거합니다.
- **메소드**:
  - `add(value)`: Set에 값을 추가합니다.
  - `delete(value)`: Set에서 값을 삭제합니다.
  - `has(value)`: Set에 값이 존재하는지 확인합니다.
  - `clear()`: Set의 모든 값을 제거합니다.
  - `size`: Set의 요소 개수를 반환합니다.

## 예제

### 기본 사용 예제
```javascript
// Set 생성
const fruits = new Set(['apple', 'banana', 'orange', 'banana']);
console.log(fruits); // Set(3) { 'apple', 'banana', 'orange' }

// 값 추가
fruits.add('kiwi');
console.log(fruits); // Set(4) { 'apple', 'banana', 'orange', 'kiwi' }

// 값 삭제
fruits.delete('orange');
console.log(fruits); // Set(3) { 'apple', 'banana', 'kiwi' }

// 존재 여부 확인
console.log(fruits.has('kiwi')); // true
console.log(fruits.has('grape')); // false
```

### Set의 순회
```javascript
const numbers = new Set([1, 2, 3, 4]);
numbers.forEach(num => {
    console.log(num * 2); // 2, 4, 6, 8
});
```

## 설명
Set을 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **객체의 동등성**: Set은 참조 타입인 객체를 다룰 때 동일한 객체를 중복으로 추가할 수 없습니다. 서로 다른 객체는 동일한 값이더라도 별개의 항목으로 인식됩니다.
  
- **순서 보장**: Set은 삽입된 순서를 유지하며, 요소를 순회할 때 이 순서대로 반환됩니다.

- **이터러블**: Set은 이터러블 객체이므로, `for...of` 루프를 사용하여 값에 접근할 수 있습니다.

```javascript
for (let value of fruits) {
    console.log(value); // apple, banana, kiwi
}
```

## 한 문장 요약
JavaScript의 Set은 중복되지 않는 값의 집합을 효율적으로 관리하고 조작할 수 있는 강력한 데이터 구조입니다.