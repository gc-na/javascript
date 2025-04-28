<!--
Meta Description: # SharedWorker em JavaScript: O Que É e Como Usar ## Sinopse O `SharedWorker` é uma funcionalidade do JavaScript que permite a criação de trabalhadore...
Meta Keywords: worker, sharedworker, port, event, que
-->

# SharedWorker em JavaScript: O Que É e Como Usar

## Sinopse
O `SharedWorker` é uma funcionalidade do JavaScript que permite a criação de trabalhadores (workers) que podem ser compartilhados entre diferentes janelas, abas ou iframes de uma mesma origem, possibilitando uma comunicação eficiente e otimização de recursos.

## Documentação

### O que é o SharedWorker?
O `SharedWorker` é uma interface que se estende do Worker padrão, permitindo que um único worker seja acessado por várias conexões, como janelas ou abas do navegador. Isso é especialmente útil para aplicações que precisam compartilhar dados ou estados entre diferentes partes da interface do usuário.

### Propósito
O principal propósito do `SharedWorker` é permitir a execução de tarefas em segundo plano que podem ser compartilhadas entre várias partes de uma aplicação web, reduzindo a duplicação de recursos e melhorando a eficiência.

### Uso
Para criar um `SharedWorker`, você deve seguir o seguinte procedimento:

1. **Criação do arquivo do Worker:** Primeiro, crie um arquivo JavaScript que será o código do seu `SharedWorker`.

   ```javascript
   // shared-worker.js
   self.onconnect = function(event) {
       const port = event.ports[0];
       port.onmessage = function(event) {
           port.postMessage('Mensagem recebida: ' + event.data);
       };
   };
   ```

2. **Instância do SharedWorker:** Em seu código principal, crie uma instância do `SharedWorker`.

   ```javascript
   const worker = new SharedWorker('shared-worker.js');

   worker.port.onmessage = function(event) {
       console.log(event.data);
   };

   worker.port.start();
   worker.port.postMessage('Olá, Worker!');
   ```

## Exemplos

### Exemplo Básico de SharedWorker

**Código do SharedWorker (shared-worker.js):**

```javascript
self.onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(event) {
        port.postMessage('Olá do SharedWorker: ' + event.data);
    };
};
```

**Código do Cliente:**

```javascript
const worker = new SharedWorker('shared-worker.js');

worker.port.onmessage = function(event) {
    console.log(event.data);
};

worker.port.start();
worker.port.postMessage('Mensagem inicial');
```

### Exemplo com Múltiplas Abas

```javascript
// Em uma aba
const worker = new SharedWorker('shared-worker.js');
worker.port.start();
worker.port.postMessage('Mensagem da aba 1');

// Em outra aba
const worker2 = new SharedWorker('shared-worker.js');
worker2.port.start();
worker2.port.onmessage = function(event) {
    console.log(event.data); // Receberá mensagens da aba 1
};
```

## Explicação
### Armadilhas Comuns e Dicas
- **Conexão Limitada:** Um `SharedWorker` pode ser acessado por várias janelas, mas se uma conexão for fechada (por exemplo, ao fechar uma aba), ela não será reiniciada automaticamente. Certifique-se de gerenciar as conexões adequadamente.
- **Escopo do Worker:** O `SharedWorker` é limitado ao mesmo domínio. Tentar acessá-lo de um domínio diferente resultará em erro.
- **Mensagens Assíncronas:** As mensagens entre o worker e as conexões são assíncronas. Isso significa que você deve estar preparado para lidar com a natureza assíncrona da comunicação.

## Resumo em Uma Linha
O `SharedWorker` em JavaScript permite compartilhar um worker entre múltiplas janelas ou abas, facilitando a comunicação e a eficiência em aplicações web.