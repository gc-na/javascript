<!--
Meta Description: # DOMRectList: Entendendo a Lista de Retângulos no JavaScript ## Sinopse O `DOMRectList` é uma interface no JavaScript que representa uma lista de obj...
Meta Keywords: domrectlist, retângulos, elemento, que, uma
-->

# DOMRectList: Entendendo a Lista de Retângulos no JavaScript

## Sinopse
O `DOMRectList` é uma interface no JavaScript que representa uma lista de objetos `DOMRect`, permitindo manipular e acessar múltiplos retângulos de forma eficiente. É frequentemente utilizado em operações relacionadas a geometria e posicionamento de elementos na página.

## Documentação
A interface `DOMRectList` é uma coleção de objetos `DOMRect`. Cada objeto `DOMRect` contém informações sobre a posição e dimensões de um retângulo, incluindo propriedades como `x`, `y`, `width`, e `height`. A principal função do `DOMRectList` é facilitar a manipulação de múltiplos retângulos, que podem ser retornados por métodos como `getClientRects()` de um elemento DOM.

### Uso
Um `DOMRectList` é geralmente obtido ao chamar métodos que retornam retângulos relativos a um elemento DOM. Por exemplo, ao usar `getClientRects()` em um elemento, você obtém um `DOMRectList` que contém todos os retângulos que representam a área ocupada por aquele elemento na tela.

#### Propriedades Principais:
- `length`: Retorna o número de `DOMRect` na lista.
- `item(index)`: Retorna o `DOMRect` no índice especificado.

## Exemplos

### Exemplo 1: Obtendo Retângulos de um Elemento
```javascript
// Seleciona um elemento da página
const elemento = document.querySelector('#meuElemento');

// Obtém a lista de retângulos
const retangulos = elemento.getClientRects();

// Itera sobre a lista de retângulos
for (let i = 0; i < retangulos.length; i++) {
    console.log(`Retângulo ${i}:`, retangulos[i]);
}
```

### Exemplo 2: Acessando Propriedades de um Retângulo
```javascript
const retangulos = document.querySelector('#meuElemento').getClientRects();
if (retangulos.length > 0) {
    const primeiroRetangulo = retangulos[0];
    console.log(`Posição X: ${primeiroRetangulo.x}, Posição Y: ${primeiroRetangulo.y}`);
    console.log(`Largura: ${primeiroRetangulo.width}, Altura: ${primeiroRetangulo.height}`);
}
```

## Explicação
- **Evitar Confusões**: Um erro comum é assumir que `DOMRectList` é um array comum. Embora possua um método `length` e um método `item()`, não suporta todas as operações de um array, como `forEach` ou `map`.
- **Compatibilidade**: O `DOMRectList` é amplamente suportado em navegadores modernos, mas sempre verifique a compatibilidade com versões antigas se o seu projeto precisar suportar navegadores desatualizados.
- **Performance**: Ao trabalhar com muitos elementos na DOM, o uso excessivo de `getClientRects()` pode afetar a performance. Utilize-o de forma criteriosa.

## Resumo em Uma Linha
`DOMRectList` é uma interface em JavaScript que representa uma coleção de retângulos, facilitando a manipulação de múltiplas áreas ocupadas por elementos DOM na página.