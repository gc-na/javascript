<!--
Meta Description: # structuredClone: Clonagem Estruturada em JavaScript ## Sinopse A função `structuredClone` permite a clonagem profunda de objetos JavaScript, incluin...
Meta Keywords: structuredclone, clonagem, javascript, objetos, não
-->

# structuredClone: Clonagem Estruturada em JavaScript

## Sinopse
A função `structuredClone` permite a clonagem profunda de objetos JavaScript, incluindo tipos complexos como Mapas, Conjuntos e instâncias de classes, preservando a estrutura e os dados, sem a necessidade de implementar manualmente a clonagem.

## Documentação
A função `structuredClone` foi introduzida no ECMAScript 2021 e fornece uma maneira eficiente de criar uma cópia de um objeto ou valor, mantendo suas propriedades e referências adequadas.

### Propósito
O propósito principal do `structuredClone` é facilitar a clonagem de estruturas de dados complexas que não podem ser copiadas usando métodos tradicionais, como `Object.assign()` ou `JSON.stringify()`/`JSON.parse()`.

### Uso
A sintaxe básica da função é:
```javascript
let clone = structuredClone(value);
```
Onde `value` é o objeto ou valor que você deseja clonar.

### Detalhes
- **Tipos Suportados**: `structuredClone` suporta a clonagem de diversos tipos, incluindo objetos, arrays, Mapas, Conjuntos, e até mesmo instâncias de classes.
- **Valores Não Suportados**: Funções, símbolos, e objetos que não podem ser serializados, como `undefined`, não são copiados.
- **Ciclo de Referência**: A função pode lidar com referências circulares, evitando loops infinitos.

## Exemplos

### Exemplo Básico
```javascript
const original = { a: 1, b: { c: 2 } };
const clone = structuredClone(original);

console.log(clone); // { a: 1, b: { c: 2 } }
console.log(clone !== original); // true
```

### Clonando um Mapa
```javascript
const originalMap = new Map([[1, 'one'], [2, 'two']]);
const cloneMap = structuredClone(originalMap);

console.log(cloneMap); // Map(2) { 1 => 'one', 2 => 'two' }
console.log(cloneMap !== originalMap); // true
```

### Clonando um Conjunto
```javascript
const originalSet = new Set([1, 2, 3]);
const cloneSet = structuredClone(originalSet);

console.log(cloneSet); // Set(3) { 1, 2, 3 }
console.log(cloneSet !== originalSet); // true
```

## Explicação
Embora `structuredClone` seja uma ferramenta poderosa, existem algumas armadilhas comuns a serem observadas:

- **Limitações de Tipos**: Tente evitar a tentativa de clonar funções ou símbolos, pois isso resultará em um erro. Além disso, objetos que são instâncias de classes personalizadas podem não se comportar como esperado se não forem manipulados corretamente.
- **Performance**: Para objetos muito grandes ou complexos, a clonagem pode ser um processo demorado. É importante considerar se a clonagem é realmente necessária em seu caso de uso.
- **Ciclos de Referência**: Embora o `structuredClone` lide com referências circulares, é importante ter cuidado ao manipular esses tipos de objetos, pois o comportamento pode ser inesperado.

## Resumo em Uma Linha
A função `structuredClone` em JavaScript oferece uma maneira eficaz de realizar clonagens profundas de objetos, incluindo estruturas complexas, preservando suas propriedades e referências.