<!--
Meta Description: # SVGAnimatedNumberList: Entendendo e Usando no JavaScript ## Sinopse O `SVGAnimatedNumberList` é uma interface do DOM utilizada em SVG (Scalable Vect...
Meta Keywords: svg, que, svganimatednumberlist, animados, uma
-->

# SVGAnimatedNumberList: Entendendo e Usando no JavaScript

## Sinopse
O `SVGAnimatedNumberList` é uma interface do DOM utilizada em SVG (Scalable Vector Graphics) que permite a manipulação de listas de números animadas. É especialmente útil para criar animações fluidas e dinâmicas em gráficos vetoriais escaláveis através do JavaScript.

## Documentação
A interface `SVGAnimatedNumberList` é parte da especificação SVG e é utilizada para representar uma lista de valores numéricos que podem ser animados. Esta interface possui duas propriedades principais:

- **baseVal**: Um objeto do tipo `SVGNumberList` que contém o valor base da lista de números.
- **animVal**: Um objeto do tipo `SVGNumberList` que representa o valor atual da lista após qualquer animação.

### Propósito
O `SVGAnimatedNumberList` é usado para manipular animações em elementos SVG, como formas geométricas, caminhos, e outros elementos que aceitam listas de números, como `stroke-dasharray` ou `points`.

### Uso
Para utilizar o `SVGAnimatedNumberList`, você deve acessar os atributos animados de um elemento SVG. Por exemplo, ao usar um elemento `<path>`, você pode acessar suas propriedades animadas diretamente através de JavaScript.

## Exemplos

### Exemplo 1: Acessando valores de uma animação
```html
<svg width="100" height="100">
    <circle id="myCircle" cx="50" cy="50" r="40" fill="red" />
    <animate attributeName="r" from="10" to="40" dur="2s" repeatCount="indefinite" />
</svg>
<script>
    const circle = document.getElementById('myCircle');
    const animatedRadius = circle.r.baseVal; // Acessa a lista de números animados
    console.log(animatedRadius); // Saída: 40
</script>
```

### Exemplo 2: Modificando valores animados
```html
<svg width="200" height="200">
    <rect id="myRect" width="100" height="100" fill="blue">
        <animate attributeName="x" from="0" to="100" dur="2s" repeatCount="indefinite" />
    </rect>
</svg>
<script>
    const rect = document.getElementById('myRect');
    const animatedX = rect.x.baseVal; // Acessa o valor do atributo x
    animatedX.value = 50; // Modifica o valor
    console.log(animatedX.value); // Saída: 50
</script>
```

## Explicação
Um ponto importante a considerar ao trabalhar com `SVGAnimatedNumberList` é que a alteração direta dos valores animados pode não ter efeito imediato se a animação estiver em andamento. Além disso, é essencial garantir que as animações estejam corretamente definidas no SVG para que os valores base e animados sejam acessíveis.

Outra armadilha comum é não verificar se o elemento SVG realmente suporta animações em suas propriedades, o que pode levar a erros ao tentar acessar `baseVal` ou `animVal` de atributos não animados.

## Resumo em Uma Linha
`SVGAnimatedNumberList` é uma interface do DOM que permite a manipulação de listas de números animadas em SVG, facilitando a criação de animações dinâmicas com JavaScript.