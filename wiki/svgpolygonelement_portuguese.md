<!--
Meta Description: # SVGPolygonElement: Manipulando Polígonos SVG com JavaScript ## Sinopse O `SVGPolygonElement` é uma interface do DOM que representa um elemento `<pol...
Meta Keywords: svg, que, svgpolygonelement, points, 150
-->

# SVGPolygonElement: Manipulando Polígonos SVG com JavaScript

## Sinopse
O `SVGPolygonElement` é uma interface do DOM que representa um elemento `<polygon>` em um documento SVG, permitindo a manipulação de polígonos através de JavaScript.

## Documentação
O `SVGPolygonElement` é utilizado para criar e manipular polígonos em gráficos vetoriais escaláveis (SVG). Um polígono é definido por uma série de pontos que formam um caminho fechado. A interface `SVGPolygonElement` herda de `SVGGraphicsElement`, o que permite que polígonos tenham propriedades e métodos gráficos.

### Propriedades e Métodos
- **Propriedades:**
  - `points`: Um objeto `SVGPointList` que contém a lista de pontos que definem o polígono.
  
- **Métodos:**
  - `getAttribute(name)`: Obtém o valor do atributo especificado.
  - `setAttribute(name, value)`: Define o valor de um atributo específico.

### Uso
Para usar `SVGPolygonElement`, você deve criar um elemento `<polygon>` dentro de um SVG e, em seguida, manipulá-lo usando JavaScript. O atributo `points` é especialmente importante, pois define a forma do polígono.

## Exemplos

### Exemplo 1: Criando um Polígono Simples
```html
<svg width="200" height="200">
  <polygon id="meuPoligono" points="50,150 100,50 150,150" fill="lime" />
</svg>

<script>
  const poligono = document.getElementById('meuPoligono');
  console.log(poligono.points);
</script>
```

### Exemplo 2: Alterando os Pontos do Polígono
```html
<svg width="200" height="200">
  <polygon id="meuPoligono" points="50,150 100,50 150,150" fill="lime" />
</svg>

<script>
  const poligono = document.getElementById('meuPoligono');
  poligono.setAttribute('points', '40,140 100,40 160,140');
</script>
```

## Explicação
Um erro comum ao trabalhar com `SVGPolygonElement` é a manipulação inadequada da lista de pontos. É essencial garantir que os pontos estejam no formato correto (x,y) e que formem um caminho fechado. Além disso, a atualização do atributo `points` não atualiza automaticamente a visualização; isso deve ser feito explicitamente.

## Resumo em Uma Linha
O `SVGPolygonElement` permite a manipulação de polígonos SVG em JavaScript, facilitando a criação e modificação de formas vetoriais.