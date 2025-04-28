<!--
Meta Description: # OfflineAudioCompletionEvent em JavaScript: O Que É e Como Usar ## Sinopse O `OfflineAudioCompletionEvent` é um evento que ocorre quando o processame...
Meta Keywords: áudio, que, processamento, contexto, offlineaudiocompletionevent
-->

# OfflineAudioCompletionEvent em JavaScript: O Que É e Como Usar

## Sinopse
O `OfflineAudioCompletionEvent` é um evento que ocorre quando o processamento de áudio em um contexto de áudio offline é concluído. Ele permite que desenvolvedores manipulem e utilizem áudio gerado de forma não interativa, ideal para casos de pré-processamento de som em aplicações web.

## Documentação
O `OfflineAudioCompletionEvent` faz parte da Web Audio API e é acionado quando um contexto de áudio offline termina de processar seu áudio. Isso é especialmente útil quando você deseja gerar áudio de forma assíncrona e precisa de um evento que sinalize que o trabalho foi concluído.

### Propósito
O propósito principal do `OfflineAudioCompletionEvent` é notificar os desenvolvedores que o áudio gerado em um contexto offline está pronto para ser utilizado, seja para reprodução, exportação ou manipulação adicional.

### Uso
Para utilizar o `OfflineAudioCompletionEvent`, você deve primeiro criar um `OfflineAudioContext`, que é um tipo especial de contexto de áudio que permite a renderização de áudio em segundo plano. Assim que o processamento é concluído, o evento `complete` é disparado.

### Propriedades
- `renderedBuffer`: Um objeto `AudioBuffer` que contém o áudio processado.

## Exemplos

### Exemplo Básico
```javascript
// Cria um contexto de áudio offline com uma taxa de amostragem de 44100Hz e duração de 2 segundos
const offlineContext = new OfflineAudioContext(2, 44100 * 2, 44100);

// Cria um oscilador
const oscillator = offlineContext.createOscillator();
oscillator.type = 'sine';
oscillator.frequency.setValueAtTime(440, 0); // Frequência de 440Hz (nota A)
oscillator.start(0);
oscillator.stop(offlineContext.length / offlineContext.sampleRate); // Para o oscilador ao final do contexto

// Conecta o oscilador ao contexto offline e inicia o processamento
oscillator.connect(offlineContext.destination);
offlineContext.startRendering().then(renderedBuffer => {
    // O áudio foi processado e o evento é disparado
    console.log('Processamento concluído!');
    
    // Aqui você pode usar o renderedBuffer
});
```

## Explicação
Um erro comum ao trabalhar com `OfflineAudioCompletionEvent` é não estar ciente de que o processamento pode levar algum tempo, especialmente se o áudio for complexo ou se houver efeitos sendo aplicados. É importante ter uma estrutura de manipulação de promessas, como mostrado no exemplo, para garantir que você lide corretamente com o resultado após o término do processamento.

Além disso, o `renderedBuffer` só estará disponível após o evento `complete`, portanto, tentativas de acessá-lo antes desse ponto resultarão em erros.

## Resumo em Uma Linha
O `OfflineAudioCompletionEvent` é um evento que indica a conclusão do processamento de áudio em um contexto offline, permitindo o uso do áudio gerado de forma assíncrona em aplicações JavaScript.