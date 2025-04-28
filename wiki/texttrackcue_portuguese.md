<!--
Meta Description: # TextTrackCue: Manipulando Legendas e Pistas de Texto em JavaScript ## Sinopse O `TextTrackCue` é uma interface do JavaScript que representa uma pist...
Meta Keywords: cue, que, uma, texttrackcue, texto
-->

# TextTrackCue: Manipulando Legendas e Pistas de Texto em JavaScript

## Sinopse
O `TextTrackCue` é uma interface do JavaScript que representa uma pista de texto, como legendas ou legendas ocultas, em vídeos HTML5. Ele permite que desenvolvedores manipulem e personalizem a exibição de texto durante a reprodução de mídia.

## Documentação
### O que é o TextTrackCue?
O `TextTrackCue` faz parte das APIs de mídia do HTML5 e é utilizado para representar uma cue (pista) de texto em vídeos, como legendas ou descrição de áudio. Essa interface permite a adição, remoção e manipulação de pistas de texto, proporcionando uma melhor acessibilidade e experiência ao usuário.

### Como usar o TextTrackCue
Para utilizar o `TextTrackCue`, você deve primeiro criar uma nova instância dessa interface, especificando informações como o início e o fim da cue, o texto que será exibido, e opções de estilo se necessário.

### Propriedades principais
- **startTime**: O tempo em segundos em que a cue deve começar a ser exibida.
- **endTime**: O tempo em segundos em que a cue deve parar de ser exibida.
- **text**: O texto que será exibido na cue.
- **vertical**: Define a posição vertical da cue (opcional).
- **line**: Especifica a linha da cue em relação ao vídeo (opcional).
- **position**: Define a posição horizontal da cue (opcional).

### Métodos
- **getCueAsHTML()**: Retorna a cue formatada como HTML, permitindo personalizações visuais.

## Exemplos
### Exemplo 1: Criando e Adicionando uma Cue
```javascript
// Selecionando o elemento de vídeo
const video = document.querySelector('video');

// Criando um novo objeto TextTrack
const textTrack = video.addTextTrack('subtitles', 'Português', 'pt');

// Criando uma nova cue
const cue = new TextTrackCue(0, 5, 'Bem-vindo ao nosso vídeo!');

// Adicionando a cue ao TextTrack
textTrack.addCue(cue);
```

### Exemplo 2: Usando getCueAsHTML
```javascript
// Selecionando o elemento de vídeo
const video = document.querySelector('video');

// Criando um novo objeto TextTrack
const textTrack = video.addTextTrack('subtitles', 'Inglês', 'en');

// Criando uma nova cue
const cue = new TextTrackCue(5, 10, 'Thank you for watching!');
textTrack.addCue(cue);

// Obtendo a cue como HTML
const cueHTML = cue.getCueAsHTML();
console.log(cueHTML);
```

## Explicação
Um dos principais desafios ao trabalhar com `TextTrackCue` é garantir que as cues sejam sincronizadas corretamente com o vídeo. Se o tempo de início ou fim estiver incorreto, a cue pode não aparecer no momento desejado. Além disso, é importante lembrar que as cues devem ser adicionadas ao `TextTrack` antes que o vídeo comece a ser reproduzido para garantir que sejam exibidas.

Outros pontos a considerar incluem a formatação do texto, que pode ser feita através do método `getCueAsHTML`, mas é essencial manter a acessibilidade em mente ao personalizar a aparência das cues.

## Resumo em uma linha
O `TextTrackCue` é uma interface do JavaScript que permite a manipulação de pistas de texto, como legendas, em vídeos HTML5, proporcionando uma experiência de visualização melhorada.