<!--
Meta Description: # onrejectionhandled: Tratamento de Rejeições em Promessas no JavaScript ## Sinopse O evento `onrejectionhandled` no JavaScript é utilizado para captu...
Meta Keywords: onrejectionhandled, que, promessas, evento, uma
-->

# onrejectionhandled: Tratamento de Rejeições em Promessas no JavaScript

## Sinopse
O evento `onrejectionhandled` no JavaScript é utilizado para capturar e tratar rejeições de Promessas que foram manipuladas após a ocorrência de um erro, ajudando a monitorar e gerenciar promessas de forma eficaz.

## Documentação
O evento `onrejectionhandled` é parte da API de Promessas do JavaScript. Ele é disparado quando uma promessa que foi rejeitada é tratada através do método `.catch()` ou da declaração `try/catch` em uma função assíncrona. Esse evento permite que os desenvolvedores realizem ações específicas quando uma rejeição é manipulada, como o registro de erros ou a execução de lógica adicional.

### Propósito
O principal objetivo do `onrejectionhandled` é fornecer um mecanismo para detectar e responder a rejeições de promessas que foram resolvidas posteriormente. Isso é crucial em aplicações que dependem de promessas para o fluxo de dados e tratamento de erros.

### Uso
Para usar o `onrejectionhandled`, você precisa atribuir uma função de callback a ele. Essa função será chamada sempre que uma rejeição de promessa for tratada. O código a seguir ilustra como configurar esse evento:

```javascript
window.onrejectionhandled = function(event) {
    console.log('Rejeição tratada:', event.promise);
};
```

## Exemplos

### Exemplo Básico
Aqui está um exemplo simples demonstrando o uso do `onrejectionhandled`:

```javascript
// Definindo uma promessa que será rejeitada
let minhaPromessa = new Promise((resolve, reject) => {
    reject('Erro ocorreu!');
});

// Capturando a rejeição posteriormente
minhaPromessa.catch((error) => {
    console.log('Erro capturado:', error);
});

// Definindo o evento onrejectionhandled
window.onrejectionhandled = function(event) {
    console.log('Rejeição tratada:', event.promise);
};
```

### Exemplo com Async/Await
Em um contexto assíncrono, o `onrejectionhandled` pode ser usado da seguinte forma:

```javascript
async function executar() {
    throw new Error('Erro na execução');
}

executar().catch((error) => {
    console.log('Erro capturado:', error.message);
});

// Definindo o evento onrejectionhandled
window.onrejectionhandled = function(event) {
    console.log('Rejeição tratada:', event.promise);
};
```

## Explicação
Um ponto importante a considerar ao usar `onrejectionhandled` é que ele não é chamado para rejeições que não foram manipuladas. Portanto, garantir que todas as promessas sejam tratadas adequadamente é fundamental para evitar comportamentos inesperados.

### Armadilhas Comuns
- **Não Manipular Rejeições**: Se você não capturar a rejeição de uma promessa com `.catch()` ou `try/catch`, o evento `onrejectionhandled` não será disparado.
- **Uso em Ambientes Diferentes**: A compatibilidade do `onrejectionhandled` pode variar em diferentes ambientes de execução (navegadores, Node.js), portanto, sempre verifique a compatibilidade.

## Resumo em Uma Linha
O evento `onrejectionhandled` no JavaScript permite detectar e gerenciar rejeições de promessas que foram tratadas, melhorando a robustez da aplicação.