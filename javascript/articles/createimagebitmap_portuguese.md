<!--
Meta Description: # createImageBitmap: Criando Bitmaps de Imagens em JavaScript ## Sinopse O método `createImageBitmap` em JavaScript permite a criação de um bitmap a p...
Meta Keywords: bitmap, imagem, createimagebitmap, que, ser
-->

# createImageBitmap: Criando Bitmaps de Imagens em JavaScript

## Sinopse
O método `createImageBitmap` em JavaScript permite a criação de um bitmap a partir de diferentes tipos de fontes de imagem, proporcionando uma maneira eficiente de manipular e renderizar imagens em aplicações web.

## Documentação
O método `createImageBitmap` é uma função assíncrona que cria um bitmap a partir de uma variedade de fontes, como elementos HTMLImageElement, HTMLCanvasElement, ou objetos ImageData. Este método é útil para otimizar o desempenho de renderização de imagens em ambientes gráficos, como WebGL ou em animações.

### Propósito
O principal objetivo do `createImageBitmap` é permitir a pré-renderização de imagens, minimizando o tempo de carregamento e melhorando a performance geral da aplicação.

### Uso
A sintaxe básica do `createImageBitmap` é a seguinte:

```javascript
createImageBitmap(image, sx, sy, sw, sh, options)
```

- **image**: (Obligatório) A fonte da imagem, que pode ser um objeto Image, Canvas, ou ImageData.
- **sx**: (Opcional) A coordenada x inicial da área da imagem a ser extraída (default é 0).
- **sy**: (Opcional) A coordenada y inicial da área da imagem a ser extraída (default é 0).
- **sw**: (Opcional) A largura da área da imagem a ser extraída (default é a largura total da imagem).
- **sh**: (Opcional) A altura da área da imagem a ser extraída (default é a altura total da imagem).
- **options**: (Opcional) Um objeto que pode incluir a propriedade `imageOrientation` para ajustar a orientação da imagem.

### Retorno
O método retorna uma Promise que resolve em um objeto `ImageBitmap`.

## Exemplos

### Exemplo 1: Criar um bitmap a partir de uma imagem
```javascript
const img = new Image();
img.src = 'caminho/para/imagem.jpg';
img.onload = () => {
    createImageBitmap(img).then(bitmap => {
        // Use o bitmap aqui
        console.log('Bitmap criado com sucesso:', bitmap);
    }).catch(error => {
        console.error('Erro ao criar o bitmap:', error);
    });
};
```

### Exemplo 2: Criar um bitmap a partir de um canvas
```javascript
const canvas = document.createElement('canvas');
const ctx = canvas.getContext('2d');
ctx.fillStyle = 'red';
ctx.fillRect(0, 0, 100, 100);

createImageBitmap(canvas).then(bitmap => {
    // Use o bitmap aqui
    console.log('Bitmap criado a partir do canvas:', bitmap);
}).catch(error => {
    console.error('Erro ao criar o bitmap:', error);
});
```

## Explicação
Um dos principais pontos a serem observados ao usar `createImageBitmap` é que a função é assíncrona. Isso significa que você deve lidar com a Promise retornada para garantir que o bitmap foi criado antes de usá-lo. Além disso, é importante notar que o método pode não funcionar corretamente em alguns navegadores mais antigos, então sempre verifique a compatibilidade.

Outro ponto a ser considerado é o uso do parâmetro `options`, que pode ser útil para ajustar a orientação da imagem em casos específicos, como quando a imagem contém metadados de orientação.

## Resumo em Uma Linha
O método `createImageBitmap` em JavaScript permite a criação eficiente de bitmaps a partir de diversas fontes de imagem, melhorando a performance em aplicações web.