<!--
Meta Description: # WeakSet em JavaScript: O que é e Como Usar ## Sinopse O `WeakSet` é uma coleção de objetos em JavaScript que permite armazenar referências fracas a ...
Meta Keywords: weakset, objetos, que, não, javascript
-->

# WeakSet em JavaScript: O que é e Como Usar

## Sinopse
O `WeakSet` é uma coleção de objetos em JavaScript que permite armazenar referências fracas a objetos, garantindo que esses objetos possam ser coletados pelo garbage collector quando não forem mais referenciados em outros lugares.

## Documentação
O `WeakSet` é uma estrutura de dados introduzida no ECMAScript 2015 (ES6) que oferece uma maneira de armazenar coleções de objetos sem impedir que esses objetos sejam coletados pelo garbage collector. Isso significa que, ao contrário de um `Set`, os objetos armazenados em um `WeakSet` não aumentam o contador de referências, permitindo que a memória seja liberada quando não houver mais referências a esses objetos.

### Criação
Você pode criar um `WeakSet` usando o construtor `WeakSet()`. Ele aceita um iterável, mas esse iterável deve conter apenas objetos.

```javascript
const weakset = new WeakSet();
```

### Métodos
O `WeakSet` possui três métodos principais:

- **add(value)**: Adiciona um objeto ao `WeakSet`.
- **delete(value)**: Remove um objeto do `WeakSet`.
- **has(value)**: Verifica se um objeto está presente no `WeakSet`.

### Restrições
- Os valores armazenados em um `WeakSet` devem ser objetos; tipos primitivos (como números ou strings) não são permitidos.
- O `WeakSet` não possui métodos para iterar sobre seus elementos, como `forEach` ou `size`.

## Exemplos
### Exemplo 1: Criando um WeakSet
```javascript
const objeto1 = {};
const objeto2 = {};
const weakset = new WeakSet([objeto1]);

console.log(weakset.has(objeto1)); // true
console.log(weakset.has(objeto2)); // false
```

### Exemplo 2: Adicionando e Removendo Objetos
```javascript
const objeto3 = {};
weakset.add(objeto2);
console.log(weakset.has(objeto2)); // true

weakset.delete(objeto1);
console.log(weakset.has(objeto1)); // false
```

### Exemplo 3: Coleta de Lixo
```javascript
let objeto4 = {};
const weakset2 = new WeakSet([objeto4]);

console.log(weakset2.has(objeto4)); // true

objeto4 = null; // O objeto pode ser coletado pelo garbage collector
```

## Explicação
Embora o `WeakSet` seja uma ferramenta poderosa, ele possui algumas peculiaridades que os desenvolvedores devem estar cientes:

- **Sem Iteração**: Você não pode iterar sobre um `WeakSet`, o que pode ser uma limitação se precisar acessar todos os elementos.
- **Coleta de Lixo**: Como os objetos em um `WeakSet` são referenciados de forma fraca, eles podem ser coletados pelo garbage collector assim que não houver mais referências a eles em outras partes do código. Isso pode levar a comportamentos inesperados se você não estiver ciente de que os objetos podem desaparecer.
- **Objetos Apenas**: O `WeakSet` aceita apenas objetos como valores. Tentar adicionar um tipo primitivo resultará em um erro.

## Resumo em Uma Linha
O `WeakSet` é uma estrutura de dados em JavaScript que permite armazenar referências fracas a objetos, facilitando a coleta de lixo automática.