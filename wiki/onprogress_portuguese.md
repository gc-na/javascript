<!--
Meta Description: # onprogress: Acompanhando Progresso de Processos Assíncronos em JavaScript ## Sinopse O evento `onprogress` em JavaScript é utilizado para monitorar ...
Meta Keywords: onprogress, que, para, const, xhr
-->

# onprogress: Acompanhando Progresso de Processos Assíncronos em JavaScript

## Sinopse
O evento `onprogress` em JavaScript é utilizado para monitorar o progresso de operações assíncronas, como downloads de arquivos e requisições AJAX. Ele permite que os desenvolvedores implementem feedback visual durante a execução de tarefas que podem levar um tempo considerável para serem concluídas.

## Documentação
O `onprogress` é um evento associado a objetos como `XMLHttpRequest` e `Fetch API`, que permite rastrear o estado de uma operação em andamento. Ele é acionado periodicamente durante a transferência de dados, fornecendo informações sobre a quantidade de dados que já foram recebidos ou enviados. 

### Propósito
O evento `onprogress` é essencial para melhorar a experiência do usuário, permitindo que a interface reaja ao andamento de operações, como exibir barras de progresso ou mensagens de status.

### Uso
Para utilizar o `onprogress`, você deve definir um manipulador de eventos que será chamado sempre que o progresso de uma operação mudar. Abaixo estão os passos básicos para implementá-lo:

1. Crie uma instância de `XMLHttpRequest`.
2. Defina o manipulador de eventos `onprogress`.
3. Inicie a requisição.

### Detalhes
O `onprogress` fornece três propriedades principais no objeto do evento:
- `loaded`: O número de bytes já transferidos.
- `total`: O número total de bytes a serem transferidos.
- `lengthComputable`: Um booleano que indica se o total é conhecido.

## Exemplos

### Exemplo Básico com XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://example.com/arquivo.zip', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`Carregado: ${percentComplete.toFixed(2)}%`);
    } else {
        console.log('Carregando...');
    }
};

xhr.onload = function() {
    if (xhr.status === 200) {
        console.log('Download concluído!');
    }
};

xhr.send();
```

### Exemplo com Fetch API
```javascript
const url = 'https://example.com/arquivo.zip';

fetch(url)
    .then(response => {
        const reader = response.body.getReader();
        const contentLength = +response.headers.get('Content-Length');

        let receivedLength = 0; // quantidade recebida
        let chunks = []; // partes recebidas

        return new ReadableStream({
            start(controller) {
                function push() {
                    reader.read().then(({ done, value }) => {
                        if (done) {
                            controller.close();
                            return;
                        }
                        chunks.push(value);
                        receivedLength += value.length;
                        const percentComplete = (receivedLength / contentLength) * 100;
                        console.log(`Carregado: ${percentComplete.toFixed(2)}%`);
                        controller.enqueue(value);
                        push();
                    });
                }
                push();
            }
        });
    })
    .then(stream => new Response(stream))
    .then(response => response.blob())
    .then(blob => {
        console.log('Download concluído!', blob);
    });
```

## Explicação
Um erro comum ao usar `onprogress` é não verificar se a propriedade `lengthComputable` é verdadeira. Se essa propriedade for falsa, o total de bytes não é conhecido, e você não deve tentar calcular o percentual. Além disso, é importante lembrar que o evento `onprogress` pode ser chamado várias vezes durante a execução, por isso, é fundamental garantir que as atualizações de interface sejam feitas de forma eficiente para evitar sobrecarga no DOM.

## Resumo em Uma Linha
O `onprogress` em JavaScript permite monitorar o progresso de operações assíncronas, oferecendo feedback visual ao usuário durante transferências de dados.