<!--
Meta Description: # IDBKeyRange em JavaScript: A Compreensão do Intervalo de Chaves em IndexedDB ## Sinopse O `IDBKeyRange` é uma interface do IndexedDB que permite a c...
Meta Keywords: idbkeyrange, const, que, intervalo, request
-->

# IDBKeyRange em JavaScript: A Compreensão do Intervalo de Chaves em IndexedDB

## Sinopse
O `IDBKeyRange` é uma interface do IndexedDB que permite a criação de intervalos de chaves para consultas em bancos de dados, facilitando operações de leitura e filtragem de dados.

## Documentação
O `IDBKeyRange` é utilizado em operações de IndexedDB para definir um intervalo de chaves que podem ser usadas em consultas de dados. Essa ferramenta é essencial para filtrar registros que se encaixam em um determinado critério, como buscar todos os itens que têm um valor de chave dentro de um intervalo específico.

### Criação de Intervalos
Existem várias maneiras de criar um `IDBKeyRange`:

- **IDBKeyRange.only(value)**: Cria um intervalo que corresponde exatamente a um único valor.
- **IDBKeyRange.lowerBound(lower, open)**: Cria um intervalo que começa em um valor mínimo. O parâmetro `open` determina se o limite inferior é inclusivo (`false`) ou exclusivo (`true`).
- **IDBKeyRange.upperBound(upper, open)**: Cria um intervalo que termina em um valor máximo. O parâmetro `open` funciona da mesma forma que no `lowerBound`.
- **IDBKeyRange.bound(lower, upper, lowerOpen, upperOpen)**: Cria um intervalo entre dois valores, com a possibilidade de definir se os limites são inclusivos ou exclusivos.

### Uso
Os intervalos de chaves são frequentemente usados em métodos como `IDBIndex.openCursor()` ou `IDBObjectStore.openCursor()` para iterar sobre os registros que correspondem ao critério definido.

## Exemplos

### Exemplo 1: Usando `IDBKeyRange.only`
```javascript
const request = indexedDB.open("meuBanco", 1);

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("minhaStore", "readonly");
    const store = transaction.objectStore("minhaStore");
    const index = store.index("minhaIndex");

    const keyRange = IDBKeyRange.only("valorExato");
    const request = index.openCursor(keyRange);

    request.onsuccess = function(event) {
        const cursor = event.target.result;
        if (cursor) {
            console.log(cursor.value);
            cursor.continue();
        }
    };
};
```

### Exemplo 2: Usando `IDBKeyRange.bound`
```javascript
const request = indexedDB.open("meuBanco", 1);

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("minhaStore", "readonly");
    const store = transaction.objectStore("minhaStore");

    const keyRange = IDBKeyRange.bound("valorInferior", "valorSuperior", false, true);
    const request = store.openCursor(keyRange);

    request.onsuccess = function(event) {
        const cursor = event.target.result;
        if (cursor) {
            console.log(cursor.value);
            cursor.continue();
        }
    };
};
```

## Explicação
Um erro comum ao usar `IDBKeyRange` é não entender a diferença entre limites inclusivos e exclusivos. Isso pode levar a resultados inesperados se não forem definidos corretamente. Além disso, é importante lembrar que as chaves devem ser comparáveis; caso contrário, pode ocorrer um erro ao tentar criar um intervalo.

Outro ponto a considerar é que o uso de `IDBKeyRange` pode impactar o desempenho das consultas, especialmente em bancos de dados grandes. Portanto, sempre que possível, otimize suas chaves e intervalos para melhorar a eficiência das operações.

## Resumo em Uma Frase
O `IDBKeyRange` é uma interface do JavaScript para definir intervalos de chaves em IndexedDB, permitindo consultas eficientes e filtradas em bancos de dados.