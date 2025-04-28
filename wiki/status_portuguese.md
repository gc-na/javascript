<!--
Meta Description: # Status em JavaScript: Entendendo o Comando e Suas Aplicações ## Sinopse O status em JavaScript refere-se a uma propriedade que pode ser utilizada em...
Meta Keywords: status, resposta, com, propriedade, ser
-->

# Status em JavaScript: Entendendo o Comando e Suas Aplicações

## Sinopse
O status em JavaScript refere-se a uma propriedade que pode ser utilizada em diferentes contextos, como em promessas, requisições HTTP e manipulação de eventos. Esta documentação visa esclarecer como utilizar a propriedade de status de forma eficaz em suas aplicações.

## Documentação

### Propósito
A propriedade `status` é amplamente utilizada para verificar o estado de uma operação, especialmente em requisições HTTP, onde indica o resultado da resposta do servidor. Em Promessas, o status pode indicar se a operação está pendente, foi cumprida ou rejeitada.

### Uso
A propriedade `status` é comumente acessada em objetos de resposta de requisições feitas com `XMLHttpRequest` ou `fetch`. O valor do status é um código numérico que representa o resultado da requisição, como 200 (OK), 404 (Não Encontrado) ou 500 (Erro Interno do Servidor).

### Detalhes
- **XMLHttpRequest**: A propriedade `status` pode ser acessada após o método `send()` ser chamado. O status é atualizado quando a resposta é recebida.
- **Fetch API**: Com a Fetch API, a propriedade `status` é parte do objeto `Response`, que é retornado após a requisição ser concluída.

## Exemplos

### Exemplo com XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.exemplo.com/dados', true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4) { // A requisição foi concluída
        console.log('Status:', xhr.status); // Exibe o status da resposta
    }
};
xhr.send();
```

### Exemplo com Fetch API
```javascript
fetch('https://api.exemplo.com/dados')
    .then(response => {
        console.log('Status:', response.status); // Exibe o status da resposta
        if (response.ok) {
            return response.json(); // Processa a resposta se o status for 200-299
        }
        throw new Error('Erro na requisição: ' + response.status);
    })
    .then(data => console.log(data))
    .catch(error => console.error(error));
```

## Explicação
Um erro comum ao trabalhar com o status é esquecer que ele só pode ser acessado após a conclusão da requisição. No caso do `XMLHttpRequest`, é importante verificar se o `readyState` é igual a 4. Com a Fetch API, o status deve ser verificado após a promessa ser resolvida. Outro ponto a se considerar é que o status 200 não garante que a operação foi bem-sucedida em termos de lógica de aplicação; sempre verifique o conteúdo da resposta.

## Resumo em Uma Linha
A propriedade `status` em JavaScript é usada para verificar o resultado de requisições HTTP, indicando o estado da resposta do servidor.