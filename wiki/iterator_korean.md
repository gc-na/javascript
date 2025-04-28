<!--
Meta Description: # 자바스크립트 Iterator (이터레이터) 완벽 가이드 ## 개요 이터레이터(Iterator)는 자바스크립트에서 데이터 구조를 순회하는 방법을 제공하는 객체입니다. 이터레이터는 컬렉션의 요소를 하나씩 접근할 수 있도록 해주며, 특히 배열, 맵, 셋과 같은 반복 가능...
Meta Keywords: iterator, done, value, next, return
-->

# 자바스크립트 Iterator (이터레이터) 완벽 가이드

## 개요
이터레이터(Iterator)는 자바스크립트에서 데이터 구조를 순회하는 방법을 제공하는 객체입니다. 이터레이터는 컬렉션의 요소를 하나씩 접근할 수 있도록 해주며, 특히 배열, 맵, 셋과 같은 반복 가능한 객체에서 유용하게 사용됩니다.

## 문서화

### 목적
이터레이터는 반복 가능한 객체의 요소를 순회하는 통일된 방법을 제공합니다. 이터레이터를 사용하면 복잡한 데이터 구조를 간편하게 탐색할 수 있으며, 코드의 가독성과 유지보수성을 높여줍니다.

### 사용법
이터레이터는 `next()` 메서드를 통해 순차적으로 값을 반환합니다. 이 메서드는 다음 값을 포함하는 객체를 반환하며, 이 객체는 `value`와 `done` 프로퍼티를 가집니다.

- `value`: 현재 이터레이션의 값.
- `done`: 이터레이션이 끝났는지를 나타내는 불리언 값.

### 이터레이터 생성
이터레이터를 생성하려면 `Symbol.iterator` 메서드를 구현해야 합니다. 예를 들어, 커스텀 객체에 이터레이터를 추가할 수 있습니다.

```javascript
const myObject = {
  values: [1, 2, 3],
  [Symbol.iterator]: function() {
    let index = 0;
    return {
      next: () => {
        if (index < this.values.length) {
          return { value: this.values[index++], done: false };
        } else {
          return { value: undefined, done: true };
        }
      }
    };
  }
};
```

## 예제
### 기본 사용 예제
```javascript
const array = [10, 20, 30];
const iterator = array[Symbol.iterator]();

console.log(iterator.next()); // { value: 10, done: false }
console.log(iterator.next()); // { value: 20, done: false }
console.log(iterator.next()); // { value: 30, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

### 커스텀 이터레이터 예제
```javascript
const range = {
  from: 1,
  to: 5,
  [Symbol.iterator]: function() {
    let current = this.from;
    return {
      next: () => {
        if (current <= this.to) {
          return { value: current++, done: false };
        } else {
          return { value: undefined, done: true };
        }
      }
    };
  }
};

for (let num of range) {
  console.log(num); // 1, 2, 3, 4, 5
}
```

## 설명
### 일반적인 실수
- 이터레이터의 `next()` 메서드를 호출하지 않으면 값을 얻을 수 없습니다.
- 이터레이터가 끝났을 때 `done` 프로퍼티를 체크하지 않으면 예기치 않은 결과가 발생할 수 있습니다.

### 추가 메모
- 이터레이터는 다양한 데이터 구조와 함께 사용되어 매우 유용합니다. 특히 `for...of` 루프와 함께 사용할 때 그 진가를 발휘합니다.
- 자바스크립트의 내장 객체인 `Map`, `Set` 등은 이미 이터레이터를 구현하고 있어 쉽게 사용할 수 있습니다.

## 한줄 요약
이터레이터는 자바스크립트에서 데이터 구조를 순회하는 데 사용되는 객체로, 코드의 가독성과 효율성을 높여줍니다.