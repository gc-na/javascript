<!--
Meta Description: # FinalizationRegistry: JavaScript의 최종화 레지스트리 이해하기 ## 개요 `FinalizationRegistry`는 자바스크립트에서 가비지 컬렉션이 이루어진 후 특정 작업을 수행할 수 있도록 해주는 기능입니다. 이를 통해 객체가 메모리에서 ...
Meta Keywords: finalizationregistry, 가비지, 객체가, const, registry
-->

# FinalizationRegistry: JavaScript의 최종화 레지스트리 이해하기

## 개요
`FinalizationRegistry`는 자바스크립트에서 가비지 컬렉션이 이루어진 후 특정 작업을 수행할 수 있도록 해주는 기능입니다. 이를 통해 객체가 메모리에서 제거될 때의 후처리를 관리할 수 있습니다.

## 문서화
`FinalizationRegistry`는 객체가 가비지 컬렉터에 의해 수거될 때 특정 콜백 함수를 호출할 수 있게 해주는 API입니다. 주로 메모리 관리와 자원 해제를 위한 용도로 사용됩니다.

### 목적
- 객체의 수명 주기를 감시하고, 객체가 더 이상 필요하지 않을 때 후속 작업을 수행할 수 있도록합니다.

### 사용법
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`가비지 수집됨: ${heldValue}`);
});

function createObject() {
    const obj = {};
    registry.register(obj, '객체의 정보');
    return obj;
}

let obj1 = createObject();
obj1 = null; // 이 시점에서 obj1은 가비지 수집 대상이 됩니다.
```

### 세부사항
- `FinalizationRegistry`는 생성자를 통해 초기화되며, 콜백 함수와 함께 사용됩니다.
- `register` 메소드를 사용하여 감시할 객체와 관련된 값을 등록할 수 있습니다.
- 객체가 가비지 컬렉션 대상이 되었을 때, 등록된 콜백 함수가 호출됩니다. 이때 콜백 함수는 등록된 값을 인자로 받습니다.
- `FinalizationRegistry`는 단일 스레드 환경에서만 사용되며, 비동기 작업의 신뢰성을 보장하지 않습니다.

## 예제
### 기본 사용 예
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`가비지 수집됨: ${heldValue}`);
});

function createUser(name) {
    const user = { name };
    registry.register(user, name);
    return user;
}

let user1 = createUser('Alice');
user1 = null; // Alice 객체가 가비지 수집 대상이 됩니다.
```

### 추가 예
```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`정리 작업: ${heldValue} 객체가 수집됨`);
});

function createResource() {
    const resource = {};
    registry.register(resource, '리소스 정보');
    return resource;
}

let resource1 = createResource();
resource1 = null; // 리소스 객체가 가비지 수집 대상입니다.
```

## 설명
- `FinalizationRegistry`를 사용할 때 주의할 점은 콜백 함수가 언제 호출될지 예측할 수 없다는 것입니다. 가비지 컬렉션은 자바스크립트 엔진의 내부 로직에 따라 다르기 때문에, 예상보다 늦게 호출될 수 있습니다.
- 또한, 등록된 콜백은 자원 관리를 위해 사용될 수 있지만, 이를 통해 동기적 작업이 보장되지 않으므로, 비동기 코드에서의 사용은 주의가 필요합니다.
- `FinalizationRegistry`는 메모리 누수를 방지하는 데 유용하지만, 모든 경우에 적합하지 않을 수 있습니다. 특히, 객체의 수명이 짧은 경우에는 필요하지 않을 수 있습니다.

## 한 줄 요약
`FinalizationRegistry`는 자바스크립트에서 가비지 수집 후 특정 작업을 수행하도록 돕는 기능입니다.