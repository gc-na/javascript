<!--
Meta Description: # SVGFEDistantLightElement: Entendendo o Elemento de Luz Distante no JavaScript ## Sinopse O `SVGFEDistantLightElement` é um elemento do SVG que defin...
Meta Keywords: luz, svg, filter, que, svgfedistantlightelement
-->

# SVGFEDistantLightElement: Entendendo o Elemento de Luz Distante no JavaScript

## Sinopse
O `SVGFEDistantLightElement` é um elemento do SVG que define uma fonte de luz distante em um efeito de filtro SVG, permitindo a criação de sombras e iluminações em gráficos vetoriais escaláveis.

## Documentação
O `SVGFEDistantLightElement` é parte da especificação SVG e é utilizado em conjunto com filtros SVG para simular efeitos de iluminação em elementos gráficos. Este elemento especifica a direção de uma fonte de luz que está a uma distância infinita, o que é especialmente útil para criar sombras realistas em elementos gráficos.

### Propósito
O principal objetivo do `SVGFEDistantLightElement` é fornecer uma forma de definir a direção da luz que incide sobre um objeto em um contexto SVG. Isso é crucial para a criação de efeitos visuais dinâmicos e atraentes em aplicações web que utilizam gráficos vetoriais.

### Uso
Para utilizar o `SVGFEDistantLightElement`, você deve incluí-lo dentro de um elemento `<filter>` em um documento SVG. A direção da luz é determinada pelos atributos `azimuth` e `elevation`, que especificam a posição da fonte de luz em relação ao plano do objeto.

```html
<svg width="200" height="200">
  <defs>
    <filter id="f1" x="0" y="0">
      <feDiffuseLighting in="SourceGraphic" lighting-color="white">
        <feDistantLight azimuth="45" elevation="30"/>
      </feDiffuseLighting>
    </filter>
  </defs>
  <rect width="200" height="200" fill="blue" filter="url(#f1)"/>
</svg>
```

## Exemplos
### Exemplo Básico
Neste exemplo, um retângulo azul é iluminado por uma fonte de luz distante.

```html
<svg width="300" height="300">
  <defs>
    <filter id="lightEffect">
      <feDiffuseLighting in="SourceGraphic" lighting-color="yellow">
        <feDistantLight azimuth="120" elevation="45" />
      </feDiffuseLighting>
    </filter>
  </defs>
  <circle cx="150" cy="150" r="100" fill="green" filter="url(#lightEffect)" />
</svg>
```

### Exemplo de Variação de Luz
Neste exemplo, a elevação e a azimute da luz são alterados para demonstrar diferentes efeitos de iluminação.

```html
<svg width="300" height="300">
  <defs>
    <filter id="dynamicLight">
      <feDiffuseLighting in="SourceGraphic" lighting-color="pink">
        <feDistantLight azimuth="90" elevation="60" />
      </feDiffuseLighting>
    </filter>
  </defs>
  <rect x="50" y="50" width="200" height="200" fill="red" filter="url(#dynamicLight)" />
</svg>
```

## Explicação
Um dos erros comuns ao usar o `SVGFEDistantLightElement` é não entender corretamente os atributos `azimuth` e `elevation`. O `azimuth` representa a direção horizontal da luz em graus, enquanto o `elevation` representa a altura da luz em graus. Se os valores não forem definidos adequadamente, o efeito de iluminação pode não aparecer como esperado.

Além disso, é importante lembrar que a cor da luz pode ser ajustada usando o atributo `lighting-color`, e que este elemento só tem efeito em um contexto de filtro onde a luz e a sombra são aplicadas.

## Resumo em Uma Linha
O `SVGFEDistantLightElement` é um componente SVG que define a direção de uma fonte de luz distante, essencial para criar efeitos de iluminação realistas em gráficos vetoriais usando JavaScript.