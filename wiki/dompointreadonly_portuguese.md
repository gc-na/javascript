<!--
Meta Description: # DOMPointReadOnly: Entendendo o Objeto de Ponto Imutável em JavaScript ## Sinopse O `DOMPointReadOnly` é um objeto utilizado na Web API que represent...
Meta Keywords: dompointreadonly, ponto, que, point, objeto
-->

# DOMPointReadOnly: Entendendo o Objeto de Ponto Imutável em JavaScript

## Sinopse
O `DOMPointReadOnly` é um objeto utilizado na Web API que representa um ponto em um espaço 2D ou 3D, sendo uma versão imutável do `DOMPoint`. Ele é particularmente útil em aplicações que lidam com gráficos, animações e manipulação de coordenadas.

## Documentação
O `DOMPointReadOnly` é parte da interface `DOMPoint`, que faz parte do módulo de coordenadas da API de gráficos. Este objeto é projetado para fornecer um ponto fixo, uma vez que suas propriedades não podem ser alteradas após a criação.

### Propósito
O `DOMPointReadOnly` é utilizado para representar coordenadas em um espaço, podendo ser utilizado em contextos de transformação de elementos gráficos, como `Canvas` ou operações de desenho em SVG.

### Uso
A instância de `DOMPointReadOnly` é criada normalmente através da classe `DOMPoint`. Uma vez que um objeto `DOMPointReadOnly` é gerado, suas propriedades `x`, `y`, `z`, e `w` se tornam acessíveis, mas não podem ser alteradas diretamente.

#### Propriedades
- `x`: A coordenada X do ponto.
- `y`: A coordenada Y do ponto.
- `z`: A coordenada Z do ponto (opcional, aplicável em 3D).
- `w`: A coordenada homogênea (opcional, aplicável em 3D).

## Exemplos
Aqui estão alguns exemplos que demonstram como utilizar o `DOMPointReadOnly` em JavaScript:

### Exemplo 1: Criando um DOMPointReadOnly
```javascript
// Cria um novo DOMPoint
const point = new DOMPoint(10, 20);

// Acessa as propriedades do ponto
console.log(point.x); // 10
console.log(point.y); // 20

// O ponto é imutável
point.x = 30; // Isso não terá efeito e gerará um erro em modo estrito
```

### Exemplo 2: Utilizando com Canvas
```javascript
const canvas = document.querySelector('canvas');
const ctx = canvas.getContext('2d');

// Cria um DOMPointReadOnly
const point = new DOMPoint(100, 150);

// Desenha um ponto no canvas usando as coordenadas do DOMPointReadOnly
ctx.fillRect(point.x, point.y, 5, 5); // Desenha um pequeno quadrado na posição (100, 150)
```

## Explicação
Um ponto a ser observado ao trabalhar com `DOMPointReadOnly` é que, por ser um objeto imutável, qualquer tentativa de modificar suas propriedades resultará em um erro. Isso é uma característica importante para manter a integridade dos dados, especialmente em aplicações onde as coordenadas precisam ser fixas após a sua criação.

Além disso, ao utilizar `DOMPointReadOnly`, é comum usar a função `DOMMatrix` para realizar transformações, como translação e rotação, que podem gerar novos pontos a partir de um ponto existente.

## Resumo em Uma Linha
O `DOMPointReadOnly` é um objeto imutável que representa um ponto em um espaço 2D ou 3D, utilizado em manipulações gráficas em JavaScript.