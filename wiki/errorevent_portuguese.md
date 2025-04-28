<!--
Meta Description: # ErrorEvent em JavaScript: Entenda e Utilize Eficientemente ## Sinopse O `ErrorEvent` é um objeto que representa um erro que ocorreu durante a execuç...
Meta Keywords: erro, event, errorevent, que, error
-->

# ErrorEvent em JavaScript: Entenda e Utilize Eficientemente

## Sinopse
O `ErrorEvent` é um objeto que representa um erro que ocorreu durante a execução de scripts em um contexto de navegador. Este evento é fundamental para o tratamento de erros em JavaScript, permitindo que desenvolvedores capturem, analisem e respondam a falhas no código.

## Documentação
O `ErrorEvent` é parte da API de Eventos do JavaScript e é disparado quando ocorre um erro durante a execução de um script. Ele fornece informações úteis sobre o erro, como a mensagem de erro, a URL do script que causou o erro e a linha onde ocorreu.

### Propósito
O principal objetivo do `ErrorEvent` é permitir que os desenvolvedores tratem erros de forma eficaz, melhorando a experiência do usuário e facilitando a depuração do código.

### Uso
Para capturar um `ErrorEvent`, você pode utilizar o método `window.addEventListener` com o tipo de evento definido como `"error"`. 

```javascript
window.addEventListener("error", function(event) {
    console.error("Mensagem de Erro: ", event.message);
    console.error("Arquivo: ", event.filename);
    console.error("Linha: ", event.lineno);
});
```

### Propriedades
O `ErrorEvent` possui as seguintes propriedades principais:
- `message`: A mensagem de erro.
- `filename`: O nome do arquivo onde ocorreu o erro.
- `lineno`: O número da linha onde o erro ocorreu.
- `colno`: O número da coluna onde o erro ocorreu (disponível em alguns navegadores).
- `error`: O objeto de erro associado (se disponível).

## Exemplos
### Exemplo 1: Capturando um erro simples
```javascript
window.addEventListener("error", function(event) {
    console.log("Erro capturado: ", event.message);
});

undefinedFunction(); // Chamada a uma função inexistente
```

### Exemplo 2: Exibindo informações detalhadas do erro
```javascript
window.addEventListener("error", function(event) {
    alert(`Erro: ${event.message}\nArquivo: ${event.filename}\nLinha: ${event.lineno}`);
});

// Forçando um erro
const result = 1 / 0; // Não gera um ErrorEvent, mas pode ser usado em testes de lógica
```

## Explicação
Uma armadilha comum ao usar `ErrorEvent` é não considerar que ele só captura erros de scripts. Erros de rede, por exemplo, não são capturados por este evento. Além disso, para erros que ocorrem em promessas rejeitadas, é recomendável utilizar o tratamento de erro adequado com `.catch()`.

Outro ponto importante é que a captura de eventos de erro no `window` pode afetar a performance do aplicativo se não for gerenciado adequadamente. Mantenha o código dentro do manipulador de eventos eficiente e faça a limpeza de recursos se necessário.

## Resumo em Uma Linha
O `ErrorEvent` em JavaScript permite capturar e gerenciar erros em scripts, fornecendo informações cruciais para melhoria e depuração do código.