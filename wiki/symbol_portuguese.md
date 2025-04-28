<!--
Meta Description: # Símbolo em JavaScript: Entendendo o Tipo de Dado Único ## Sinopse O tipo de dado `Symbol` em JavaScript é uma nova primitiva introduzida no ECMAScri...
Meta Keywords: symbol, que, símbolos, javascript, const
-->

# Símbolo em JavaScript: Entendendo o Tipo de Dado Único

## Sinopse
O tipo de dado `Symbol` em JavaScript é uma nova primitiva introduzida no ECMAScript 2015 (ES6) que permite a criação de identificadores únicos e imutáveis, sendo útil para propriedades de objetos.

## Documentação
O `Symbol` é um tipo de dado primitivo que é usado principalmente para criar chaves de propriedades de objetos que são únicas e não colidíveis. Cada símbolo criado é único, mesmo que dois símbolos tenham o mesmo descrição. A sintaxe básica para criar um símbolo é:

```javascript
let meuSimbolo = Symbol('descrição opcional');
```

### Propósito
O propósito principal dos símbolos é evitar conflitos de propriedade em objetos, especialmente quando diferentes partes de um código podem estar adicionando propriedades ao mesmo objeto.

### Uso
Os símbolos são usados como chaves de propriedades em objetos. Por exemplo:

```javascript
const id = Symbol('id');
const usuario = {
    [id]: 123,
    nome: 'João'
};
```

Nesse exemplo, a propriedade `id` é única, e não pode ser acessada através de métodos normais de enumeração de propriedades.

### Detalhes
- **Imutabilidade**: Um símbolo é imutável, ou seja, uma vez criado, seu valor não pode ser alterado.
- **Global Symbols**: A função `Symbol.for()` permite que você registre e recupere símbolos globais, garantindo que você possa obter o mesmo símbolo em diferentes partes do código.

## Exemplos
### Criação de Símbolos
```javascript
const simbolo1 = Symbol('teste');
const simbolo2 = Symbol('teste');

console.log(simbolo1 === simbolo2); // false
```

### Uso em Objetos
```javascript
const cor = Symbol('cor');
const carro = {
    [cor]: 'vermelho',
    modelo: 'Fusca'
};

console.log(carro[cor]); // 'vermelho'
```

### Símbolos Globais
```javascript
const simboloGlobal = Symbol.for('globalSymbol');
const outroSimboloGlobal = Symbol.for('globalSymbol');

console.log(simboloGlobal === outroSimboloGlobal); // true
```

## Explicação
Um dos principais erros ao trabalhar com símbolos é esperar que eles sejam enumeráveis em loops, como `for...in` ou `Object.keys()`. Os símbolos não aparecem nesses loops, a menos que você utilize `Object.getOwnPropertySymbols(obj)` para acessá-los. Além disso, ao usar `Symbol.for()`, é importante lembrar que símbolos registrados globalmente podem ser acessados em qualquer parte do código, o que pode levar a colisões se não forem gerenciados adequadamente.

## Resumo em Uma Linha
O `Symbol` é um tipo de dado único e imutável em JavaScript, usado para criar chaves de propriedades de objetos que evitam conflitos.