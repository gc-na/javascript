<!--
Meta Description: # SVGLinearGradientElement: Gradientes Lineares em SVG com JavaScript ## Sinopse O `SVGLinearGradientElement` é uma interface do DOM que representa um...
Meta Keywords: gradiente, lineargradient, stop, svg, setattribute
-->

# SVGLinearGradientElement: Gradientes Lineares em SVG com JavaScript

## Sinopse
O `SVGLinearGradientElement` é uma interface do DOM que representa um elemento de gradiente linear em SVG, permitindo a criação de transições suaves entre cores em gráficos vetoriais escaláveis através de JavaScript.

## Documentação
O `SVGLinearGradientElement` é utilizado para definir um gradiente linear que pode ser aplicado a formas SVG, como retângulos, círculos e caminhos. Ele especifica como as cores devem transitar ao longo de uma linha definida por dois pontos: o ponto inicial e o ponto final do gradiente.

### Propriedades Principais
- **x1, y1**: Coordenadas do ponto inicial do gradiente.
- **x2, y2**: Coordenadas do ponto final do gradiente.
- **gradientUnits**: Especifica o sistema de coordenadas para o gradiente.
- **gradientTransform**: Permite aplicar uma transformação ao gradiente.

### Métodos
- **setAttribute(name, value)**: Modifica o valor de um atributo.
- **getAttribute(name)**: Retorna o valor de um atributo.

### Uso
Para usar o `SVGLinearGradientElement`, você deve criar um elemento SVG e, em seguida, adicionar um gradiente linear como parte de seus definições de estilo.

## Exemplos
### Exemplo Simples de Gradiente Linear
```html
<svg width="200" height="200">
  <defs>
    <linearGradient id="gradienteExemplo" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="200" height="200" fill="url(#gradienteExemplo)" />
</svg>
```

### Manipulando Gradiente com JavaScript
```javascript
const svgNS = "http://www.w3.org/2000/svg";
const linearGradient = document.createElementNS(svgNS, "linearGradient");
linearGradient.setAttribute("id", "gradienteDinamico");
linearGradient.setAttribute("x1", "0%");
linearGradient.setAttribute("y1", "0%");
linearGradient.setAttribute("x2", "100%");
linearGradient.setAttribute("y2", "0%");

const stop1 = document.createElementNS(svgNS, "stop");
stop1.setAttribute("offset", "0%");
stop1.setAttribute("style", "stop-color:rgb(0,255,0);stop-opacity:1");
linearGradient.appendChild(stop1);

const stop2 = document.createElementNS(svgNS, "stop");
stop2.setAttribute("offset", "100%");
stop2.setAttribute("style", "stop-color:rgb(0,0,255);stop-opacity:1");
linearGradient.appendChild(stop2);

document.querySelector("svg defs").appendChild(linearGradient);
```

## Explicação
Embora o `SVGLinearGradientElement` seja uma ferramenta poderosa para criar transições de cores, alguns erros comuns podem ocorrer. Por exemplo, não definir corretamente as coordenadas `x1`, `y1`, `x2` e `y2` pode resultar em um gradiente inesperado. Além disso, certifique-se de que o gradiente está referenciado corretamente no elemento que o utiliza, caso contrário, o preenchimento não será aplicado.

Outro ponto importante é que as cores devem ser definidas corretamente usando o formato de cor suportado pelo SVG, como `rgb()`, `rgba()`, `hex`, entre outros.

## Resumo em Uma Linha
O `SVGLinearGradientElement` permite a criação de gradientes lineares em SVG, proporcionando transições de cores suaves em gráficos vetoriais através de JavaScript.