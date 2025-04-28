<!--
Meta Description: # Evento ontimeupdate em JavaScript: O que é e como usar ## Sinopse O evento `ontimeupdate` em JavaScript é um recurso utilizado para monitorar e reag...
Meta Keywords: ontimeupdate, evento, video, reprodução, como
-->

# Evento ontimeupdate em JavaScript: O que é e como usar

## Sinopse
O evento `ontimeupdate` em JavaScript é um recurso utilizado para monitorar e reagir a mudanças na posição de reprodução de mídias, como vídeos e áudios, em elementos HTML.

## Documentação
O evento `ontimeupdate` é disparado sempre que a posição de reprodução de um elemento `<video>` ou `<audio>` é atualizada. Este evento é especialmente útil para criar interfaces dinâmicas que respondem a alterações no tempo de reprodução, como barras de progresso e controles personalizados.

### Propósito
O objetivo do `ontimeupdate` é permitir que os desenvolvedores possam executar funções específicas em resposta à atualização do tempo de reprodução, proporcionando uma experiência de usuário mais interativa.

### Uso
Para usar o evento `ontimeupdate`, você deve adicionar um listener ao elemento de mídia. O código a seguir ilustra como adicionar esse evento:

```javascript
const video = document.getElementById('meuVideo');

video.ontimeupdate = function() {
  console.log(`O tempo atual de reprodução é: ${video.currentTime} segundos`);
};
```

## Exemplos
### Exemplo Básico
Aqui está um exemplo básico que demonstra como usar o `ontimeupdate` para exibir o tempo atual de reprodução de um vídeo em um elemento HTML:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de ontimeupdate</title>
</head>
<body>
    <video id="meuVideo" width="640" height="360" controls>
        <source src="video.mp4" type="video/mp4">
        Seu navegador não suporta o vídeo.
    </video>
    <p>Tempo atual: <span id="tempoAtual">0</span> segundos</p>

    <script>
        const video = document.getElementById('meuVideo');
        const tempoAtual = document.getElementById('tempoAtual');

        video.ontimeupdate = function() {
            tempoAtual.textContent = Math.floor(video.currentTime);
        };
    </script>
</body>
</html>
```

## Explicação
### Armadilhas Comuns
- **Repetição Excessiva**: O evento `ontimeupdate` pode ser disparado várias vezes por segundo. Se você realizar operações pesadas dentro desse evento, isso pode causar lentidão na aplicação. É recomendável usar técnicas de debounce ou throttle.
- **Compatibilidade do Navegador**: Embora a maioria dos navegadores modernos suporte o evento `ontimeupdate`, sempre é bom verificar a compatibilidade quando se está desenvolvendo para uma base de usuários diversificada.

### Notas Adicionais
- O evento é particularmente útil para implementar recursos como barras de progresso personalizadas, que atualizam em tempo real com a reprodução do vídeo ou áudio.
- Você pode combinar o evento `ontimeupdate` com outros eventos de mídia, como `play`, `pause` e `ended`, para criar experiências de usuário mais ricas.

## Resumo em Uma Linha
O evento `ontimeupdate` em JavaScript permite monitorar e responder a mudanças na posição de reprodução de vídeos e áudios em elementos HTML, melhorando a interatividade da interface.