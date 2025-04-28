<!--
Meta Description: # onunhandledrejection: Tratamento de Promessas Não Tratadas em JavaScript ## Sinopse O evento `onunhandledrejection` é uma funcionalidade do JavaScri...
Meta Keywords: onunhandledrejection, não, que, evento, promessas
-->

# onunhandledrejection: Tratamento de Promessas Não Tratadas em JavaScript

## Sinopse
O evento `onunhandledrejection` é uma funcionalidade do JavaScript que permite capturar promessas rejeitadas que não foram tratadas, oferecendo uma maneira eficaz de lidar com erros assíncronos em aplicações web.

## Documentação
O `onunhandledrejection` é um evento que é disparado quando uma promessa é rejeitada e não há um manipulador de rejeição associado. Ao utilizar esse evento, os desenvolvedores podem interceptar erros que poderiam passar despercebidos, permitindo um tratamento mais robusto e eficiente de falhas em operações assíncronas.

### Propósito
O principal objetivo do `onunhandledrejection` é fornecer um mecanismo para capturar e gerenciar erros de promessas não tratadas. Isso é especialmente útil em aplicações que utilizam muito operações assíncronas, como chamadas a APIs ou processamento de dados.

### Uso
Para utilizar o evento `onunhandledrejection`, basta adicionar um listener ao objeto `window`. O manipulador receberá um evento que contém informações sobre a rejeição da promessa.

```javascript
window.onunhandledrejection = function(event) {
    console.error('Promessa não tratada:', event.reason);
};
```

## Exemplos
### Exemplo Básico
Aqui está um exemplo simples de como utilizar `onunhandledrejection`:

```javascript
// Definindo um manipulador para promessas não tratadas
window.onunhandledrejection = function(event) {
    console.error('Erro capturado:', event.reason);
};

// Uma promessa que será rejeitada
const minhaPromessa = new Promise((resolve, reject) => {
    reject(new Error('Algo deu errado!'));
});

// Não capturamos a rejeição, então o evento será disparado
minhaPromessa;
```

### Exemplo com Tratamento de Erros
Aqui está um exemplo onde tratamos a rejeição utilizando `catch`, mas também configuramos o `onunhandledrejection` para capturar outras promessas não tratadas:

```javascript
window.onunhandledrejection = function(event) {
    console.error('Erro não tratado:', event.reason);
};

const promessaTratada = new Promise((resolve, reject) => {
    reject('Erro tratado com catch');
});

// Tratando a rejeição
promessaTratada.catch(error => console.log('Capturado:', error));
```

## Explicação
### Armadilhas Comuns
1. **Falta de manipulador**: Se você não definir um manipulador para `onunhandledrejection`, os erros podem passar despercebidos e dificultar a depuração da aplicação.
2. **Eventos globais**: O `onunhandledrejection` é um evento global, o que significa que ele capturará rejeições de qualquer parte da aplicação. Isso pode levar a confusões se não for bem gerenciado.
3. **Desempenho**: Capturar e lidar com erros de promessas não tratadas pode impactar o desempenho da aplicação se não for feito de forma eficiente.

### Notas Adicionais
- O evento `unhandledrejection` é suportado na maioria dos navegadores modernos, mas sempre verifique a compatibilidade se você estiver visando ambientes específicos.
- É uma boa prática sempre tentar tratar erros de promessas utilizando `catch`, mas o `onunhandledrejection` serve como uma rede de segurança adicional.

## Resumo em Uma Linha
O evento `onunhandledrejection` em JavaScript permite capturar e gerenciar promessas que foram rejeitadas sem tratamento, melhorando a robustez da aplicação.