<!--
Meta Description: # SVGFEGaussianBlurElement: Componente JavaScript para Efeitos de Desfoque em SVG ## Sinopse O `SVGFEGaussianBlurElement` é uma interface do DOM que r...
Meta Keywords: desfoque, svg, svgfegaussianblurelement, para, filtro
-->

# SVGFEGaussianBlurElement: Componente JavaScript para Efeitos de Desfoque em SVG

## Sinopse
O `SVGFEGaussianBlurElement` é uma interface do DOM que representa um filtro SVG que aplica um efeito de desfoque gaussiano a elementos gráficos, permitindo a criação de efeitos visuais mais sofisticados em gráficos vetoriais escaláveis (SVG) com JavaScript.

## Documentação

### Propósito
O `SVGFEGaussianBlurElement` é utilizado para aplicar um desfoque gaussiano a um elemento SVG. Esta técnica é frequentemente utilizada em design gráfico para suavizar bordas, criar sombras ou efeitos de profundidade.

### Uso
Para utilizar o `SVGFEGaussianBlurElement`, você deve primeiro criar um filtro SVG e, em seguida, adicionar um elemento de desfoque gaussiano a esse filtro. O desfoque é definido por um ou mais parâmetros, como o raio do desfoque.

### Propriedades e Métodos
- **raioX** e **raioY**: Propriedades que definem a intensidade do desfoque em direções horizontal e vertical, respectivamente.
- **in1**: Especifica a entrada para o efeito de desfoque.
- **out**: Define a saída do efeito de desfoque aplicado.

Aqui está um exemplo básico de como configurar um filtro SVG com `SVGFEGaussianBlurElement`.

## Exemplos

### Exemplo Básico
```html
<svg width="200" height="200">
  <defs>
    <filter id="blurFilter">
      <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="blue" filter="url(#blurFilter)" />
</svg>
```
Neste exemplo, um retângulo azul é desenhado com um filtro de desfoque gaussiano aplicado a ele, resultando em um efeito de suavização.

### Exemplo com Raio Variável
```html
<svg width="200" height="200">
  <defs>
    <filter id="blurFilter">
      <feGaussianBlur in="SourceGraphic" stdDeviation="10" />
    </filter>
  </defs>
  <circle cx="100" cy="100" r="50" fill="red" filter="url(#blurFilter)" />
</svg>
```
Aqui, um círculo vermelho é aplicado com um desfoque mais intenso, onde o `stdDeviation` é ajustado para 10.

## Explicação
Um erro comum ao trabalhar com `SVGFEGaussianBlurElement` é não configurar corretamente o atributo `in`. Se a entrada não for especificada corretamente, o filtro pode não ser aplicado conforme o esperado. Além disso, é importante lembrar que o desfoque é baseado em valores de pixel, portanto, um valor muito alto pode resultar em um efeito excessivo que pode comprometer a legibilidade do gráfico.

## Resumo em Uma Linha
O `SVGFEGaussianBlurElement` é uma ferramenta poderosa em JavaScript para aplicar desfoques gaussianos em gráficos SVG, melhorando a estética e a profundidade visual.