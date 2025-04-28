<!--
Meta Description: # JavaScript에서 Uint8Array: 효율적인 바이트 데이터 처리 ## 개요 `Uint8Array`는 자바스크립트에서 0부터 255까지의 정수 값을 저장할 수 있는 배열을 생성하는 Typed Array의 일종입니다. 이는 주로 바이너리 데이터를 효율적으로 처...
Meta Keywords: uint8array, new, const, console, log
-->

# JavaScript에서 Uint8Array: 효율적인 바이트 데이터 처리

## 개요
`Uint8Array`는 자바스크립트에서 0부터 255까지의 정수 값을 저장할 수 있는 배열을 생성하는 Typed Array의 일종입니다. 이는 주로 바이너리 데이터를 효율적으로 처리하고 조작하는 데 사용됩니다.

## 문서화
`Uint8Array`는 ECMAScript 6(ES6)에서 도입되었으며, 고정된 길이의 배열을 생성할 수 있는 기능을 제공합니다. 이 배열은 8비트 부호 없는 정수 값만을 담을 수 있으며, 일반 배열보다 더 나은 성능을 제공합니다. 특히, 이미지 데이터, 오디오 데이터, 또는 다른 바이너리 데이터를 다룰 때 유용합니다.

### 사용법
`Uint8Array`는 다양한 방법으로 생성할 수 있습니다:

1. **길이를 지정하여 생성**: `new Uint8Array(length)`
2. **배열이나 배열 비슷한 객체로부터 생성**: `new Uint8Array(array)`
3. **ArrayBuffer 객체로부터 생성**: `new Uint8Array(buffer)`

### 프로퍼티 및 메서드
- **length**: 배열의 길이를 반환합니다.
- **set()**: 주어진 배열이나 Typed Array의 값을 현재 `Uint8Array`에 설정합니다.
- **subarray()**: 지정한 시작 및 끝 인덱스에 해당하는 서브 배열을 반환합니다.

## 예제
```javascript
// 길이를 지정하여 Uint8Array 생성
const arr1 = new Uint8Array(5);
console.log(arr1); // Uint8Array(5) [ 0, 0, 0, 0, 0 ]

// 배열로부터 Uint8Array 생성
const arr2 = new Uint8Array([10, 20, 30]);
console.log(arr2); // Uint8Array(3) [ 10, 20, 30 ]

// ArrayBuffer로부터 Uint8Array 생성
const buffer = new ArrayBuffer(8);
const arr3 = new Uint8Array(buffer);
console.log(arr3); // Uint8Array(8) [ 0, 0, 0, 0, 0, 0, 0, 0 ]

// set() 메서드 사용
arr3.set([1, 2, 3]);
console.log(arr3); // Uint8Array(8) [ 1, 2, 3, 0, 0, 0, 0, 0 ]

// subarray() 메서드 사용
const subArr = arr3.subarray(1, 4);
console.log(subArr); // Uint8Array(3) [ 2, 3, 0 ]
```

## 설명
`Uint8Array`는 메모리 효율적이며, 성능이 뛰어난 배열을 제공하지만, 몇 가지 유의해야 할 점이 있습니다. 
- **값의 제한**: `Uint8Array`는 0에서 255 사이의 값만을 허용합니다. 이 범위를 초과하는 값은 자동으로 범위 내로 조절됩니다.
- **타입 제한**: 모든 값이 8비트 부호 없는 정수여야 하므로, 다른 타입의 값을 사용하면 오류가 발생할 수 있습니다.
- **메모리 관리**: `Uint8Array`는 ArrayBuffer와 밀접하게 연결되어 있어, ArrayBuffer의 생명주기에 영향을 받습니다. ArrayBuffer가 해제되면 관련된 `Uint8Array`도 사용할 수 없습니다.

## 한 줄 요약
`Uint8Array`는 바이너리 데이터를 효율적으로 처리할 수 있도록 설계된 자바스크립트의 Typed Array입니다.