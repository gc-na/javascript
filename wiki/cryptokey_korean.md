<!--
Meta Description: # JavaScript의 CryptoKey: 안전한 암호화와 키 관리 ## 개요 CryptoKey는 JavaScript의 Web Cryptography API에서 제공하는 객체로, 안전한 암호화 및 데이터 보호를 위한 키를 나타냅니다. 이 객체는 암호화, 복호화, 서명...
Meta Keywords: 암호화, const, crypto, cryptokey, cryptokey는
-->

# JavaScript의 CryptoKey: 안전한 암호화와 키 관리

## 개요
CryptoKey는 JavaScript의 Web Cryptography API에서 제공하는 객체로, 안전한 암호화 및 데이터 보호를 위한 키를 나타냅니다. 이 객체는 암호화, 복호화, 서명 및 검증과 같은 다양한 암호화 작업을 수행하는 데 사용됩니다.

## 문서화
### 목적
CryptoKey의 주요 목적은 암호화 알고리즘에서 사용할 수 있는 키를 안전하게 생성하고 관리하는 것입니다. 이 API는 웹 애플리케이션에서 보안성을 높이기 위해 설계되었습니다.

### 사용법
CryptoKey 객체는 `SubtleCrypto` 인터페이스의 메서드를 사용하여 생성됩니다. 예를 들어, `generateKey` 메서드를 사용하여 대칭 또는 비대칭 암호화 키를 생성할 수 있습니다.

```javascript
// 대칭 키 생성 예제
const crypto = window.crypto.subtle;
const keyPromise = crypto.generateKey(
    {
        name: "AES-GCM",
        length: 256,
    },
    true, // 키가 추출 가능한지 여부
    ["encrypt", "decrypt"] // 키 사용 용도
);
```

이 코드에서 생성된 `keyPromise`는 Promise를 반환하며, 성공적으로 생성된 후 CryptoKey 객체를 제공받습니다.

### 세부 사항
- **키 유형**: CryptoKey는 대칭키(AES) 및 비대칭키(RSA, ECDSA) 등 다양한 유형을 지원합니다.
- **키의 내구성**: CryptoKey는 메모리에 안전하게 보관되며, 불필요한 노출을 방지합니다.
- **사용 용도**: 생성된 키는 암호화(`encrypt`), 복호화(`decrypt`), 서명(`sign`), 검증(`verify`) 등의 작업에 사용될 수 있습니다.

## 예제
### 대칭 키로 데이터 암호화하기
```javascript
async function encryptData(plainText, key) {
    const encodedText = new TextEncoder().encode(plainText);
    const iv = window.crypto.getRandomValues(new Uint8Array(12)); // 초기화 벡터 생성
    const cipherText = await crypto.encrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        encodedText
    );
    return { cipherText, iv };
}
```

### 복호화
```javascript
async function decryptData(cipherText, key, iv) {
    const decryptedText = await crypto.decrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        cipherText
    );
    return new TextDecoder().decode(decryptedText);
}
```

## 설명
### 일반적인 함정 및 주의사항
- **키 관리**: CryptoKey 객체는 자동으로 관리되지만, 보안 관점에서 키 사용 후에는 적절히 폐기하는 것이 좋습니다.
- **비동기 처리**: `generateKey`, `encrypt`, `decrypt`와 같은 메서드는 모두 비동기적이므로 Promise를 처리하는 방법을 숙지해야 합니다.
- **브라우저 호환성**: Web Cryptography API는 모든 브라우저에서 동일하게 지원되지 않으므로, 사용하기 전에 호환성 체크가 필요합니다.

## 한 줄 요약
CryptoKey는 JavaScript의 Web Cryptography API에서 안전한 암호화 및 키 관리를 위한 객체로, 다양한 암호화 작업에 사용됩니다.