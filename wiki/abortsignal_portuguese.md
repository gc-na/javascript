<!--
Meta Description: # AbortSignal em JavaScript: Controle de Cancelamento de Requisições ## Sinopse O `AbortSignal` é uma interface do JavaScript que permite o controle d...
Meta Keywords: signal, const, abortsignal, controller, abortcontroller
-->

# AbortSignal em JavaScript: Controle de Cancelamento de Requisições

## Sinopse
O `AbortSignal` é uma interface do JavaScript que permite o controle de cancelamento de operações assíncronas, como requisições HTTP, proporcionando uma maneira eficaz de interromper tarefas em andamento.

## Documentação
O `AbortSignal` é parte da API de Aborts do JavaScript, que foi introduzida para melhorar o gerenciamento de requisições assíncronas. Ele permite que um objeto `AbortController` crie sinais que podem ser usados para cancelar operações, como chamadas de rede.

### Propósito
O principal objetivo do `AbortSignal` é fornecer um mecanismo que permita cancelar operações que não são mais necessárias, economizando recursos e melhorando a experiência do usuário.

### Uso
Para utilizar o `AbortSignal`, você deve criar um `AbortController`. O `AbortController` possui uma propriedade chamada `signal`, que é um objeto `AbortSignal`.

#### Exemplo básico de uso:
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://api.exemplo.com/dados', { signal })
  .then(response => {
    if (!response.ok) {
      throw new Error('Rede falhou');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('Requisição cancelada');
    } else {
      console.error(err);
    }
  });

// Cancelar a requisição
controller.abort();
```

## Exemplos
### Exemplo 1: Cancelamento de uma Requisição
```javascript
const controller = new AbortController();
const signal = controller.signal;

const fetchData = async () => {
  try {
    const response = await fetch('https://api.exemplo.com/dados', { signal });
    const data = await response.json();
    console.log(data);
  } catch (err) {
    if (err.name === 'AbortError') {
      console.log('Requisição foi cancelada.');
    } else {
      console.error('Erro:', err);
    }
  }
};

fetchData();

// Cancelar após 1 segundo
setTimeout(() => {
  controller.abort();
}, 1000);
```

### Exemplo 2: Uso com Promessas
```javascript
const controller = new AbortController();
const signal = controller.signal;

const promise = new Promise((resolve, reject) => {
  signal.addEventListener('abort', () => {
    reject(new Error('Operação cancelada'));
  });

  // Simulando uma operação demorada
  setTimeout(() => resolve('Operação concluída'), 3000);
});

promise
  .then(result => console.log(result))
  .catch(err => console.error(err.message));

// Cancelar a operação
controller.abort();
```

## Explicação
### Armadilhas Comuns
1. **Requisições não canceladas**: Se você não passar o `signal` para a função de requisição, não conseguirá cancelar a operação.
2. **Múltiplos abortos**: Tentar abortar um `AbortController` várias vezes não causará erros, mas o comportamento pode não ser o esperado. O sinal só será "ativado" uma vez.
3. **Eventos de cancelamento**: O `AbortSignal` permite adicionar ouvintes de eventos. Certifique-se de remover ouvintes se não forem mais necessários para evitar vazamentos de memória.

### Notas Adicionais
- O `AbortSignal` é suportado na maioria dos navegadores modernos, mas verifique a compatibilidade antes de usá-lo em ambientes de produção.

## Resumo em Uma Linha
`AbortSignal` em JavaScript permite o cancelamento eficiente de operações assíncronas, como requisições de rede, por meio do uso do `AbortController`.