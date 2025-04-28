<!--
Meta Description: # JavaScript의 Symbol: 고유하고 불변의 데이터 타입 ## 개요 JavaScript의 `Symbol`은 ES6(ECMAScript 2015)에서 도입된 데이터 타입으로, 고유하고 불변의 값으로 사용됩니다. 주로 객체의 고유한 키를 생성하는 데 활용되며, ...
Meta Keywords: symbol, const, 객체의, 데이터, javascript
-->

# JavaScript의 Symbol: 고유하고 불변의 데이터 타입

## 개요
JavaScript의 `Symbol`은 ES6(ECMAScript 2015)에서 도입된 데이터 타입으로, 고유하고 불변의 값으로 사용됩니다. 주로 객체의 고유한 키를 생성하는 데 활용되며, 이름 충돌을 방지하기 위해 사용됩니다.

## 문서화
### 목적
`Symbol`은 다른 데이터 타입과 충돌하지 않는 고유한 식별자를 생성하는 데 사용됩니다. 이는 객체의 프로퍼티 키로 사용될 수 있어, 객체의 구조를 안전하게 확장하는 데 유용합니다.

### 사용법
`Symbol`을 생성하려면 `Symbol()` 함수를 호출하면 됩니다. 이 함수는 선택적인 설명(description) 문자열을 인자로 받을 수 있으며, 이는 디버깅 시 유용하게 사용됩니다. 다음은 기본적인 사용법입니다.

```javascript
const sym1 = Symbol();
const sym2 = Symbol('description');
```

### 세부 사항
- **고유성**: 각 `Symbol`은 고유한 값이며, 같은 설명을 가진 두 `Symbol`도 동일하지 않습니다.
  
  ```javascript
  const symA = Symbol('key');
  const symB = Symbol('key');
  console.log(symA === symB); // false
  ```

- **객체의 키로 사용**: `Symbol`은 객체의 프로퍼티 키로 사용할 수 있으며, 일반적인 문자열 키와는 달리 외부에서 접근하기 어렵습니다.

  ```javascript
  const mySymbol = Symbol('mySymbol');
  const obj = {
      [mySymbol]: 'value'
  };
  console.log(obj[mySymbol]); // 'value'
  ```

- **전역 심볼**: `Symbol.for(key)` 메서드를 사용하면, 주어진 키에 대해 전역 심볼을 생성하거나 기존의 심볼을 반환할 수 있습니다.

  ```javascript
  const globalSym = Symbol.for('shared');
  const anotherGlobalSym = Symbol.for('shared');
  console.log(globalSym === anotherGlobalSym); // true
  ```

## 예제
```javascript
const uniqueKey = Symbol('unique');

const myObject = {
    [uniqueKey]: 'This is a unique value'
};

console.log(myObject[uniqueKey]); // 'This is a unique value'
```

## 설명
`Symbol`을 사용할 때 주의해야 할 점은 `Symbol` 값은 일반적인 데이터 타입과는 다르게 문자열이나 숫자와 같은 기본 타입으로 변환되지 않는다는 점입니다. 이로 인해 `Symbol`을 문자열로 사용하려고 하면 오류가 발생할 수 있습니다. 또한, `Symbol`은 객체의 속성으로 추가할 수 있지만, `for...in` 루프나 `Object.keys()`와 같은 메서드로는 열거되지 않기 때문에, 이를 고려해야 합니다.

### 일반적인 실수
- `Symbol`을 문자열로 변환하려고 시도할 때 `TypeError`가 발생할 수 있습니다.
- `Symbol`을 사용하는 객체의 프로퍼티를 열거하려면 `Object.getOwnPropertySymbols()` 메서드를 사용해야 합니다.

## 한 줄 요약
JavaScript의 `Symbol`은 고유하고 불변의 식별자를 생성하여 객체의 프로퍼티 키로 사용되는 데이터 타입입니다.