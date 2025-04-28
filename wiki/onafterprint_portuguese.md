<!--
Meta Description: # onafterprint: Manipulando Eventos de Impressão em JavaScript ## Sinopse O evento `onafterprint` em JavaScript é utilizado para executar código após ...
Meta Keywords: impressão, onafterprint, evento, javascript, para
-->

# onafterprint: Manipulando Eventos de Impressão em JavaScript

## Sinopse
O evento `onafterprint` em JavaScript é utilizado para executar código após o término de uma impressão de página. Esse evento é particularmente útil para restaurar alterações na interface do usuário que foram feitas antes da impressão.

## Documentação
### Propósito
O evento `onafterprint` faz parte da interface `Window` do JavaScript e é acionado quando a janela de impressão é fechada, permitindo que os desenvolvedores realizem ações específicas após a impressão, como reverter estilos ou ocultar elementos que foram exibidos apenas para a impressão.

### Uso
Para usar o evento `onafterprint`, você deve adicionar um listener ao objeto `window`. A sintaxe básica é a seguinte:

```javascript
window.onafterprint = function() {
    // Código a ser executado após a impressão
};
```

Além disso, você pode utilizar o método `addEventListener` para registrar o evento de forma mais flexível:

```javascript
window.addEventListener('afterprint', function() {
    // Código a ser executado após a impressão
});
```

### Detalhes
- O evento `onafterprint` é parte dos eventos de impressão que também incluem `onbeforeprint`, que é acionado antes da janela de impressão ser exibida.
- É suportado na maioria dos navegadores modernos, mas é sempre bom verificar a compatibilidade antes de implementar.

## Exemplos
### Exemplo Básico
Aqui está um exemplo simples que altera o fundo da página antes da impressão e o reverte após a impressão:

```javascript
window.onbeforeprint = function() {
    document.body.style.backgroundColor = 'lightgray';
};

window.onafterprint = function() {
    document.body.style.backgroundColor = '';
};
```

### Exemplo com `addEventListener`
Usando `addEventListener`, você pode adicionar múltiplos manipuladores para o mesmo evento:

```javascript
window.addEventListener('beforeprint', function() {
    console.log('Preparando para imprimir...');
});

window.addEventListener('afterprint', function() {
    console.log('Impressão concluída.');
});
```

## Explicação
### Armadilhas Comuns
- **Compatibilidade**: Verifique a compatibilidade do navegador ao usar esse evento, pois alguns navegadores mais antigos podem não suportá-lo adequadamente.
- **Múltiplos Listeners**: Se você usar tanto `onbeforeprint` quanto `onafterprint`, tenha em mente que a ordem de execução é importante. Certifique-se de que as alterações necessárias sejam feitas antes e revertidas após a impressão.
- **Performance**: Evite inserir operações pesadas dentro dos manipuladores de eventos, pois isso pode afetar a performance durante a impressão.

## Resumo em Uma Linha
O evento `onafterprint` em JavaScript permite executar ações específicas após o fechamento da janela de impressão, sendo útil para restaurar a interface do usuário.