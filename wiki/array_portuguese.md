<!--
Meta Description: # Arrays em JavaScript: Tudo Que Você Precisa Saber ## Sinopse Arrays em JavaScript são estruturas de dados que permitem armazenar múltiplos valores e...
Meta Keywords: array, javascript, que, elementos, arrays
-->

# Arrays em JavaScript: Tudo Que Você Precisa Saber

## Sinopse
Arrays em JavaScript são estruturas de dados que permitem armazenar múltiplos valores em uma única variável. Eles são dinâmicos e podem conter elementos de diferentes tipos, como números, strings e até objetos.

## Documentação
Os arrays em JavaScript são objetos que possuem uma propriedade especial chamada `length`, que indica o número de elementos contidos. Eles são utilizados para armazenar coleções de dados de forma ordenada e oferecem vários métodos embutidos que facilitam a manipulação de seus dados.

### Criação de Arrays
Você pode criar um array de várias maneiras:

1. Usando colchetes:
   ```javascript
   const frutas = ['maçã', 'banana', 'laranja'];
   ```

2. Usando o construtor `Array`:
   ```javascript
   const numeros = new Array(1, 2, 3, 4);
   ```

3. Usando o método `Array.of`:
   ```javascript
   const cores = Array.of('vermelho', 'verde', 'azul');
   ```

### Acesso e Modificação
Os elementos de um array podem ser acessados e modificados através de seus índices:
```javascript
console.log(frutas[0]); // 'maçã'
frutas[1] = 'manga';
console.log(frutas); // ['maçã', 'manga', 'laranja']
```

### Métodos Comuns
Alguns métodos comuns dos arrays incluem:
- `push()`: Adiciona um ou mais elementos ao final do array.
- `pop()`: Remove o último elemento do array.
- `shift()`: Remove o primeiro elemento do array.
- `unshift()`: Adiciona um ou mais elementos ao início do array.
- `map()`: Cria um novo array com os resultados da chamada de uma função para cada elemento do array.
- `filter()`: Cria um novo array com todos os elementos que passaram no teste implementado pela função fornecida.

## Exemplos
### Exemplo 1: Criando e Manipulando um Array
```javascript
const animais = ['cachorro', 'gato', 'pássaro'];
animais.push('peixe'); // Adiciona 'peixe' ao final
console.log(animais); // ['cachorro', 'gato', 'pássaro', 'peixe']
```

### Exemplo 2: Usando o Método `map`
```javascript
const numeros = [1, 2, 3, 4];
const quadrados = numeros.map(num => num * num);
console.log(quadrados); // [1, 4, 9, 16]
```

### Exemplo 3: Filtrando Elementos
```javascript
const valores = [5, 12, 8, 130, 44];
const maioresQue10 = valores.filter(valor => valor > 10);
console.log(maioresQue10); // [12, 130, 44]
```

## Explicação
Um erro comum ao trabalhar com arrays é a confusão sobre índices, já que eles começam em 0. Assim, `array[0]` refere-se ao primeiro elemento, não ao segundo. Além disso, o método `splice()` pode causar alterações inesperadas, pois não apenas remove elementos, mas também pode adicionar novos no lugar.

Outro ponto a ser observado é que os arrays em JavaScript são dinâmicos. Isso significa que você pode adicionar ou remover elementos a qualquer momento, o que pode levar a comportamento inesperado se não for gerenciado corretamente.

## Resumo em Uma Linha
Arrays em JavaScript são coleções dinâmicas que armazenam diferentes tipos de dados, permitindo fácil acesso e manipulação.