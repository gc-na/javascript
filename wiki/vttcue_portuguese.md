<!--
Meta Description: # VTTCue: Manipulação de Legendas em JavaScript ## Sinopse O VTTCue é uma interface em JavaScript que permite a manipulação de legendas em vídeos, fac...
Meta Keywords: vttcue, que, texto, cue, uma
-->

# VTTCue: Manipulação de Legendas em JavaScript

## Sinopse
O VTTCue é uma interface em JavaScript que permite a manipulação de legendas em vídeos, facilitando a adição de textos de forma sincronizada com a reprodução de conteúdo multimídia.

## Documentação
### Propósito
A interface VTTCue é parte do WebVTT (Web Video Text Tracks), que é um formato usado para fornecer legendas e outras faixas de texto em vídeos na web. O VTTCue permite criar e gerenciar objetos de cue (pontos de texto) que definem quando e como o texto deve aparecer durante a reprodução do vídeo.

### Uso
O VTTCue é utilizado em conjunto com elementos de vídeo HTML5. Para criar uma nova instância de VTTCue, você deve especificar o tempo de início e fim da exibição do texto, além do conteúdo da legenda.

#### Sintaxe
```javascript
let cue = new VTTCue(inicio, fim, texto);
```

- **inicio**: Tempo em segundos em que a cue deve começar a aparecer.
- **fim**: Tempo em segundos em que a cue deve desaparecer.
- **texto**: O conteúdo textual que será exibido.

### Propriedades
As instâncias de VTTCue têm várias propriedades que permitem personalizar o comportamento e a apresentação do texto, entre elas:
- **startTime**: O tempo em que a cue começa a ser exibida.
- **endTime**: O tempo em que a cue para de ser exibida.
- **text**: O conteúdo textual da cue.
- **line**: A posição vertical do texto (padrão: "auto").
- **position**: A posição horizontal do texto (padrão: "auto").
- **align**: O alinhamento do texto (padrão: "center").

## Exemplos
### Exemplo Básico
```javascript
const video = document.querySelector('video');
const track = video.addTextTrack('subtitles', 'Português', 'pt');

const cue = new VTTCue(0, 5, 'Bem-vindo ao nosso vídeo!');
track.addCue(cue);
```

### Exemplo com Várias Cues
```javascript
const track = video.addTextTrack('subtitles', 'Português', 'pt');

const cue1 = new VTTCue(0, 5, 'Início do vídeo.');
const cue2 = new VTTCue(5, 10, 'Aqui está uma explicação.');

track.addCue(cue1);
track.addCue(cue2);
```

## Explicação
### Armadilhas Comuns
- **Tempos Inadequados**: Certifique-se de que os tempos de início e fim não se sobreponham com outras cues, pois isso pode causar comportamentos inesperados na exibição.
- **Formato de Texto**: O conteúdo deve ser bem formatado, evitando caracteres especiais que possam não ser renderizados corretamente.
- **Compatibilidade**: Embora o VTTCue seja suportado na maioria dos navegadores modernos, sempre verifique a compatibilidade para garantir uma experiência uniforme.

### Notas Adicionais
- O uso de VTTCue é mais eficaz quando combinado com a API de vídeo HTML5, pois permite uma experiência mais rica e interativa para o usuário.
- A API WebVTT também pode ser utilizada para criar arquivos de legendas que podem ser carregados dinamicamente, tornando o gerenciamento de conteúdo de vídeo ainda mais flexível.

## Resumo em Uma Frase
VTTCue é uma interface JavaScript que facilita a criação e gerenciamento de legendas sincronizadas em vídeos HTML5.