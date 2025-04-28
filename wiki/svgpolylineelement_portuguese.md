<!--
Meta Description: # SVGPolylineElement em JavaScript: Manipulando Polígonos em SVG ## Sinopse O `SVGPolylineElement` é uma interface do DOM que representa um elemento `...
Meta Keywords: svg, stroke, que, polilinha, width
-->

# SVGPolylineElement em JavaScript: Manipulando Polígonos em SVG

## Sinopse
O `SVGPolylineElement` é uma interface do DOM que representa um elemento `<polyline>` em um documento SVG, permitindo a criação de formas poligonais complexas que podem ser manipuladas através de JavaScript.

## Documentação
O `SVGPolylineElement` é parte da especificação SVG (Scalable Vector Graphics) e é utilizado para definir uma forma composta por uma série de linhas conectadas entre si. Cada linha é formada por um conjunto de pontos especificados nas coordenadas do elemento. Os principais atributos incluem:

- **points**: Um atributo que define os pontos de controle da polilinha. Este atributo contém uma lista de pares de coordenadas (x,y) que definem os vértices da forma.
- **fill**: Define a cor de preenchimento da polilinha.
- **stroke**: Define a cor da borda da polilinha.
- **stroke-width**: Define a largura da borda da polilinha.

### Uso
Para usar o `SVGPolylineElement`, você pode criar um elemento `<polyline>` diretamente no HTML ou gerar um dinamicamente usando JavaScript. Aqui está um exemplo básico de como criar e manipular um polígono SVG:

```html
<svg width="200" height="200">
    <polyline id="minhaPolilinha" points="10,10 20,20 30,10" fill="none" stroke="black" stroke-width="2" />
</svg>

<script>
    const polilinha = document.getElementById('minhaPolilinha');
    polilinha.setAttribute('points', '10,10 20,40 30,10 40,20');
</script>
```

## Exemplos
### Exemplo 1: Criando uma Polilinha Simples
```html
<svg width="100" height="100">
    <polyline points="10,10 50,50 90,10" fill="none" stroke="blue" stroke-width="3" />
</svg>
```

### Exemplo 2: Alterando a Polilinha com JavaScript
```html
<svg width="200" height="200">
    <polyline id="exemploPolilinha" points="20,20 40,60 60,20" fill="none" stroke="red" stroke-width="4" />
</svg>

<script>
    const polilinhaExemplo = document.getElementById('exemploPolilinha');
    polilinhaExemplo.setAttribute('points', '20,20 80,80 140,20');
    polilinhaExemplo.setAttribute('stroke', 'green');
</script>
```

## Explicação
Um erro comum ao trabalhar com `SVGPolylineElement` é não formatar corretamente o atributo `points`. Certifique-se de que as coordenadas sejam separadas por espaços e que cada coordenada seja composta por dois números, representando x e y. Além disso, o uso de valores que excedem as dimensões do SVG pode resultar em uma visualização inadequada.

Outro ponto importante é que a polilinha deve ser criada dentro de um elemento `<svg>` para que seja renderizada corretamente. Não esquecer de definir os atributos de estilo (como `stroke`, `fill` e `stroke-width`) para garantir a aparência desejada.

## Resumo em Uma Linha
O `SVGPolylineElement` permite a criação e manipulação de polilinhas em SVG, facilitando a construção de formas gráficas dinâmicas com JavaScript.