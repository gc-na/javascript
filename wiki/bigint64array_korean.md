<!--
Meta Description: # JavaScript에서 BigInt64Array 이해하기 ## 개요 BigInt64Array는 JavaScript에서 64비트 정수의 배열을 처리하기 위해 제공되는 TypedArray입니다. 이 자료구조는 고정된 크기의 배열로, 정수형 데이터를 효율적으로 저장하고 ...
Meta Keywords: bigint64array, bigint64array는, new, 64비트, int64array
-->

# JavaScript에서 BigInt64Array 이해하기

## 개요
BigInt64Array는 JavaScript에서 64비트 정수의 배열을 처리하기 위해 제공되는 TypedArray입니다. 이 자료구조는 고정된 크기의 배열로, 정수형 데이터를 효율적으로 저장하고 조작할 수 있도록 설계되었습니다.

## 문서화
### 목적
BigInt64Array는 대량의 정수 데이터를 메모리에서 효율적으로 처리할 수 있게 해주는 도구입니다. 이 배열은 64비트의 정수만을 저장할 수 있으며, 주로 성능이 중요한 상황에서 사용됩니다.

### 사용법
BigInt64Array는 다음과 같은 방법으로 생성할 수 있습니다:
1. `new BigInt64Array(length)` : 주어진 길이만큼의 BigInt64Array를 생성합니다.
2. `new BigInt64Array(array)` : 기존의 배열이나 TypedArray를 기반으로 BigInt64Array를 생성합니다.
3. `new BigInt64Array(buffer, byteOffset, length)` : 주어진 ArrayBuffer의 특정 위치에서부터 주어진 길이만큼의 BigInt64Array를 생성합니다.

### 세부 사항
- **길이**: BigInt64Array의 길이는 정수형 데이터의 수를 나타내며, 길이는 8바이트(64비트) 단위로 증가합니다.
- **바이트 오프셋**: 바이트 오프셋은 배열의 시작 위치를 지정하며, 기본값은 0입니다.
- **읽기 및 쓰기**: BigInt64Array는 인덱스를 통해 데이터에 접근할 수 있으며, 기본적인 배열 메서드도 지원합니다.

## 예제
```javascript
// 5개의 요소를 가진 BigInt64Array 생성
const int64Array = new BigInt64Array(5);
int64Array[0] = BigInt(1234567890123456789);
int64Array[1] = BigInt(9876543210987654321);
console.log(int64Array); // BigInt64Array(5) [ 1234567890123456789n, 9876543210987654321n, 0n, 0n, 0n ]

// 기존 배열에서 생성
const numArray = [1n, 2n, 3n];
const int64ArrayFromArray = new BigInt64Array(numArray);
console.log(int64ArrayFromArray); // BigInt64Array(3) [ 1n, 2n, 3n ]
```

## 설명
- **정수 범위**: BigInt64Array는 -2^63부터 2^63-1까지의 범위를 가진 64비트 정수를 저장할 수 있습니다. 이는 정수형 데이터의 범위가 제한적이라는 것을 의미합니다.
- **성능**: TypedArray는 일반 배열보다 메모리 사용이 효율적이며, 성능이 중요한 계산에서 유리합니다.
- **호환성**: 모든 최신 브라우저에서 지원되지만, 구형 브라우저에서는 지원되지 않을 수 있습니다.

## 한 줄 요약
BigInt64Array는 64비트 정수를 효율적으로 처리하기 위한 JavaScript의 TypedArray로, 성능이 중요한 데이터 작업에 적합합니다.