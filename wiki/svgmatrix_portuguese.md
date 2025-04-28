<!--
Meta Description: # SVGMatrix: Manipulação de Matrizes SVG com JavaScript ## Sinopse O SVGMatrix é uma interface do DOM SVG que permite a manipulação de matrizes de tra...
Meta Keywords: svg, uma, var, svgmatrix, javascript
-->

# SVGMatrix: Manipulação de Matrizes SVG com JavaScript

## Sinopse
O SVGMatrix é uma interface do DOM SVG que permite a manipulação de matrizes de transformação em gráficos vetoriais escaláveis (SVG) utilizando JavaScript. Essa funcionalidade é essencial para realizar transformações como translação, rotação, escala e inclinação em elementos SVG.

## Documentação
### O que é SVGMatrix?
SVGMatrix é uma representação de uma matriz 2D que pode ser usada para transformar elementos em um espaço SVG. Ela é parte da especificação SVG e está disponível nos navegadores modernos. A matriz é utilizada para aplicar transformações geométricas nos elementos SVG, permitindo a manipulação visual e a animação.

### Proprósito
O propósito do SVGMatrix é fornecer uma forma programática de aplicar e combinar transformações sobre elementos SVG, facilitando a criação de gráficos dinâmicos e interativos.

### Uso
Para utilizar a SVGMatrix, você pode criar uma nova instância utilizando o método `createSVGMatrix()` do contexto SVG. Uma vez criada, a matriz pode ser manipulada por meio de métodos como `translate()`, `rotate()`, `scale()`, e `invert()`. As transformações podem ser combinadas para criar efeitos complexos.

#### Exemplo de Criação
```javascript
var svg = document.getElementById("meuSVG");
var matrix = svg.createSVGMatrix();
```

## Exemplos
### Exemplo 1: Translação
```javascript
var svg = document.getElementById("meuSVG");
var matrix = svg.createSVGMatrix().translate(50, 50);
```
Esse exemplo move um elemento SVG 50 unidades para a direita e 50 unidades para baixo.

### Exemplo 2: Rotação
```javascript
var svg = document.getElementById("meuSVG");
var matrix = svg.createSVGMatrix().rotate(45);
```
Aqui, o elemento SVG é rotacionado em 45 graus.

### Exemplo 3: Escala
```javascript
var svg = document.getElementById("meuSVG");
var matrix = svg.createSVGMatrix().scale(2);
```
Este exemplo aumenta o tamanho do elemento SVG em 200%.

### Exemplo 4: Combinação de Transformações
```javascript
var svg = document.getElementById("meuSVG");
var matrix = svg.createSVGMatrix().translate(50, 50).rotate(45).scale(2);
```
Nesse caso, o elemento é primeiramente transladado, depois rotacionado e, por último, escalado.

## Explicação
### Armadilhas Comuns
1. **Ordem das Transformações**: A ordem em que as transformações são aplicadas é crucial. Por exemplo, aplicar uma rotação antes de uma translação pode resultar em um comportamento inesperado.
2. **Matrizes não Mutáveis**: As operações em SVGMatrix não alteram a matriz original, mas retornam uma nova matriz. Isso pode levar a confusões se não for observado.
3. **Compatibilidade do Navegador**: Embora a maioria dos navegadores modernos suporte SVGMatrix, sempre verifique a compatibilidade se você estiver visando suporte a navegadores mais antigos.

## Resumo em uma linha
SVGMatrix é uma interface em JavaScript que permite a manipulação programática de matrizes de transformação para elementos SVG, facilitando a criação de gráficos dinâmicos.