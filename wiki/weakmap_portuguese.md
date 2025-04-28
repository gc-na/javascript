<!--
Meta Description: # WeakMap em JavaScript: Entenda Como Funciona e Quando Usar ## Sinopse WeakMap é uma coleção de pares chave-valor em JavaScript onde as chaves são ob...
Meta Keywords: weakmap, chave, que, valor, uma
-->

# WeakMap em JavaScript: Entenda Como Funciona e Quando Usar

## Sinopse
WeakMap é uma coleção de pares chave-valor em JavaScript onde as chaves são objetos e os valores podem ser de qualquer tipo. Diferente de um Map tradicional, as chaves em um WeakMap são "fracas", o que significa que se não houver referências a uma chave, ela pode ser coletada pelo garbage collector, permitindo uma melhor gestão de memória.

## Documentação

### O que é WeakMap?
WeakMap é um objeto que permite armazenar dados associados a objetos sem impedir que esses objetos sejam coletados pelo garbage collector. Isso é útil para situações onde você deseja associar metadados a objetos sem comprometer seu ciclo de vida.

### Uso do WeakMap
Você pode criar um WeakMap usando o construtor `WeakMap()`. A sintaxe básica é:
```javascript
const meuWeakMap = new WeakMap();
```

#### Métodos do WeakMap
- `set(chave, valor)`: Adiciona um novo par chave-valor ao WeakMap.
- `get(chave)`: Retorna o valor associado a uma chave específica.
- `has(chave)`: Retorna um booleano indicando se o WeakMap contém a chave especificada.
- `delete(chave)`: Remove o par chave-valor associado a uma chave específica.

### Detalhes Importantes
- As chaves de um WeakMap devem ser objetos. Tipos primitivos (como números e strings) não podem ser usados como chaves.
- O WeakMap não tem um método para iterar sobre suas chaves ou valores, diferentemente de um Map regular.
- As chaves são "fracas", ou seja, se não houver outras referências a um objeto que serve como chave, ele pode ser removido da memória, permitindo o garbage collection.

## Exemplos

### Exemplo Básico
```javascript
const objeto1 = {};
const objeto2 = {};
const meuWeakMap = new WeakMap();

meuWeakMap.set(objeto1, 'Valor 1');
meuWeakMap.set(objeto2, 'Valor 2');

console.log(meuWeakMap.get(objeto1)); // Saída: 'Valor 1'
console.log(meuWeakMap.has(objeto2)); // Saída: true

meuWeakMap.delete(objeto1);
console.log(meuWeakMap.has(objeto1)); // Saída: false
```

### Exemplo com Garbage Collection
```javascript
let chave = {};
let meuWeakMap = new WeakMap();

meuWeakMap.set(chave, 'Valor');

console.log(meuWeakMap.get(chave)); // Saída: 'Valor'

// Removendo a referência
chave = null;

// Aqui, o garbage collector pode remover a chave do WeakMap
```

## Explicação
Um dos principais desafios ao usar WeakMap é que ele não permite a iteração, o que pode ser uma limitação se você precisar acessar todos os pares chave-valor. Além disso, como as chaves são "fracas", é importante entender que uma vez que não houver mais referências a uma chave, o valor associado pode ser perdido sem aviso.

Outro ponto a considerar é que o WeakMap é ideal para armazenar dados que não precisam persistir indefinidamente, como informações temporárias ou de configuração que podem ser removidas automaticamente quando os objetos não são mais necessários.

## Resumo em uma Linha
WeakMap é uma coleção de pares chave-valor em JavaScript que permite o uso de objetos como chaves sem impedir sua coleta pelo garbage collector, oferecendo uma forma eficiente de gerenciar memória.