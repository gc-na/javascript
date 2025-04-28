<!--
Meta Description: # SVGAnimatedLengthList: Manipulando Listas de Comprimento em SVG com JavaScript ## Sinopse O `SVGAnimatedLengthList` é uma interface do DOM utilizada...
Meta Keywords: que, svg, comprimentos, uma, lista
-->

# SVGAnimatedLengthList: Manipulando Listas de Comprimento em SVG com JavaScript

## Sinopse
O `SVGAnimatedLengthList` é uma interface do DOM utilizada para trabalhar com listas de comprimentos animadas em documentos SVG. Esta interface é especialmente útil para manipular atributos que aceitam listas de comprimentos, como os atributos de forma e de caminho em gráficos vetoriais escaláveis.

## Documentação

### Descrição
A interface `SVGAnimatedLengthList` é uma extensão da interface `SVGLengthList`, que permite a manipulação de listas de comprimentos que podem ser animadas. Ela é utilizada frequentemente em SVG para controlar elementos que possuem uma lista de valores de comprimento, como os atributos `stroke-dasharray` e `stroke-dashoffset`.

#### Estrutura
O `SVGAnimatedLengthList` possui duas propriedades principais:
- `baseVal`: um objeto do tipo `SVGLengthList` que representa o valor base (não animado) da lista de comprimentos.
- `animVal`: um objeto do tipo `SVGLengthList` que representa o valor animado da lista de comprimentos, que pode ser alterado ao longo do tempo por meio de animações.

### Uso
Para utilizar o `SVGAnimatedLengthList`, você deve primeiro acessar um elemento SVG que contenha um atributo que aceite uma lista de comprimentos. Em seguida, você pode manipular as propriedades `baseVal` e `animVal` para definir ou obter valores desses atributos.

## Exemplos

### Exemplo 1: Acessando uma Lista de Comprimento
```javascript
// Selecionando um elemento SVG
const svgElement = document.getElementById('meuElemento');

// Acessando o atributo stroke-dasharray
const dashArray = svgElement.getAttribute('stroke-dasharray');

// Acessando a lista de comprimentos animada
const animatedLengthList = svgElement.getAttribute('stroke-dasharray').baseVal;

// Logando o valor base
console.log(animatedLengthList);
```

### Exemplo 2: Modificando o Valor Base
```javascript
// Selecionando um elemento SVG
const svgElement = document.getElementById('meuElemento');

// Modificando o valor base do stroke-dasharray
svgElement.style.strokeDasharray = "5, 5"; // Define uma nova lista de comprimento
```

### Exemplo 3: Acessando o Valor Animado
```javascript
// Selecionando um elemento SVG
const svgElement = document.getElementById('meuElemento');

// Acessando o valor animado
const animatedLengthList = svgElement.getAttribute('stroke-dasharray').animVal;

// Logando o valor animado
console.log(animatedLengthList);
```

## Explicação
Ao trabalhar com `SVGAnimatedLengthList`, é importante ter em mente que a manipulação direta dos valores animados pode não ter efeito se uma animação estiver em execução. Além disso, a compatibilidade com todos os navegadores deve ser testada, pois algumas funcionalidades podem variar entre diferentes implementações de SVG.

Outro ponto a considerar é que a lista de comprimentos deve estar no formato correto (ex: "10, 20, 30") para evitar erros na execução do código. Ao manipular a propriedade `baseVal`, as alterações podem ser refletidas imediatamente no elemento SVG, enquanto a propriedade `animVal` pode não refletir essas mudanças até que a animação termine.

## Resumo em Uma Linha
O `SVGAnimatedLengthList` permite a manipulação de listas de comprimentos animadas em SVG, facilitando a criação de gráficos dinâmicos e interativos com JavaScript.