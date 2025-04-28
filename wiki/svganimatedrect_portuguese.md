<!--
Meta Description: # SVGAnimatedRect: Manipulando Retângulos Animados em SVG com JavaScript ## Sinopse O `SVGAnimatedRect` é uma interface do SVG que permite a manipulaç...
Meta Keywords: rect, svg, setattribute, svganimatedrect, que
-->

# SVGAnimatedRect: Manipulando Retângulos Animados em SVG com JavaScript

## Sinopse
O `SVGAnimatedRect` é uma interface do SVG que permite a manipulação de retângulos animados, possibilitando a criação de gráficos interativos e dinâmicos em aplicações web utilizando JavaScript.

## Documentação
O `SVGAnimatedRect` é usado para representar as propriedades de um retângulo SVG que podem ser animadas. Ele fornece acesso a valores animados de atributos como largura, altura, x e y. Esta interface é especialmente útil para desenvolvedores que desejam fazer animações suaves em gráficos SVG.

### Propósito
O propósito principal do `SVGAnimatedRect` é fornecer uma maneira de animar retângulos SVG, permitindo que suas propriedades sejam alteradas ao longo do tempo em resposta a eventos ou condições específicas.

### Uso
O `SVGAnimatedRect` é utilizado como parte da interface `SVGRectElement`, que é responsável por criar um retângulo. As propriedades animadas podem ser acessadas através de atributos como `x`, `y`, `width` e `height`.

### Detalhes
O `SVGAnimatedRect` inclui as seguintes propriedades:

- **baseVal**: Representa o valor base do retângulo. Este valor não é afetado por animações.
- **animVal**: Representa o valor animado do retângulo, que muda durante a animação.

Um exemplo de uso simples seria:

```javascript
let rect = document.createElementNS("http://www.w3.org/2000/svg", "rect");
rect.setAttribute("x", 10);
rect.setAttribute("y", 10);
rect.setAttribute("width", 100);
rect.setAttribute("height", 50);
document.querySelector("svg").appendChild(rect);
```

## Exemplos

### Exemplo 1: Criando um Retângulo Simples

```javascript
const svgNS = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNS, "svg");
document.body.appendChild(svg);

const rect = document.createElementNS(svgNS, "rect");
rect.setAttribute("x", 50);
rect.setAttribute("y", 50);
rect.setAttribute("width", 200);
rect.setAttribute("height", 100);
rect.setAttribute("fill", "blue");

svg.appendChild(rect);
```

### Exemplo 2: Animando um Retângulo

```javascript
const rect = document.createElementNS(svgNS, "rect");
rect.setAttribute("x", 10);
rect.setAttribute("y", 10);
rect.setAttribute("width", 100);
rect.setAttribute("height", 100);
rect.setAttribute("fill", "red");

svg.appendChild(rect);

// Animação simples
let posX = 10;
setInterval(() => {
    posX += 1;
    rect.setAttribute("x", posX);
    if (posX > 400) posX = 10; // Reseta a posição
}, 16); // Aproximadamente 60 frames por segundo
```

## Explicação
Ao trabalhar com `SVGAnimatedRect`, é importante estar ciente de algumas dificuldades comuns:

- **Compatibilidade do Navegador**: Verifique se o suporte ao SVG está habilitado no navegador de destino, pois alguns navegadores mais antigos podem ter limitações.
- **Eventos de Animação**: As animações não são necessariamente contínuas e podem depender de outros fatores, como a taxa de atualização do navegador. Utilize `requestAnimationFrame` para melhores resultados.

Além disso, a manipulação direta de atributos SVG pode levar a comportamentos inesperados se não for tratada com cuidado. Sempre verifique as propriedades antes de aplicar animações.

## Resumo em Uma Linha
O `SVGAnimatedRect` é uma interface que permite a animação de retângulos em SVG, facilitando a criação de gráficos interativos com JavaScript.