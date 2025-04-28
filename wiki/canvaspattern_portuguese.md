<!--
Meta Description: # CanvasPattern em JavaScript: Criando Padrões em Elementos Canvas ## Sinopse O `CanvasPattern` é uma interface do HTML5 Canvas API que permite criar ...
Meta Keywords: canvas, padrão, context, const, img
-->

# CanvasPattern em JavaScript: Criando Padrões em Elementos Canvas

## Sinopse
O `CanvasPattern` é uma interface do HTML5 Canvas API que permite criar padrões a partir de imagens ou gradientes, que podem ser utilizados para preencher formas desenhadas no canvas. Essa funcionalidade é essencial para desenvolvedores que desejam adicionar texturas e complexidade visual aos seus gráficos.

## Documentação
### Propósito
O `CanvasPattern` é utilizado para definir um padrão que pode ser aplicado como preenchimento em formas desenhadas em um elemento `<canvas>`. Isso é especialmente útil para criar visuais mais dinâmicos e interessantes em gráficos, jogos e interfaces de usuário.

### Uso
Para criar um `CanvasPattern`, você primeiro precisa de um contexto de renderização do canvas (2D ou WebGL) e, em seguida, utilizar o método `createPattern()` para gerar o padrão desejado.

#### Sintaxe
```javascript
const pattern = context.createPattern(image, repetition);
```

- **context**: O contexto de renderização do canvas, obtido através de `getContext('2d')`.
- **image**: Pode ser uma imagem, um canvas ou uma `<video>` que será usada como padrão.
- **repetition**: Um valor que define como o padrão será repetido. Os valores podem ser:
  - `'repeat'`: O padrão será repetido tanto horizontalmente quanto verticalmente.
  - `'repeat-x'`: O padrão será repetido apenas na direção horizontal.
  - `'repeat-y'`: O padrão será repetido apenas na direção vertical.
  - `'no-repeat'`: O padrão será exibido apenas uma vez.

### Detalhes
Após criar um `CanvasPattern`, você pode usá-lo como estilo de preenchimento ao desenhar formas, utilizando a propriedade `fillStyle` do contexto do canvas.

## Exemplos

### Exemplo 1: Padrão Simples
```javascript
const canvas = document.getElementById('meuCanvas');
const context = canvas.getContext('2d');
const img = new Image();
img.src = 'imagem.jpg';

img.onload = function() {
    const pattern = context.createPattern(img, 'repeat');
    context.fillStyle = pattern;
    context.fillRect(0, 0, canvas.width, canvas.height);
};
```

### Exemplo 2: Padrão em uma Forma
```javascript
const canvas = document.getElementById('meuCanvas');
const context = canvas.getContext('2d');
const img = new Image();
img.src = 'textura.png';

img.onload = function() {
    const pattern = context.createPattern(img, 'no-repeat');
    context.fillStyle = pattern;
    context.fillRect(50, 50, 200, 200); // Desenha um quadrado com a textura
};
```

## Explicação
Um erro comum ao usar `CanvasPattern` é não esperar a imagem ser carregada antes de tentar criar o padrão. O método `onload` deve ser utilizado para garantir que a imagem esteja totalmente carregada antes de ser usada. Além disso, é importante considerar o desempenho ao usar imagens muito grandes como padrões, pois isso pode impactar a renderização do canvas.

## Resumo em Uma Linha
O `CanvasPattern` permite criar e aplicar padrões a formas em um elemento canvas, melhorando a estética visual de gráficos e interfaces em JavaScript.