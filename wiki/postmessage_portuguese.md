<!--
Meta Description: # postMessage: Comunicação entre janelas em JavaScript ## Sinopse O método `postMessage` é uma função do JavaScript que permite a comunicação segura e...
Meta Keywords: postmessage, que, uma, mensagem, javascript
-->

# postMessage: Comunicação entre janelas em JavaScript

## Sinopse
O método `postMessage` é uma função do JavaScript que permite a comunicação segura entre diferentes janelas, frames ou iframes. Ele é essencial para o desenvolvimento de aplicações web que utilizam múltiplas fontes de origem.

## Documentação
O método `postMessage` é utilizado para enviar mensagens entre janelas ou documentos que possuem origens diferentes. Essa comunicação é realizada de forma assíncrona e é uma parte fundamental da API de Web Messaging. 

### Propósito
O principal propósito do `postMessage` é permitir que scripts em diferentes janelas ou frames se comuniquem sem violar as políticas de segurança do mesmo-origem (same-origin policy), que limitam o acesso a documentos de origens diferentes.

### Uso
O método `postMessage` é chamado em um objeto `Window` e recebe dois parâmetros principais:

1. **message**: O conteúdo da mensagem a ser enviada. Pode ser de qualquer tipo que possa ser serializado, como strings, objetos, etc.
2. **targetOrigin**: A origem do destinatário da mensagem. Este parâmetro é crucial para garantir a segurança, pois determina onde a mensagem pode ser enviada. Pode ser uma string representando a URL de origem ou um asterisco (`*`) para permitir qualquer origem (não recomendado por questões de segurança).

### Sintaxe
```javascript
window.postMessage(message, targetOrigin);
```

## Exemplos

### Exemplo Básico de Envio de Mensagem
```javascript
// Janela A
const janelaB = window.open('https://exemplo.com'); // Abre uma nova janela
janelaB.postMessage('Olá, Janela B!', 'https://exemplo.com');
```

### Exemplo Básico de Recebimento de Mensagem
```javascript
// Janela B
window.addEventListener('message', (event) => {
  if (event.origin === 'https://origemesperada.com') {
    console.log('Mensagem recebida:', event.data);
  }
});
```

## Explicação
Embora o `postMessage` seja uma ferramenta poderosa, é importante estar ciente de algumas armadilhas comuns:

- **Segurança**: Sempre especifique a `targetOrigin` correta para evitar o envio de mensagens para origens não confiáveis. O uso de `*` deve ser evitado em aplicações que lidam com informações sensíveis.
- **Eventos de Mensagem**: Ao receber mensagens, sempre verifique a `origin` do evento para garantir que a mensagem está vindo de uma fonte confiável.
- **Serialização de Objetos**: Os objetos enviados através de `postMessage` são serializados. Portanto, é importante que o objeto seja um tipo que possa ser serializado, como um objeto JavaScript simples ou uma string.

## Resumo em Uma Linha
O método `postMessage` permite a comunicação segura entre janelas e frames de origens diferentes em JavaScript.