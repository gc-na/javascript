<!--
Meta Description: # onloadedmetadata: Entendendo o Evento em JavaScript ## Sinopse O evento `onloadedmetadata` em JavaScript é acionado quando os metadados de um recurs...
Meta Keywords: video, mídia, onloadedmetadata, evento, arquivo
-->

# onloadedmetadata: Entendendo o Evento em JavaScript

## Sinopse
O evento `onloadedmetadata` em JavaScript é acionado quando os metadados de um recurso de mídia, como um vídeo ou áudio, são carregados. Isso permite que os desenvolvedores acessem informações como duração, dimensões e outros atributos do arquivo de mídia, possibilitando um controle mais eficaz sobre a reprodução.

## Documentação
O evento `onloadedmetadata` é parte da API de mídia HTML5 e pode ser utilizado em elementos `<video>` e `<audio>`. Ele é fundamental para garantir que as informações do arquivo de mídia estejam disponíveis antes de interagir com ele.

### Propósito
O principal propósito do evento `onloadedmetadata` é notificar os desenvolvedores quando os metadados de um arquivo de mídia foram totalmente carregados. Isso é especialmente útil em aplicações que necessitam manipular a reprodução de mídia com base nas características do arquivo.

### Uso
Para utilizar o evento `onloadedmetadata`, é necessário atribuir uma função de callback ao evento do elemento de mídia. Veja a sintaxe básica:

```javascript
const video = document.querySelector('video');

video.onloadedmetadata = function() {
    console.log('Metadados carregados!');
    console.log('Duração do vídeo: ' + video.duration + ' segundos');
};
```

## Exemplos

### Exemplo 1: Exibindo a Duração do Vídeo
```html
<video id="meuVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Seu navegador não suporta o elemento de vídeo.
</video>

<script>
    const video = document.getElementById('meuVideo');
    
    video.onloadedmetadata = function() {
        console.log('Duração do vídeo: ' + video.duration + ' segundos');
    };
</script>
```

### Exemplo 2: Exibindo Dimensões do Vídeo
```html
<video id="meuVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Seu navegador não suporta o elemento de vídeo.
</video>

<script>
    const video = document.getElementById('meuVideo');
    
    video.onloadedmetadata = function() {
        console.log('Largura: ' + video.videoWidth + ' pixels');
        console.log('Altura: ' + video.videoHeight + ' pixels');
    };
</script>
```

## Explicação
Um ponto importante a ser observado é que o evento `onloadedmetadata` será acionado apenas uma vez, quando os metadados do arquivo de mídia forem carregados. Caso o arquivo de mídia seja alterado dinamicamente, o evento precisará ser redefinido para lidar com os novos metadados.

Além disso, é essencial garantir que o arquivo de mídia seja acessível; caso contrário, o evento pode não ser acionado. É recomendável incluir tratamento de erros para casos em que o arquivo não possa ser carregado, garantindo uma experiência de usuário mais robusta.

## Resumo em uma Linha
O evento `onloadedmetadata` em JavaScript permite que desenvolvedores acessem metadados de arquivos de mídia, facilitando a manipulação da reprodução e informações do arquivo.