<!--
Meta Description: # MediaQueryListEvent em JavaScript: Entendendo os Eventos de Consulta de Mídia ## Sinopse O `MediaQueryListEvent` é um objeto que representa eventos ...
Meta Keywords: que, mediaquerylistevent, mídia, addeventlistener, para
-->

# MediaQueryListEvent em JavaScript: Entendendo os Eventos de Consulta de Mídia

## Sinopse
O `MediaQueryListEvent` é um objeto que representa eventos relacionados a mudanças em consultas de mídia, permitindo que desenvolvedores detectem e respondam a alterações em características de apresentação, como largura da tela, orientação e outros parâmetros.

## Documentação
O `MediaQueryListEvent` é associado à interface `MediaQueryList`, que permite escutar mudanças em consultas de mídia através do método `addListener()` ou `addEventListener()`. Quando a condição da consulta de mídia muda (por exemplo, de true para false ou vice-versa), um evento `MediaQueryListEvent` é disparado, informando que uma alteração ocorreu. 

### Propósito
O principal objetivo do `MediaQueryListEvent` é permitir que os desenvolvedores respondam dinamicamente a mudanças em consultas de mídia, facilitando a criação de layouts responsivos e interativos.

### Uso
Para utilizar o `MediaQueryListEvent`, siga os seguintes passos:

1. Crie uma consulta de mídia usando `window.matchMedia()`.
2. Adicione um ouvinte de evento para escutar mudanças na consulta.
3. Implemente uma função de callback que será chamada quando a consulta mudar.

```javascript
const mediaQuery = window.matchMedia('(max-width: 600px)');

const handleMediaChange = (event) => {
    if (event.matches) {
        console.log('A tela é menor que 600px');
    } else {
        console.log('A tela é maior que 600px');
    }
};

// Adiciona o ouvinte de evento
mediaQuery.addEventListener('change', handleMediaChange);

// Chama a função inicialmente para verificar o estado atual
handleMediaChange(mediaQuery);
```

## Exemplos
### Exemplo Básico de Escuta de Mudanças
```javascript
const mq = window.matchMedia('(prefers-color-scheme: dark)');

const colorSchemeChangeHandler = (event) => {
    if (event.matches) {
        console.log('Tema escuro ativado');
    } else {
        console.log('Tema claro ativado');
    }
};

mq.addEventListener('change', colorSchemeChangeHandler);
```

### Exemplo com Várias Consultas de Mídia
```javascript
const query1 = window.matchMedia('(max-width: 800px)');
const query2 = window.matchMedia('(orientation: landscape)');

const handleMultipleQueries = (event) => {
    if (query1.matches) {
        console.log('A tela é menor que 800px');
    }

    if (query2.matches) {
        console.log('A orientação é paisagem');
    }
};

query1.addEventListener('change', handleMultipleQueries);
query2.addEventListener('change', handleMultipleQueries);
```

## Explicação
### Armadilhas Comuns
1. **Compatibilidade do Navegador**: Nem todos os navegadores suportam `addEventListener` para `MediaQueryList`. Para navegadores mais antigos, use `addListener()` como alternativa.
2. **Remoção de Ouvintes**: É importante remover ouvintes de eventos quando não forem mais necessários para evitar vazamentos de memória.

### Nota Adicional
Utilizar `MediaQueryListEvent` com `addEventListener` é a prática recomendada, pois oferece uma melhor interoperabilidade e suporte a recursos futuros.

## Resumo em Uma Linha
`MediaQueryListEvent` permite que desenvolvedores JavaScript respondam a mudanças em consultas de mídia, facilitando a criação de aplicações responsivas.