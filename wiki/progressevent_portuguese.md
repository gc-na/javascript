<!--
Meta Description: # ProgressEvent em JavaScript: Compreendendo o Evento de Progresso ## Sinopse O `ProgressEvent` é um evento do DOM que fornece informações sobre o pro...
Meta Keywords: progresso, const, que, progressevent, eventos
-->

# ProgressEvent em JavaScript: Compreendendo o Evento de Progresso

## Sinopse
O `ProgressEvent` é um evento do DOM que fornece informações sobre o progresso de uma operação em andamento, como o carregamento de um arquivo ou o download de dados, sendo amplamente utilizado em operações assíncronas em JavaScript.

## Documentação
### O que é o ProgressEvent?
`ProgressEvent` é um objeto de evento que é disparado quando uma operação de progresso é realizada. Isso é comumente utilizado em APIs de rede, como `XMLHttpRequest` e `Fetch API`, para monitorar o progresso de uploads e downloads de arquivos.

### Propósito
O propósito do `ProgressEvent` é fornecer uma maneira de acompanhar o progresso de tarefas que podem demorar um tempo para serem concluídas. Isso permite que os desenvolvedores atualizem a interface do usuário em resposta ao progresso dessas operações.

### Uso
Os eventos de progresso podem ser capturados através de manipuladores de eventos, como `onprogress`. Para utilizá-lo, é necessário adicionar um listener a um objeto que suporta eventos de progresso, como `XMLHttpRequest`.

### Propriedades Principais
- `loaded`: Representa a quantidade de bytes que já foram carregados.
- `total`: Representa o total de bytes que devem ser carregados. Se o total não estiver disponível, pode ser `undefined`.

## Exemplos

### Exemplo Básico com XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "https://example.com/largefile");

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Carregamento: ${percentComplete.toFixed(2)}% completo.`);
    }
};

xhr.onload = function() {
    console.log("Carregamento completo!");
};

xhr.send();
```

### Exemplo com Fetch API
```javascript
async function fetchWithProgress(url) {
    const response = await fetch(url);
    const reader = response.body.getReader();
    const contentLength = +response.headers.get('Content-Length');

    let receivedLength = 0;
    let chunks = [];

    while (true) {
        const { done, value } = await reader.read();
        if (done) break;

        chunks.push(value);
        receivedLength += value.length;

        const percentComplete = (receivedLength / contentLength) * 100;
        console.log(`Carregamento: ${percentComplete.toFixed(2)}% completo.`);
    }

    const chunksAll = new Uint8Array(receivedLength);
    let position = 0;
    for (const chunk of chunks) {
        chunksAll.set(chunk, position);
        position += chunk.length;
    }

    const result = new TextDecoder("utf-8").decode(chunksAll);
    console.log("Carregamento completo!");
    return result;
}

fetchWithProgress("https://example.com/largefile");
```

## Explicação
### Armadilhas Comuns
1. **Eventos não sendo disparados**: É importante verificar se a operação realmente suporta eventos de progresso, pois nem todas as APIs fornecem esses eventos.
2. **Cálculo de Progresso**: Certifique-se de que a propriedade `lengthComputable` é verdadeira antes de realizar cálculos de porcentagem, caso contrário, pode resultar em um erro.
3. **Manipulação de Erros**: Sempre implemente um tratamento para erros, pois operações de rede podem falhar e não disparar o evento de progresso.

### Notas Adicionais
O `ProgressEvent` pode não estar disponível em todos os navegadores ou em todas as situações, portanto, sempre consulte a compatibilidade e faça testes em diferentes ambientes.

## Resumo em Uma Linha
O `ProgressEvent` em JavaScript permite monitorar o progresso de operações assíncronas, como carregamentos e downloads, proporcionando feedback em tempo real ao usuário.