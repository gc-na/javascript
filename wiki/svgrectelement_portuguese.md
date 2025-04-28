<!--
Meta Description: # SVGRectElement em JavaScript: Manipulando Retângulos em SVG ## Sinopse O `SVGRectElement` é uma interface do DOM em JavaScript que representa um ele...
Meta Keywords: svg, retângulo, setattribute, rect, para
-->

# SVGRectElement em JavaScript: Manipulando Retângulos em SVG

## Sinopse
O `SVGRectElement` é uma interface do DOM em JavaScript que representa um elemento retangular dentro de um gráfico SVG (Scalable Vector Graphics). Ele permite criar, manipular e interagir com retângulos em uma página web de forma programática.

## Documentação
O `SVGRectElement` herda de `SVGGeometryElement` e é utilizado para definir retângulos em gráficos SVG. Este elemento é especialmente útil para desenhar formas geométricas simples, como retângulos, que podem ser estilizados e animados com CSS e JavaScript. 

### Propriedades Principais
- **x**: Define a coordenada X do canto superior esquerdo do retângulo.
- **y**: Define a coordenada Y do canto superior esquerdo do retângulo.
- **width**: Define a largura do retângulo.
- **height**: Define a altura do retângulo.
- **rx**: Define o raio dos cantos arredondados do retângulo.
- **ry**: Define o raio dos cantos arredondados do retângulo (separado do `rx`).

### Métodos
O `SVGRectElement` não possui métodos específicos, mas pode ser manipulado utilizando métodos do DOM padrão para elementos SVG, como `setAttribute()` e `getAttribute()`.

## Exemplos

### Exemplo Básico de Criação de um Retângulo SVG
```javascript
// Criando um elemento SVG
const svgNamespace = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNamespace, "svg");
svg.setAttribute("width", "200");
svg.setAttribute("height", "200");

// Criando um retângulo
const rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("x", "10");
rect.setAttribute("y", "10");
rect.setAttribute("width", "100");
rect.setAttribute("height", "50");
rect.setAttribute("fill", "blue");

// Adicionando o retângulo ao SVG
svg.appendChild(rect);
document.body.appendChild(svg);
```

### Exemplo de Modificação de Propriedades de um Retângulo Existente
```javascript
const existingRect = document.querySelector('rect');
existingRect.setAttribute('fill', 'red'); // Muda a cor de preenchimento para vermelho
existingRect.setAttribute('width', '150'); // Altera a largura para 150
```

## Explicação
Embora o `SVGRectElement` seja uma ferramenta poderosa para desenhar retângulos, é importante ter em mente algumas armadilhas comuns:

- **Coordenadas e Sistema de Referência**: As coordenadas (x, y) são relativas ao sistema de coordenadas do elemento pai SVG. Se o SVG for redimensionado, isso pode afetar a posição do retângulo.
- **Raios de Canto**: A propriedade `rx` e `ry` só têm efeito se o retângulo não estiver sendo desenhado como um retângulo "puro". Se ambos os valores forem 0, o retângulo terá cantos quadrados.
- **Compatibilidade com Navegadores**: Embora a maioria dos navegadores modernos suporte SVG, sempre é bom testar a funcionalidade em diferentes plataformas para garantir compatibilidade.

## Resumo em Uma Linha
O `SVGRectElement` em JavaScript permite a criação e manipulação de retângulos em gráficos SVG, oferecendo uma maneira flexível de trabalhar com formas em aplicações web.