<!--
Meta Description: # PromiseRejectionEvent em JavaScript: Entendendo o Evento de Rejeição de Promessas ## Sinopse O `PromiseRejectionEvent` é um evento que é disparado q...
Meta Keywords: não, que, evento, promiserejectionevent, javascript
-->

# PromiseRejectionEvent em JavaScript: Entendendo o Evento de Rejeição de Promessas

## Sinopse
O `PromiseRejectionEvent` é um evento que é disparado quando uma promessa é rejeitada e não há manipulador de rejeição registrado. Este evento permite monitorar e tratar rejeições de promessas que não foram capturadas, facilitando a depuração e o manejo de erros em aplicações JavaScript.

## Documentação
O `PromiseRejectionEvent` é parte do modelo de eventos do JavaScript e é utilizado para capturar rejeições de promessas que não são tratadas adequadamente. Quando uma promessa é rejeitada sem um manipulador `.catch()`, o evento `unhandledrejection` é emitido. Esse evento fornece informações sobre a razão da rejeição e a promessa que foi rejeitada.

### Propósito
O principal objetivo do `PromiseRejectionEvent` é permitir que desenvolvedores lidem com promessas rejeitadas que não foram atendidas por manipuladores de erro, ajudando a evitar possíveis falhas e comportamentos inesperados nas aplicações.

### Uso
Para utilizar o `PromiseRejectionEvent`, você pode adicionar um listener para o evento `unhandledrejection` no objeto `window`. O tratamento deste evento pode incluir ações como registro de erros, notificações ou qualquer outro mecanismo de erro.

```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.error('Promessa rejeitada:', event.reason);
});
```

## Exemplos

### Exemplo 1: Capturando uma rejeição não tratada
```javascript
window.addEventListener('unhandledrejection', function(event) {
    console.error('Rejeição não tratada:', event.reason);
});

const promesa = new Promise((resolve, reject) => {
    reject('Erro ao processar a promessa');
});

// Aqui não há um .catch(), então o evento será disparado
```

### Exemplo 2: Tratando rejeições com .catch()
```javascript
const promesa = new Promise((resolve, reject) => {
    reject('Erro com a promessa');
});

promesa.catch((error) => {
    console.log('Erro tratado:', error);
});

// Neste caso, o `unhandledrejection` não será disparado
```

## Explicação
Um ponto crucial sobre o `PromiseRejectionEvent` é que ele só é disparado para promessas rejeitadas que não têm manipuladores de erro. Isso significa que se você usar `.catch()` ou `try...catch` com `async/await`, o evento não será emitido. 

Além disso, é importante estar ciente de que a captura de rejeições não tratadas pode ser uma ferramenta poderosa para a depuração, mas deve ser usada com cautela. As mensagens de erro devem ser claras e informativas, permitindo que os desenvolvedores identifiquem rapidamente a origem do problema.

## Resumo em uma linha
O `PromiseRejectionEvent` permite capturar e tratar rejeições de promessas não tratadas em JavaScript, facilitando o manejo de erros em aplicações.