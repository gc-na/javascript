<!--
Meta Description: # DOMTokenList: Manipulando Classes e Tokens em JavaScript ## Sinopse O `DOMTokenList` é uma interface que representa uma lista de tokens, como nomes ...
Meta Keywords: classes, uma, classlist, classe, elemento
-->

# DOMTokenList: Manipulando Classes e Tokens em JavaScript

## Sinopse
O `DOMTokenList` é uma interface que representa uma lista de tokens, como nomes de classes de elementos HTML, permitindo a manipulação eficiente de classes em elementos do DOM.

## Documentação

### O que é o DOMTokenList?
A interface `DOMTokenList` fornece métodos para manipular uma lista de strings que representam tokens. É comumente utilizada para manipular a propriedade `classList` de elementos HTML, permitindo adicionar, remover e verificar a presença de classes de maneira simples e eficiente.

### Propósito
O `DOMTokenList` facilita a manipulação de classes, evitando a necessidade de manipular diretamente a string de classes. Isso resulta em um código mais legível e menos propenso a erros.

### Uso
O `DOMTokenList` é acessado através da propriedade `classList` de um elemento HTML. Os principais métodos incluem:
- `add(token)`: Adiciona um token à lista.
- `remove(token)`: Remove um token da lista.
- `toggle(token)`: Alterna a presença de um token na lista. Retorna `true` se o token foi adicionado e `false` se foi removido.
- `contains(token)`: Verifica se um token está presente na lista.
- `item(index)`: Retorna o token na posição especificada.

### Exemplo
```javascript
// Seleciona um elemento HTML
const elemento = document.querySelector('.meu-elemento');

// Adiciona uma classe
elemento.classList.add('nova-classe');

// Remove uma classe
elemento.classList.remove('classe-antiga');

// Alterna uma classe
const foiAdicionado = elemento.classList.toggle('classe-toggle');

// Verifica se uma classe está presente
const temClasse = elemento.classList.contains('nova-classe');

// Acessa um item pelo índice
const primeiraClasse = elemento.classList.item(0);
```

## Explicação
Embora o `DOMTokenList` seja uma ferramenta poderosa, existem algumas armadilhas comuns:

1. **Manipulação de múltiplas classes**: O método `add` e `remove` podem receber múltiplos argumentos, permitindo adicionar ou remover várias classes de uma só vez, como `elemento.classList.add('classe1', 'classe2')`.

2. **Sensibilidade a maiúsculas**: Os nomes das classes são sensíveis a maiúsculas e minúsculas. `classList.add('Classe')` e `classList.add('classe')` são considerados diferentes.

3. **Verificação de presença**: O método `contains` é ideal para verificar a existência de uma classe antes de executar ações que dependem dela, evitando erros.

4. **Desempenho**: Manipular classes com `classList` é mais eficiente do que concatenar e modificar diretamente a string `className`, especialmente em elementos com muitas classes.

## Resumo em Uma Linha
O `DOMTokenList` é uma interface que simplifica a manipulação de classes em elementos HTML, tornando a interação com o DOM mais intuitiva e eficiente.