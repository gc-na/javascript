<!--
Meta Description: # Int32Array: 자바스크립트에서의 32비트 정수 배열 ## 개요 Int32Array는 JavaScript에서 32비트 정수 값을 저장하고 조작하기 위한 배열 형태의 객체입니다. 이 배열은 정수 데이터를 효율적으로 처리하는 데 최적화되어 있으며, WebGL 및 ...
Meta Keywords: int32array, int32array는, 배열의, 32비트, new
-->

# Int32Array: 자바스크립트에서의 32비트 정수 배열

## 개요
Int32Array는 JavaScript에서 32비트 정수 값을 저장하고 조작하기 위한 배열 형태의 객체입니다. 이 배열은 정수 데이터를 효율적으로 처리하는 데 최적화되어 있으며, WebGL 및 다양한 데이터 처리 작업에 유용하게 사용됩니다.

## 문서화
Int32Array는 TypedArray의 일종으로, 이진 데이터의 조작을 가능하게 합니다. 주로 다음과 같은 용도로 사용됩니다:

- **목적**: Int32Array는 32비트 정수의 배열을 생성하고 이 배열을 사용하여 고성능 데이터 처리를 수행합니다.
- **사용법**: Int32Array는 다양한 방법으로 생성할 수 있습니다. 예를 들어, 정수 배열로 초기화하거나, ArrayBuffer로부터 생성할 수 있습니다.

### 생성 방법
```javascript
let arr1 = new Int32Array(5); // 길이가 5인 배열 생성
let arr2 = new Int32Array([1, 2, 3, 4, 5]); // 초기값이 있는 배열 생성
let buffer = new ArrayBuffer(16); // 16바이트의 ArrayBuffer 생성
let arr3 = new Int32Array(buffer); // ArrayBuffer로부터 Int32Array 생성
```

### 속성 및 메서드
- **length**: 배열의 길이를 반환합니다.
- **set()**: 다른 배열의 값을 현재 Int32Array에 설정합니다.
- **subarray()**: 현재 배열의 일부를 새로운 Int32Array로 반환합니다.

## 예제
```javascript
// Int32Array 생성
const intArray = new Int32Array([10, 20, 30, 40]);

// 배열의 길이 출력
console.log(intArray.length); // 4

// 배열의 값 설정
intArray.set([50, 60], 2); // 인덱스 2부터 값 설정
console.log(intArray); // Int32Array(4) [10, 20, 50, 60]

// 서브 배열 생성
const subArray = intArray.subarray(1, 3);
console.log(subArray); // Int32Array(2) [20, 50]
```

## 설명
Int32Array를 사용할 때 주의해야 할 점은 타입의 제한입니다. Int32Array는 항상 32비트 정수만을 저장할 수 있으며, 저장하려는 값이 이 범위를 초과하면 자동으로 변환됩니다. 또한, Int32Array는 배열의 길이를 고정하기 때문에, 한 번 생성된 후에는 크기를 변경할 수 없습니다. 이러한 특성은 성능을 높이는 데 기여하지만, 배열의 동적 크기 조정이 필요한 경우 다른 배열 타입을 고려해야 합니다.

## 한 줄 요약
Int32Array는 자바스크립트에서 32비트 정수 배열을 생성하고 조작하기 위한 고성능 배열 객체입니다.