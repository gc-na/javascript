<!--
Meta Description: # onbeforeunload: Entenda o Comportamento de Saída em JavaScript ## Sinopse O evento `onbeforeunload` em JavaScript permite que os desenvolvedores int...
Meta Keywords: onbeforeunload, que, pode, para, não
-->

# onbeforeunload: Entenda o Comportamento de Saída em JavaScript

## Sinopse
O evento `onbeforeunload` em JavaScript permite que os desenvolvedores interceptem a tentativa de um usuário de sair de uma página, seja por recarregar, fechar a aba ou navegar para outra URL. Este evento é útil para avisar os usuários sobre possíveis perdas de dados.

## Documentação
O evento `onbeforeunload` é acionado antes que uma página seja descarregada. Ele fornece uma oportunidade para que os desenvolvedores exibam um aviso ao usuário, permitindo que eles confirmem se realmente desejam sair da página.

### Propósito
O principal objetivo do `onbeforeunload` é evitar que os usuários percam informações importantes, como dados não salvos em formulários.

### Uso
Para utilizar o `onbeforeunload`, você pode adicionar um listener de evento ao objeto `window`. A sintaxe básica é a seguinte:

```javascript
window.onbeforeunload = function(event) {
    // Mensagem personalizada (dependendo do navegador, pode não ser exibida)
    const message = "Você tem certeza que deseja sair? Você pode perder alterações não salvas!";
    event.returnValue = message; // Para a maioria dos navegadores
    return message; // Para navegadores mais antigos
};
```

### Detalhes
- O `event.returnValue` deve ser definido para exibir uma mensagem de confirmação.
- A mensagem personalizada pode não ser exibida em navegadores modernos, que mostram um texto padrão em vez da mensagem definida pelo desenvolvedor.
- O evento pode ser cancelado se o usuário não tiver interagido com a página, dependendo das políticas do navegador.

## Exemplos
### Exemplo Básico
```javascript
window.onbeforeunload = function(event) {
    const message = "Você tem certeza que deseja sair? Você pode perder alterações não salvas!";
    event.returnValue = message; // Para navegadores modernos
    return message; // Para navegadores mais antigos
};
```

### Exemplo com Condição
```javascript
let isFormDirty = false;

document.getElementById('myForm').addEventListener('change', function() {
    isFormDirty = true;
});

window.onbeforeunload = function(event) {
    if (isFormDirty) {
        const message = "Você tem certeza que deseja sair? Você pode perder alterações não salvas!";
        event.returnValue = message;
        return message;
    }
};
```

## Explicação
### Armadilhas Comuns
- **Navegadores Diferentes**: O comportamento do `onbeforeunload` pode variar entre navegadores. Alguns podem ignorar mensagens personalizadas e exibir apenas um texto padrão.
- **Interação do Usuário**: O evento pode não ser acionado se o usuário não interagir com a página. Assim, é importante garantir que os usuários tenham a oportunidade de ver o aviso.
- **Desempenho**: O uso excessivo de `onbeforeunload` pode impactar a experiência do usuário, especialmente se a página estiver constantemente perguntando se o usuário deseja sair.

## Resumo em Uma Linha
O evento `onbeforeunload` permite que desenvolvedores em JavaScript alertem os usuários sobre a possibilidade de perda de dados ao tentarem sair de uma página.