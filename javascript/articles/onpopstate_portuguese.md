<!--
Meta Description: # onpopstate: Entendendo o Evento de Mudança de Estado no JavaScript ## Sinopse O evento `onpopstate` no JavaScript é utilizado para detectar mudanças...
Meta Keywords: onpopstate, page, evento, página, estado
-->

# onpopstate: Entendendo o Evento de Mudança de Estado no JavaScript

## Sinopse
O evento `onpopstate` no JavaScript é utilizado para detectar mudanças na história do navegador, permitindo a manipulação eficaz do histórico de navegação durante aplicações de página única (SPA).

## Documentação
### O que é o onpopstate?
O evento `onpopstate` é disparado quando o usuário navega para um estado anterior na sessão de histórico do navegador. Esse evento é crucial para aplicações que utilizam a API History, pois permite que desenvolvedores implementem funcionalidades específicas ao navegar entre estados.

### Uso
Para utilizar o `onpopstate`, você deve adicionar um listener ao objeto `window`. O evento é associado a alterações na pilha de histórico e é frequentemente usado em conjunto com a função `history.pushState()` e `history.replaceState()`.

```javascript
window.onpopstate = function(event) {
    if (event.state) {
        console.log('Estado atual:', event.state);
    } else {
        console.log('Nenhum estado associado.');
    }
};
```

### Detalhes
- **Eventos disparados**: O evento `onpopstate` é disparado somente quando o usuário navega para um estado anterior ou seguinte que foi definido usando `pushState()` ou `replaceState()`.
- **Objeto de evento**: O objeto do evento contém uma propriedade `state`, que contém dados associados ao estado, se houver.
- **Compatibilidade**: O `onpopstate` é suportado em todos os navegadores modernos, mas deve ser testado em versões mais antigas para garantir compatibilidade.

## Exemplos
### Exemplo Básico
```javascript
// Adicionando estados à pilha de histórico
history.pushState({page: 1}, "Página 1", "?page=1");
history.pushState({page: 2}, "Página 2", "?page=2");

// Escutando o evento onpopstate
window.onpopstate = function(event) {
    if (event.state) {
        console.log('Você está na página:', event.state.page);
    }
};
```

Neste exemplo, ao pressionar o botão de voltar do navegador, o console exibirá qual página foi acessada.

### Exemplo com Manipulação de DOM
```javascript
window.onpopstate = function(event) {
    const contentDiv = document.getElementById('content');
    if (event.state) {
        contentDiv.innerHTML = 'Você está na página ' + event.state.page;
    } else {
        contentDiv.innerHTML = 'Página inicial';
    }
};

// Exemplo de uso de pushState
function navigateTo(page) {
    history.pushState({page: page}, "Página " + page, "?page=" + page);
    document.getElementById('content').innerHTML = 'Você está na página ' + page;
}
```

## Explicação
### Armadilhas Comuns
- **Não disparar em navegação inicial**: O evento `onpopstate` não é acionado ao carregar a página pela primeira vez. Isso pode causar confusão se você esperar que o estado inicial seja tratado imediatamente.
- **Manipulação de estado**: É importante garantir que os estados sejam bem gerenciados. Se um estado for adicionado ao histórico sem dados, `event.state` será `null`, o que pode causar erros inesperados se não for tratado corretamente.
- **Cuidado com a URL**: Alterar a URL sem adicionar um estado correspondente pode levar a uma experiência de usuário confusa.

## Resumo em Uma Linha
O evento `onpopstate` no JavaScript permite a manipulação do histórico de navegação, essencial para o funcionamento de aplicações de página única (SPA).