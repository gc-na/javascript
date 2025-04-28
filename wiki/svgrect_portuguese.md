<!--
Meta Description: # SVGRect: Manipulando Retângulos em SVG com JavaScript ## Sinopse O `SVGRect` é uma interface do DOM que representa um retângulo em um elemento SVG, ...
Meta Keywords: retângulo, svg, rect, svgrect, para
-->

# SVGRect: Manipulando Retângulos em SVG com JavaScript

## Sinopse
O `SVGRect` é uma interface do DOM que representa um retângulo em um elemento SVG, permitindo a manipulação de suas propriedades, como posição, largura e altura, utilizando JavaScript.

## Documentação
O `SVGRect` é uma parte fundamental do Scalable Vector Graphics (SVG) que permite a definição e manipulação de retângulos em gráficos vetoriais escaláveis. Esta interface é frequentemente utilizada em conjunto com outros elementos SVG, como `<rect>`, para criar formas retangulares que podem ser estilizadas e animadas.

### Propriedades Principais
- **x**: A coordenada X do canto superior esquerdo do retângulo.
- **y**: A coordenada Y do canto superior esquerdo do retângulo.
- **width**: A largura do retângulo.
- **height**: A altura do retângulo.

### Uso
Para criar e manipular um `SVGRect`, você geralmente começa criando um elemento `<rect>` em um SVG. O `SVGRect` pode ser acessado e modificado através de JavaScript, permitindo uma interação dinâmica com o gráfico.

## Exemplos

### Exemplo 1: Criando um Retângulo Básico
```html
<svg width="200" height="200">
    <rect id="myRect" x="10" y="10" width="100" height="50" fill="blue"/>
</svg>

<script>
    const rect = document.getElementById('myRect');
    rect.setAttribute('fill', 'red'); // Muda a cor do retângulo para vermelho
</script>
```

### Exemplo 2: Modificando Propriedades do Retângulo
```html
<svg width="200" height="200">
    <rect id="myRect" x="10" y="10" width="100" height="50" fill="green"/>
</svg>

<script>
    const rect = document.getElementById('myRect');
    rect.setAttribute('x', 30); // Move o retângulo para a direita
    rect.setAttribute('y', 40); // Move o retângulo para baixo
    rect.setAttribute('width', 150); // Aumenta a largura do retângulo
    rect.setAttribute('height', 80); // Aumenta a altura do retângulo
</script>
```

## Explicação
Ao trabalhar com `SVGRect`, é importante estar ciente de algumas armadilhas comuns:

- **Coordenadas Relativas**: As coordenadas `x` e `y` são relativas ao sistema de coordenadas do elemento SVG pai. Certifique-se de que você entende a posição do SVG na página para evitar surpresas.
- **Unidades de Medida**: As propriedades de largura e altura devem ser definidas em pixels. Se você utilizar outras unidades, o navegador pode não renderizar corretamente o retângulo.
- **Manipulações Dinâmicas**: Quando você altera as propriedades de um retângulo, o navegador pode não atualizar imediatamente a renderização. Em alguns casos, pode ser necessário forçar uma atualização ou re-renderização.

## Resumo em Uma Linha
O `SVGRect` permite a criação e manipulação de retângulos em SVG através do JavaScript, oferecendo flexibilidade para gráficos interativos e dinâmicos.