<!--
Meta Description: # Fence em JavaScript: Controle de Acesso e Encapsulamento de Código ## Sinopse O conceito de "Fence" (cerca) em JavaScript refere-se a práticas e pad...
Meta Keywords: javascript, que, console, log, código
-->

# Fence em JavaScript: Controle de Acesso e Encapsulamento de Código

## Sinopse
O conceito de "Fence" (cerca) em JavaScript refere-se a práticas e padrões que ajudam a encapsular código, controlando o acesso a variáveis e funções, promovendo um melhor gerenciamento do escopo e prevenção de conflitos.

## Documentação
### Propósito
O "Fence" em JavaScript é utilizado para isolar partes do código, garantindo que variáveis e funções não sejam acessíveis globalmente, e para evitar conflitos de nome entre diferentes partes de um programa. Essa prática é essencial em ambientes de desenvolvimento modular e em aplicações de grande escala.

### Uso
O conceito pode ser implementado através de módulos, closures e IIFE (Immediately Invoked Function Expressions). Esses métodos ajudam a criar um espaço de nome separado, limitando a visibilidade das variáveis e funções.

#### Módulos
Os módulos em JavaScript permitem que você agrupe código em um único arquivo ou em vários arquivos, controlando quais partes do código são expostas publicamente.

```javascript
// meuModulo.js
const meuModulo = (() => {
    const privado = "Isto é um valor privado.";
    
    return {
        publico: () => "Isto é um valor público.",
    };
})();

console.log(meuModulo.publico()); // "Isto é um valor público."
console.log(meuModulo.privado);    // undefined
```

#### Closures
As closures permitem que funções "lembram" do ambiente em que foram criadas. Isso é útil para encapsular variáveis.

```javascript
function criarContador() {
    let contagem = 0;
    return {
        incrementar: () => ++contagem,
        obterContagem: () => contagem
    };
}

const contador = criarContador();
console.log(contador.incrementar()); // 1
console.log(contador.obterContagem()); // 1
```

#### IIFE
IIFE são funções que são executadas assim que são definidas, criando um escopo separado.

```javascript
(function() {
    var escopoPrivado = "Estou dentro da IIFE!";
    console.log(escopoPrivado);
})();

console.log(typeof escopoPrivado); // undefined
```

## Exemplos
### Exemplo de Módulo
```javascript
// moduloExemplo.js
const moduloExemplo = (() => {
    const segredo = "Este é um segredo.";
    
    return {
        revelarSegredo: () => segredo,
    };
})();

console.log(moduloExemplo.revelarSegredo()); // "Este é um segredo."
```

### Exemplo de Closure
```javascript
function contador() {
    let contagem = 0;
    return function() {
        contagem++;
        return contagem;
    };
}

const contar = contador();
console.log(contar()); // 1
console.log(contar()); // 2
```

### Exemplo de IIFE
```javascript
(function() {
    var mensagem = "Olá, Mundo!";
    console.log(mensagem);
})();
```

## Explicação
### Armadilhas Comuns
- **Acesso Global Indesejado**: Não encapsular variáveis pode levar a conflitos de nome, especialmente em projetos grandes ou ao usar bibliotecas de terceiros.
- **Performance**: Embora o encapsulamento seja bom, o uso excessivo de closures pode levar a um aumento no uso de memória, especialmente se forem referenciadas variáveis grandes.

### Notas Adicionais
- O uso de ES6 (ECMAScript 2015) trouxe melhorias significativas, como a introdução de módulos nativos (`import` e `export`), que facilitam ainda mais o encapsulamento.
- O "Fence" não é um recurso específico da linguagem, mas sim um padrão de design de código que se aplica a muitos contextos de programação.

## Resumo em Uma Linha
O "Fence" em JavaScript refere-se a práticas de encapsulamento de código que controlam o acesso a variáveis e funções, promovendo uma melhor organização e prevenção de conflitos.