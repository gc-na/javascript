<!--
Meta Description: # SubtleCrypto em JavaScript: Segurança e Criptografia no Navegador ## Sinopse O SubtleCrypto é uma interface da API Web Cryptography que fornece méto...
Meta Keywords: subtle, uma, para, crypto, subtlecrypto
-->

# SubtleCrypto em JavaScript: Segurança e Criptografia no Navegador

## Sinopse
O SubtleCrypto é uma interface da API Web Cryptography que fornece métodos para realizar operações criptográficas de forma assíncrona e segura no navegador. Ele é fundamental para desenvolvedores que desejam implementar segurança em aplicações web, permitindo operações como hashing, assinatura digital e criptografia.

## Documentação

### Propósito
O SubtleCrypto é projetado para oferecer uma maneira eficiente e segura de realizar operações criptográficas diretamente no navegador, sem a necessidade de bibliotecas externas. Ele é amplamente utilizado para proteger dados sensíveis e autenticar usuários, garantindo a integridade e a confidencialidade da informação.

### Uso
A interface SubtleCrypto está acessível através do objeto `window.crypto.subtle`. As operações disponíveis incluem:

- **Digest**: Gera um hash de um dado.
- **Encrypt**: Criptografa dados.
- **Decrypt**: Descriptografa dados.
- **Sign**: Cria uma assinatura digital.
- **Verify**: Verifica uma assinatura digital.
- **DeriveKey**: Deriva uma chave a partir de uma chave base.

### Métodos Principais
- `subtle.digest(algorithm, data)`
- `subtle.encrypt(algorithm, key, data)`
- `subtle.decrypt(algorithm, key, data)`
- `subtle.sign(algorithm, key, data)`
- `subtle.verify(algorithm, key, signature, data)`
- `subtle.deriveKey(params, baseKey, derivedKeyType, extractable, keyUsages)`

## Exemplos

### Exemplo de Hashing com SHA-256
```javascript
const data = new TextEncoder().encode("Hello, World!");
crypto.subtle.digest("SHA-256", data).then(hash => {
    console.log(new Uint8Array(hash));
});
```

### Exemplo de Criptografia e Descriptografia AES-GCM
```javascript
const keyMaterial = await crypto.subtle.importKey(
    "raw",
    new TextEncoder().encode("senha-secreta"),
    "PBKDF2",
    false,
    ["deriveKey"]
);

const key = await crypto.subtle.deriveKey(
    {
        name: "PBKDF2",
        salt: window.crypto.getRandomValues(new Uint8Array(16)),
        iterations: 100000,
        hash: "SHA-256"
    },
    keyMaterial,
    { name: "AES-GCM", length: 256 },
    false,
    ["encrypt", "decrypt"]
);

const iv = window.crypto.getRandomValues(new Uint8Array(12)); // Vetor de inicialização
const dataToEncrypt = new TextEncoder().encode("Mensagem secreta");

const encryptedData = await crypto.subtle.encrypt(
    { name: "AES-GCM", iv: iv },
    key,
    dataToEncrypt
);

// Para descriptografar
const decryptedData = await crypto.subtle.decrypt(
    { name: "AES-GCM", iv: iv },
    key,
    encryptedData
);

console.log(new TextDecoder().decode(decryptedData));
```

## Explicação
Embora o SubtleCrypto forneça uma interface poderosa, existem algumas armadilhas que os desenvolvedores devem estar cientes:

1. **Assincronicidade**: Todos os métodos retornam Promises, portanto, é essencial usar `async/await` ou `.then()` para lidar com os resultados.
2. **Segurança do IV**: Ao usar algoritmos como AES-GCM, o vetor de inicialização (IV) deve ser único e aleatório para cada operação de criptografia. Nunca reutilize um IV com a mesma chave.
3. **Compatibilidade do Navegador**: Embora suportado na maioria dos navegadores modernos, é importante verificar a compatibilidade do SubtleCrypto em versões mais antigas ou em navegadores específicos.

## Resumo em Uma Linha
O SubtleCrypto é uma interface da API Web Cryptography que permite realizar operações criptográficas seguras e assíncronas no navegador, essencial para a proteção de dados em aplicações web.