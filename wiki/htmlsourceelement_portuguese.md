<!--
Meta Description: # HTMLSourceElement: Entendendo o Elemento de Fonte em HTML no JavaScript ## Sinopse O `HTMLSourceElement` é uma interface do DOM que representa um el...
Meta Keywords: video, source, que, audio, mídia
-->

# HTMLSourceElement: Entendendo o Elemento de Fonte em HTML no JavaScript

## Sinopse
O `HTMLSourceElement` é uma interface do DOM que representa um elemento `<source>` em um documento HTML. Este elemento é utilizado principalmente para fornecer múltiplas fontes de mídia, como vídeos e áudios, permitindo que os navegadores escolham o formato mais apropriado para reprodução.

## Documentação
O `HTMLSourceElement` é parte do HTML5 e é frequentemente utilizado em conjunto com elementos de mídia, como `<video>` e `<audio>`. O propósito principal do `<source>` é especificar fontes alternativas que o navegador pode tentar carregar, dependendo do suporte do formato.

### Propriedades Principais
- `src`: Uma string que especifica a URL da fonte de mídia.
- `type`: Uma string que indica o tipo de mídia (por exemplo, `"video/mp4"`).
- `media`: Uma string que define uma condição de mídia que deve ser satisfeita para que a fonte seja aplicada.

### Uso
O `HTMLSourceElement` é definido dentro de um elemento de mídia. Por exemplo:

```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.ogg" type="video/ogg">
    Seu navegador não suporta o elemento de vídeo.
</video>
```

Neste exemplo, o navegador tentará carregar `video.mp4` primeiro; se não for suportado, tentará `video.ogg`. A inclusão da mensagem "Seu navegador não suporta o elemento de vídeo." garante que o usuário tenha uma resposta adequada se ambos os formatos falharem.

## Exemplos

### Exemplo 1: Uso Básico de `<source>` com `<video>`
```html
<video controls>
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.webm" type="video/webm">
    Seu navegador não suporta a reprodução de vídeo.
</video>
```

### Exemplo 2: Uso de `<source>` com `<audio>`
```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Seu navegador não suporta o elemento de áudio.
</audio>
```

## Explicação
Embora o uso do `HTMLSourceElement` seja bastante direto, alguns desenvolvedores podem enfrentar armadilhas comuns. Um dos problemas frequentes é não fornecer um tipo de mídia correto, resultando em falhas de carregamento. Além disso, é importante notar que o elemento `<source>` não deve ser usado fora de elementos de mídia, como `<video>` ou `<audio>`, pois isso geraria um comportamento inesperado.

Outro ponto a ser destacado é que a ordem dos `<source>` pode afetar a escolha do navegador. O navegador tentará a primeira fonte e, se não puder reproduzi-la, passará para a próxima.

## Resumo em Uma Linha
O `HTMLSourceElement` permite especificar múltiplas fontes de mídia em elementos `<video>` e `<audio>`, otimizando a compatibilidade entre navegadores.