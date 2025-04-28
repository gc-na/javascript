<!--
Meta Description: # SVGImageElement: Manipulando Imagens SVG com JavaScript ## Sinopse O `SVGImageElement` é uma interface do DOM que permite a manipulação de elementos...
Meta Keywords: svg, imagem, para, svgimageelement, que
-->

# SVGImageElement: Manipulando Imagens SVG com JavaScript

## Sinopse
O `SVGImageElement` é uma interface do DOM que permite a manipulação de elementos de imagem dentro de SVGs (Scalable Vector Graphics) usando JavaScript. Esta interface é fundamental para trabalhar com gráficos vetoriais escaláveis em aplicações web.

## Documentação
O `SVGImageElement` representa um elemento `<image>` em SVG. Ele é utilizado para incluir imagens rasterizadas ou vetoriais dentro de um gráfico SVG. A interface oferece métodos e propriedades que permitem aos desenvolvedores acessar e modificar atributos do elemento SVG.

### Propósito
O `SVGImageElement` é utilizado para incorporar imagens dentro de gráficos SVG, proporcionando uma maneira de criar visuais dinâmicos e interativos. Além de permitir a inclusão de imagens, a interface também suporta transformações e animações.

### Uso
Para utilizar o `SVGImageElement`, você precisa de um elemento SVG em seu documento HTML. Você pode criar e manipular esse elemento usando JavaScript.

### Propriedades Principais
- `href`: A URL da imagem que será exibida.
- `width`: A largura da imagem.
- `height`: A altura da imagem.

### Métodos
- `getBBox()`: Retorna as dimensões do elemento SVG.

## Exemplos

### Exemplo Básico de Criação de um Elemento SVG com Imagem
```html
<svg width="200" height="200">
    <image id="minhaImagem" href="caminho/para/imagem.png" width="100" height="100" />
</svg>

<script>
    const imagem = document.getElementById("minhaImagem");
    imagem.setAttribute("href", "caminho/para/nova-imagem.png");
</script>
```

### Exemplo de Acessar e Modificar Propriedades
```html
<svg width="300" height="300">
    <image id="imagemSVG" href="caminho/para/imagem.svg" width="150" height="150" />
</svg>

<script>
    const imagemSVG = document.getElementById("imagemSVG");
    imagemSVG.width.baseVal.value = 200; // Modifica a largura para 200
    imagemSVG.height.baseVal.value = 200; // Modifica a altura para 200
</script>
```

## Explicação
Ao trabalhar com `SVGImageElement`, é importante lembrar que nem todos os formatos de imagem são suportados em todos os navegadores. Formatos comuns como PNG e JPEG são amplamente suportados, enquanto SVGs podem ter variações em compatibilidade dependendo do conteúdo.

Além disso, ao manipular atributos como `href`, é fundamental garantir que as URLs estejam corretas e acessíveis. Caso contrário, a imagem não será exibida.

Outro ponto a considerar é que a alteração de dimensões de imagens SVG não funciona da mesma maneira que em imagens rasterizadas. O uso de `baseVal` é necessário para acessar e modificar as dimensões corretamente.

## Resumo em Uma Linha
O `SVGImageElement` permite a manipulação de elementos de imagem em SVGs através de JavaScript, facilitando a criação de gráficos interativos e dinâmicos.