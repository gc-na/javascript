<!--
Meta Description: # DOMRectReadOnly: Entenda Como Funciona no JavaScript ## Sinopse DOMRectReadOnly é uma interface em JavaScript que representa um retângulo (rectangle...
Meta Keywords: retângulo, posição, domrectreadonly, dimensões, elemento
-->

# DOMRectReadOnly: Entenda Como Funciona no JavaScript

## Sinopse
DOMRectReadOnly é uma interface em JavaScript que representa um retângulo (rectangle) em um espaço bidimensional, fornecendo informações sobre sua posição e dimensões. Essa interface é especialmente útil ao trabalhar com elementos do DOM e suas dimensões.

## Documentação
A interface DOMRectReadOnly é utilizada para descrever as dimensões e a posição de um retângulo no contexto de um elemento DOM. Ela fornece propriedades que permitem acessar informações como a largura (width), altura (height), e a posição do retângulo em relação ao sistema de coordenadas.

### Propriedades
- **x**: A coordenada x do canto superior esquerdo do retângulo.
- **y**: A coordenada y do canto superior esquerdo do retângulo.
- **width**: A largura do retângulo.
- **height**: A altura do retângulo.
- **top**: A posição vertical do topo do retângulo (equivalente a y).
- **right**: A posição horizontal da borda direita do retângulo (x + width).
- **bottom**: A posição vertical da borda inferior do retângulo (y + height).
- **left**: A posição horizontal da borda esquerda do retângulo (equivalente a x).

### Uso
O DOMRectReadOnly é frequentemente utilizado em conjunto com métodos como `getBoundingClientRect()`, que retorna um objeto DOMRectReadOnly representando a posição e dimensões de um elemento na viewport.

#### Exemplo de Uso
```javascript
const elemento = document.querySelector('#meuElemento');
const retangulo = elemento.getBoundingClientRect();

console.log(`Posição: (${retangulo.x}, ${retangulo.y})`);
console.log(`Dimensões: ${retangulo.width} x ${retangulo.height}`);
```

## Exemplos
### Exemplo 1: Acessando Propriedades
```javascript
const box = document.getElementById('caixa');
const rect = box.getBoundingClientRect();

console.log(`Top: ${rect.top}, Left: ${rect.left}`);
```

### Exemplo 2: Cálculo da Área
```javascript
const rect = document.getElementById('caixa').getBoundingClientRect();
const area = rect.width * rect.height;

console.log(`Área do retângulo: ${area}`);
```

## Explicação
Um erro comum ao utilizar o DOMRectReadOnly é não considerar o contexto de exibição (viewport) e as possíveis transformações CSS aplicadas ao elemento (como escalas ou rotações). Isso pode resultar em dimensões ou posições inesperadas. Além disso, como o DOMRectReadOnly é um objeto imutável, não é possível alterá-lo diretamente; qualquer modificação deve ser feita no elemento original.

Lembre-se de que as propriedades retornadas por `getBoundingClientRect()` são relacionadas à viewport atual e podem mudar conforme a página é redimensionada ou o elemento é movido.

## Resumo em Uma Linha
DOMRectReadOnly é uma interface JavaScript que fornece informações sobre a posição e dimensões de um retângulo em relação ao DOM e à viewport.