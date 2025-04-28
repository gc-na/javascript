<!--
Meta Description: # Uint16Array: 자바스크립트의 16비트 부호 없는 정수 배열 ## 개요 `Uint16Array`는 자바스크립트에서 16비트 부호 없는 정수의 배열을 처리하기 위한 Typed Array 중 하나입니다. 이 배열은 0부터 65535까지의 정수 값을 저장할 수 있...
Meta Keywords: uint16array, javascript, const, new, arr
-->

# Uint16Array: 자바스크립트의 16비트 부호 없는 정수 배열

## 개요
`Uint16Array`는 자바스크립트에서 16비트 부호 없는 정수의 배열을 처리하기 위한 Typed Array 중 하나입니다. 이 배열은 0부터 65535까지의 정수 값을 저장할 수 있으며, 주로 이진 데이터 처리에 유용합니다.

## 문서화

### 목적
`Uint16Array`는 대량의 숫자 데이터를 효율적으로 저장하고 처리할 수 있도록 설계되었습니다. 이는 특히 WebGL과 같은 그래픽 API와의 상호작용에서 유용합니다.

### 사용법
`Uint16Array`를 생성하는 방법은 다음과 같습니다:

1. **빈 배열 생성**:
   ```javascript
   const arr = new Uint16Array();
   ```

2. **길이를 지정하여 배열 생성**:
   ```javascript
   const arr = new Uint16Array(10); // 10개의 요소를 가진 배열
   ```

3. **기존 배열로부터 생성**:
   ```javascript
   const arr = new Uint16Array([1, 2, 3, 4, 5]);
   ```

4. **ArrayBuffer로부터 생성**:
   ```javascript
   const buffer = new ArrayBuffer(16); // 16바이트의 ArrayBuffer
   const arr = new Uint16Array(buffer); // 8개의 16비트 부호 없는 정수
   ```

### 세부 사항
- **배열 요소 접근**: 배열 요소는 인덱스를 통해 접근할 수 있습니다.
  ```javascript
  arr[0] = 1000;
  console.log(arr[0]); // 1000
  ```

- **길이**: `Uint16Array`의 길이는 `length` 속성을 통해 확인할 수 있습니다.
  ```javascript
  console.log(arr.length); // 10
  ```

- **메소드**: `Uint16Array`는 다양한 메소드를 제공합니다.
  - `set()`: 배열의 특정 위치에 값을 설정합니다.
  - `subarray()`: 지정된 범위의 하위 배열을 반환합니다.

## 예제

```javascript
// Uint16Array 생성 및 사용 예제
const numbers = new Uint16Array([10, 20, 30]);

console.log(numbers[0]); // 10
numbers[1] = 25;
console.log(numbers); // Uint16Array(3) [ 10, 25, 30 ]
```

```javascript
// ArrayBuffer로부터 Uint16Array 생성
const buffer = new ArrayBuffer(8); // 8바이트
const uint16 = new Uint16Array(buffer);

uint16[0] = 500;
uint16[1] = 1000;

console.log(uint16); // Uint16Array(4) [ 500, 1000 ]
```

## 설명
`Uint16Array`를 사용할 때 주의해야 할 점은 다음과 같습니다:

- **범위**: `Uint16Array`는 0에서 65535 사이의 정수만 저장할 수 있습니다. 이 범위를 벗어난 숫자를 설정하면 값이 자동으로 변환됩니다.
- **성능**: Typed Arrays는 일반 배열에 비해 성능이 뛰어나며, 특히 대량의 숫자 데이터를 다룰 때 유리합니다.
- **메모리 관리**: Typed Array는 메모리를 효율적으로 사용하지만, 초과 사용 시 성능 저하가 발생할 수 있습니다.

## 한 줄 요약
`Uint16Array`는 자바스크립트에서 16비트 부호 없는 정수의 배열을 효율적으로 저장하고 처리하는 기능을 제공합니다.