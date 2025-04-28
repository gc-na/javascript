<!--
Meta Description: # SubtleCrypto: JavaScript의 안전한 암호화 API ## 개요 SubtleCrypto는 JavaScript에서 안전한 암호화, 복호화, 서명 및 해시 작업을 수행하는 데 사용되는 웹 API입니다. 이 API는 웹 브라우저 환경에서 원활하게 작동하며,...
Meta Keywords: 암호화, algorithm, data, key, subtlecrypto는
-->

# SubtleCrypto: JavaScript의 안전한 암호화 API

## 개요
SubtleCrypto는 JavaScript에서 안전한 암호화, 복호화, 서명 및 해시 작업을 수행하는 데 사용되는 웹 API입니다. 이 API는 웹 브라우저 환경에서 원활하게 작동하며, 보안성이 뛰어난 암호화 알고리즘을 제공합니다.

## 문서화
### 목적
SubtleCrypto는 웹 애플리케이션에서 데이터의 보안을 강화하기 위해 설계되었습니다. 이를 통해 개발자는 다양한 암호화 작업을 구현하여 사용자 데이터를 안전하게 보호할 수 있습니다.

### 사용법
SubtleCrypto는 `window.crypto.subtle` 객체를 통해 접근할 수 있습니다. 주요 메서드로는 `encrypt()`, `decrypt()`, `sign()`, `verify()`, `digest()` 등이 있습니다.

#### 기본 메서드 설명
- **encrypt(algorithm, key, data)**: 지정된 알고리즘을 사용하여 데이터를 암호화합니다.
- **decrypt(algorithm, key, data)**: 암호화된 데이터를 복호화합니다.
- **sign(algorithm, key, data)**: 주어진 데이터에 대해 디지털 서명을 생성합니다.
- **verify(algorithm, key, signature, data)**: 서명이 주어진 데이터와 일치하는지 검증합니다.
- **digest(algorithm, data)**: 주어진 데이터의 해시를 생성합니다.

### 예제
```javascript
// AES-GCM을 사용한 데이터 암호화 예제
const subtle = window.crypto.subtle;

async function encryptData(key, data) {
    const algorithm = { name: "AES-GCM", iv: window.crypto.getRandomValues(new Uint8Array(12)) };
    const ciphertext = await subtle.encrypt(algorithm, key, data);
    return ciphertext;
}

// RSA 키 쌍 생성 및 서명 예제
async function generateKeys() {
    const keys = await subtle.generateKey(
        {
            name: "RSA-OAEP",
            modulusLength: 2048,
            publicExponent: new Uint8Array([1, 0, 1]),
            hash: "SHA-256"
        },
        true,
        ["encrypt", "decrypt"]
    );
    return keys;
}
```

### 설명
SubtleCrypto를 사용할 때 몇 가지 주의사항이 있습니다:
- **비동기 처리**: 대부분의 SubtleCrypto 메서드는 비동기적으로 작동하며, `Promise`를 반환합니다. 따라서 `async/await` 또는 `then/catch`를 사용하여 결과를 처리해야 합니다.
- **브라우저 호환성**: SubtleCrypto는 최신 웹 브라우저에서 지원되지만, 구형 브라우저에서는 지원되지 않을 수 있습니다. 브라우저 호환성을 체크하는 것이 중요합니다.
- **보안 키 관리**: 암호화 키는 안전하게 관리해야 하며, 노출되지 않도록 주의해야 합니다.

## 한 줄 요약
SubtleCrypto는 JavaScript에서 안전한 암호화 및 해시 작업을 수행할 수 있는 강력한 API입니다.