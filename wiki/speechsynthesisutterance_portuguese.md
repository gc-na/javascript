<!--
Meta Description: # SpeechSynthesisUtterance: Controle de Voz em JavaScript ## Sinopse O `SpeechSynthesisUtterance` é uma interface da Web Speech API que permite gerar ...
Meta Keywords: fala, que, utterance, speechsynthesisutterance, javascript
-->

# SpeechSynthesisUtterance: Controle de Voz em JavaScript

## Sinopse
O `SpeechSynthesisUtterance` é uma interface da Web Speech API que permite gerar fala sintética a partir de texto em aplicações JavaScript, proporcionando uma experiência interativa e acessível para usuários.

## Documentação
### Propósito
A interface `SpeechSynthesisUtterance` é usada para criar objetos que representam a fala a ser sintetizada. Com essa interface, desenvolvedores podem transformar texto em voz, personalizando aspectos como volume, taxa de fala e idioma.

### Uso
Para utilizar o `SpeechSynthesisUtterance`, você deve primeiro instanciar um objeto dessa classe e, em seguida, usar a API `SpeechSynthesis` para que o texto seja falado. 

### Sintaxe
```javascript
const utterance = new SpeechSynthesisUtterance(text);
```

### Propriedades
- **text**: O texto que será falado.
- **lang**: O idioma da fala (ex: "pt-BR" para português do Brasil).
- **volume**: Um número entre 0 e 1 que define o volume da fala.
- **rate**: Um número que define a velocidade da fala (padrão é 1).
- **pitch**: Um número que define o tom da fala (padrão é 1).

### Métodos
- **speak()**: Fala o texto especificado.
- **cancel()**: Cancela todas as falas em andamento.
- **pause()**: Pausa a fala em andamento.
- **resume()**: Retoma a fala que foi pausada.

## Exemplos
### Exemplo Básico
```javascript
const utterance = new SpeechSynthesisUtterance("Olá, mundo!");
speechSynthesis.speak(utterance);
```

### Exemplo com Propriedades
```javascript
const utterance = new SpeechSynthesisUtterance("Bem-vindo ao nosso site!");
utterance.lang = "pt-BR";
utterance.volume = 1; // volume máximo
utterance.rate = 1; // velocidade normal
utterance.pitch = 1; // tom normal
speechSynthesis.speak(utterance);
```

### Exemplo de Cancelamento
```javascript
const utterance = new SpeechSynthesisUtterance("Essa fala será cancelada.");
speechSynthesis.speak(utterance);
setTimeout(() => {
    speechSynthesis.cancel(); // Cancela a fala após 2 segundos
}, 2000);
```

## Explicação
Um dos principais desafios ao usar `SpeechSynthesisUtterance` é garantir que o texto a ser falado esteja devidamente formatado e que o navegador suporte a API. Além disso, é importante lembrar que o comportamento da síntese de fala pode variar entre navegadores, especialmente no que diz respeito a vozes disponíveis e qualidade da fala. 

Outro ponto a considerar é o gerenciamento de eventos associados à fala, como `onend`, `onerror`, e `onstart`, que podem ser úteis para criar uma experiência mais interativa e responsiva.

## Resumo em Uma Linha
O `SpeechSynthesisUtterance` permite transformar texto em fala sintética em JavaScript, facilitando a criação de aplicações interativas e acessíveis.