<!--
Meta Description: # SVGPreserveAspectRatio: Compreendendo o Controle de Aspecto em SVG com JavaScript ## Sinopse O atributo `preserveAspectRatio` em SVG (Scalable Vecto...
Meta Keywords: preserveaspectratio, svg, javascript, proporção, conteúdo
-->

# SVGPreserveAspectRatio: Compreendendo o Controle de Aspecto em SVG com JavaScript

## Sinopse
O atributo `preserveAspectRatio` em SVG (Scalable Vector Graphics) é uma propriedade crucial para controlar como uma imagem SVG deve ser exibida em relação ao seu contêiner. Combinado com JavaScript, permite manipulações dinâmicas e responsivas do layout gráfico.

## Documentação
O atributo `preserveAspectRatio` determina como um gráfico SVG deve ser escalado e alinhado dentro de sua caixa delimitadora. Ele é utilizado em elementos SVG como `<svg>`, `<image>`, e `<foreignObject>`, e aceita vários valores que definem o comportamento de preservação da proporção.

### Valores Comuns de `preserveAspectRatio`
- `none`: O conteúdo é escalado para preencher completamente a caixa, sem respeitar a proporção.
- `xMinYMin`: O conteúdo é alinhado à parte superior esquerda da caixa, mantendo a proporção.
- `xMidYMid`: Centraliza o conteúdo na caixa, mantendo a proporção.
- `xMaxYMax`: O conteúdo é alinhado à parte inferior direita, mantendo a proporção.
- Adicionalmente, você pode adicionar ` meet` ou ` slice` para definir se o conteúdo deve se encaixar ou preencher a caixa.

### Uso em JavaScript
Ao manipular SVG com JavaScript, você pode alterar dinamicamente o valor do atributo `preserveAspectRatio`, proporcionando uma maior flexibilidade na apresentação de gráficos. 

Exemplo de uso em JavaScript:
```javascript
const svgElement = document.getElementById('meuSVG');
svgElement.setAttribute('preserveAspectRatio', 'xMidYMid meet');
```

## Exemplos
### Exemplo Básico de SVG com `preserveAspectRatio`
```html
<svg id="meuSVG" width="400" height="200" preserveAspectRatio="xMidYMid meet">
    <rect width="100%" height="100%" fill="blue" />
</svg>
```

### Alterando o `preserveAspectRatio` com JavaScript
```html
<script>
    const svgElement = document.getElementById('meuSVG');
    svgElement.setAttribute('preserveAspectRatio', 'xMinYMin');
</script>
```

## Explicação
Um erro comum ao usar `preserveAspectRatio` é não considerar como a proporção do conteúdo será afetada em diferentes tamanhos de tela. Por exemplo, usar `none` pode distorcer a imagem, enquanto `meet` e `slice` oferecem soluções para evitar isso.

Outro ponto a ser observado é a compatibilidade entre navegadores. Embora a maioria dos navegadores modernos suporte `preserveAspectRatio`, sempre é bom testar a renderização em diferentes plataformas.

## Resumo em Uma Linha
O atributo `preserveAspectRatio` em SVG, manipulado via JavaScript, controla a preservação da proporção de gráficos ao serem escalados em seus contêineres.