<!--
Meta Description: # PopStateEvent em JavaScript: Entendendo o Evento de Histórico ## Sinopse O `PopStateEvent` é um evento em JavaScript que é acionado quando o históri...
Meta Keywords: histórico, que, evento, popstateevent, para
-->

# PopStateEvent em JavaScript: Entendendo o Evento de Histórico

## Sinopse

O `PopStateEvent` é um evento em JavaScript que é acionado quando o histórico do navegador é modificado, permitindo que os desenvolvedores respondam a mudanças na pilha de histórico da aplicação.

## Documentação

### O que é o PopStateEvent?

O `PopStateEvent` é um evento que é gerado sempre que um usuário navega para um histórico anterior ou posterior na sessão da página. Esse evento é parte da API de História do HTML5, que permite manipular o histórico do navegador de forma mais eficiente.

### Propósito

O propósito do `PopStateEvent` é permitir que os desenvolvedores possam capturar e reagir a eventos de navegação, como quando um usuário volta ou avança entre páginas que utilizam o histórico do navegador. Isso é especialmente útil em aplicações de página única (SPA), onde o conteúdo é atualizado sem recarregar a página.

### Uso

Para usar o `PopStateEvent`, você deve adicionar um listener ao objeto `window`. O evento pode ser escutado da seguinte forma:

```javascript
window.addEventListener('popstate', function(event) {
    // Seu código aqui
});
```

Dentro do listener, você pode acessar a propriedade `event.state` para obter o estado associado à entrada do histórico que foi ativada.

### Detalhes

- O `PopStateEvent` é acionado apenas quando a navegação é feita através dos métodos `history.back()`, `history.forward()` ou `history.go()`.
- O evento não é acionado quando a página é carregada pela primeira vez ou quando o método `history.pushState()` é utilizado para adicionar uma nova entrada ao histórico.
- O método `pushState` pode ser usado para adicionar entradas ao histórico, enquanto o `replaceState` substitui a entrada atual.

## Exemplos

### Exemplo Básico de Uso do PopStateEvent

```javascript
// Adicionando um estado ao histórico
history.pushState({page: 1}, "Título 1", "?page=1");

// Adicionando um listener para o evento popstate
window.addEventListener('popstate', function(event) {
    if (event.state) {
        console.log('Navegando para a página: ', event.state.page);
    }
});

// Simulando a navegação
history.pushState({page: 2}, "Título 2", "?page=2");
history.back(); // Isso acionará o evento popstate
```

## Explicação

### Armadilhas Comuns

1. **Evento Não Acionado no Carregamento Inicial**: O `PopStateEvent` não é acionado ao carregar a página pela primeira vez. Isso pode confundir os desenvolvedores que esperam que o evento seja disparado imediatamente.
  
2. **Somente Navegação de Histórico**: O evento é acionado apenas em navegações que afetam o histórico, como voltar ou avançar. Usar `pushState` ou `replaceState` não acionará o evento.

3. **Acesso ao Estado**: Ao acessar `event.state`, se não houver um estado associado à entrada do histórico, essa propriedade será `null`. É importante verificar isso para evitar erros.

## Resumo em Uma Linha

O `PopStateEvent` em JavaScript permite que desenvolvedores capturem e respondam a mudanças no histórico do navegador, facilitando a navegação em aplicações dinâmicas.