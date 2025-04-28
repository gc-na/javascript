<!--
Meta Description: # onended: Entendendo o Evento de Término em JavaScript ## Sinopse O evento `onended` é um manipulador de eventos que ocorre quando a reprodução de um...
Meta Keywords: onended, reprodução, que, evento, quando
-->

# onended: Entendendo o Evento de Término em JavaScript

## Sinopse
O evento `onended` é um manipulador de eventos que ocorre quando a reprodução de um áudio ou vídeo chega ao fim. Este evento é fundamental para desenvolvedores que desejam executar ações específicas após o término da reprodução, oferecendo uma experiência interativa e dinâmica em aplicativos web.

## Documentação
O evento `onended` é frequentemente utilizado em elementos multimídia, como `<audio>` e `<video>`, em JavaScript. Ele permite que os desenvolvedores escutem e respondam ao término da reprodução de um arquivo de mídia. Quando o arquivo de mídia termina, a função atribuída a `onended` é executada automaticamente.

### Propósito
O principal propósito do evento `onended` é permitir que ações sejam executadas assim que o conteúdo multimídia termina a sua reprodução. Isso pode incluir ações como reiniciar a reprodução, carregar uma nova faixa ou atualizar a interface do usuário.

### Uso
Para usar o evento `onended`, você deve adicionar um manipulador de eventos ao seu elemento de mídia. Isso pode ser feito usando a propriedade `onended` diretamente no elemento ou utilizando o método `addEventListener`.

### Sintaxe
```javascript
elemento.onended = function() {
    // Código a ser executado quando a reprodução terminar
};
```
ou
```javascript
elemento.addEventListener('ended', function() {
    // Código a ser executado quando a reprodução terminar
});
```

## Exemplos

### Exemplo 1: Usando `onended` com um elemento `<audio>`
```html
<audio id="meuAudio" src="musica.mp3" controls></audio>
<script>
    const audio = document.getElementById('meuAudio');
    audio.onended = function() {
        alert('A reprodução terminou!');
    };
</script>
```

### Exemplo 2: Usando `addEventListener` com um elemento `<video>`
```html
<video id="meuVideo" src="video.mp4" controls></video>
<script>
    const video = document.getElementById('meuVideo');
    video.addEventListener('ended', function() {
        console.log('O vídeo terminou de ser reproduzido.');
    });
</script>
```

## Explicação
Embora o uso do evento `onended` seja bastante simples, alguns desenvolvedores podem encontrar armadilhas comuns:

- **Falta de suporte em navegadores antigos**: Certifique-se de que o navegador do usuário seja compatível com eventos de mídia.
- **Não confundir com `onpause` ou `onstop`**: O evento `onended` é acionado apenas quando a reprodução chega ao fim, ao contrário de `onpause`, que é acionado quando a reprodução é interrompida manualmente.
- **Repetição de loops**: Se você estiver usando `onended` para reiniciar a reprodução, é importante que a lógica que reinicia a reprodução não cause um loop infinito.

## Resumo em uma Frase
O evento `onended` em JavaScript permite que desenvolvedores executem ações específicas quando a reprodução de um áudio ou vídeo termina, melhorando a interatividade de aplicações web.