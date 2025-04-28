<!--
Meta Description: # SVGFEFuncRElement: Manipulação de Filtros SVG com JavaScript ## Sinopse O `SVGFEFuncRElement` é um elemento do SVG (Scalable Vector Graphics) que de...
Meta Keywords: svg, svgfefuncrelement, filter, fecomponenttransfer, valores
-->

# SVGFEFuncRElement: Manipulação de Filtros SVG com JavaScript

## Sinopse
O `SVGFEFuncRElement` é um elemento do SVG (Scalable Vector Graphics) que desempenha um papel crucial na aplicação de efeitos de filtro, especificamente na definição da função de mapeamento de cor para o canal vermelho em filtros SVG. Este elemento é acessível e manipulável via JavaScript, permitindo um controle dinâmico sobre efeitos gráficos.

## Documentação

### Propósito
O `SVGFEFuncRElement` é usado dentro de um elemento `<filter>` para especificar como os valores do canal vermelho de uma imagem de entrada devem ser transformados. É parte de um conjunto de elementos que também inclui `SVGFEFuncGElement`, `SVGFEFuncBElement`, e `SVGFEFuncAElement`, cada um responsável por um canal de cor diferente.

### Uso
O `SVGFEFuncRElement` é tipicamente utilizado em combinação com filtros de cor, como `feColorMatrix`, `feComponentTransfer`, e outros. Ele permite aos desenvolvedores ajustar a intensidade e a transformação da cor vermelha de uma imagem ou gráfico vetorial.

#### Estrutura
```html
<feComponentTransfer in="SourceGraphic">
  <feFuncR type="table" tableValues="0 1" />
</feComponentTransfer>
```

### Atributos Comuns
- **type**: Define o tipo de função de transferência. Os valores podem incluir `table`, `discrete`, `linear`, e `gamma`.
- **tableValues**: Um conjunto de valores que define a tabela de mapeamento. Utilizado quando `type` é `table`.
- **slope**: Para tipos `linear`, este atributo define a inclinação da transformação do valor.
- **intercept**: Para tipos `linear`, este atributo define o deslocamento da transformação.

## Exemplos

### Exemplo Básico
```html
<svg width="200" height="200">
  <defs>
    <filter id="filter1">
      <feComponentTransfer>
        <feFuncR type="linear" slope="1.2" intercept="0" />
      </feComponentTransfer>
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="blue" filter="url(#filter1)" />
</svg>
```
Neste exemplo, um filtro é aplicado a um retângulo azul, aumentando a intensidade do canal vermelho.

### Exemplo com Tabela de Valores
```html
<svg width="200" height="200">
  <defs>
    <filter id="filter2">
      <feComponentTransfer>
        <feFuncR type="table" tableValues="0 1 1 0" />
      </feComponentTransfer>
    </filter>
  </defs>
  <circle cx="100" cy="100" r="80" fill="green" filter="url(#filter2)" />
</svg>
```
Aqui, um círculo verde tem sua cor vermelha alterada com base em uma tabela de valores.

## Explicação
Um dos principais desafios ao usar o `SVGFEFuncRElement` é entender como os diferentes tipos de função de transferência afetam a imagem. Um erro comum é não definir corretamente os atributos `slope` e `intercept`, resultando em uma transformação inesperada. Além disso, é importante notar que o uso de valores extremos em `tableValues` pode levar a resultados não intuitivos.

Ao trabalhar com JavaScript, você pode acessar e modificar o `SVGFEFuncRElement` através da API do DOM SVG. Por exemplo, você pode alterar dinamicamente os atributos para criar efeitos interativos.

## Resumo em Uma Linha
O `SVGFEFuncRElement` é um elemento SVG que permite manipular dinamicamente a função de transferência do canal vermelho de filtros gráficos via JavaScript, oferecendo controle sobre a aparência das imagens.