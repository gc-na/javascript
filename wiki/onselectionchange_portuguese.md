<!--
Meta Description: # onselectionchange: Uma Visão Geral do Evento em JavaScript ## Sinopse O evento `onselectionchange` em JavaScript é um recurso utilizado para detecta...
Meta Keywords: texto, onselectionchange, evento, document, para
-->

# onselectionchange: Uma Visão Geral do Evento em JavaScript

## Sinopse
O evento `onselectionchange` em JavaScript é um recurso utilizado para detectar alterações na seleção de elementos de entrada de texto, como `<input>` e `<textarea>`. Este evento é útil para implementar funcionalidades dinâmicas que respondem à interação do usuário com o conteúdo selecionado.

## Documentação
O evento `onselectionchange` é disparado sempre que a seleção de texto em um campo de entrada muda. Isso pode incluir a seleção, o desmarcar ou o ajuste do texto selecionado. É uma parte importante da API de eventos do DOM e é frequentemente utilizado em aplicações que requerem interações dinâmicas e responsivas.

### Propósito
O principal objetivo do `onselectionchange` é permitir que os desenvolvedores respondam a mudanças na seleção de texto, possibilitando o desenvolvimento de funcionalidades como formatação de texto, cópia para a área de transferência, ou a exibição de informações contextuais relacionadas ao texto selecionado.

### Uso
Para utilizar o evento `onselectionchange`, você pode adicioná-lo a um elemento de entrada de texto ou a um documento. Abaixo está um exemplo básico de como configurar um ouvinte de evento para `onselectionchange`:

```javascript
document.addEventListener("selectionchange", function() {
    const selection = document.getSelection();
    console.log("Texto selecionado:", selection.toString());
});
```

## Exemplos

### Exemplo 1: Logar Texto Selecionado
```html
<input type="text" id="inputField" value="Selecione este texto!">
<script>
    document.addEventListener("selectionchange", function() {
        const selection = document.getSelection();
        console.log("Texto selecionado:", selection.toString());
    });
</script>
```

### Exemplo 2: Alterar Estilo com Seleção
```html
<textarea id="textArea" rows="4" cols="50">Experimente selecionar este texto e veja o estilo mudar.</textarea>
<style>
    .highlight {
        background-color: yellow;
    }
</style>
<script>
    document.addEventListener("selectionchange", function() {
        const selection = document.getSelection();
        if (selection.toString()) {
            document.getElementById('textArea').classList.add('highlight');
        } else {
            document.getElementById('textArea').classList.remove('highlight');
        }
    });
</script>
```

## Explicação
Um dos problemas comuns ao trabalhar com o evento `onselectionchange` é que ele pode ser disparado frequentemente, especialmente em campos de entrada onde o usuário realiza múltiplas interações. Isso pode levar a um desempenho degradado se ações pesadas forem executadas dentro do manipulador de eventos. Portanto, é aconselhável usar debouncing ou throttling para otimizar a performance.

Outro ponto a ser observado é que o evento `onselectionchange` não é suportado em todos os navegadores. Antes de implementá-lo, verifique a compatibilidade do navegador para garantir que a funcionalidade desejada funcione uniformemente em diferentes plataformas.

## Resumo em Uma Linha
O evento `onselectionchange` em JavaScript permite detectar e responder a mudanças na seleção de texto em campos de entrada, proporcionando uma interação mais dinâmica e responsiva.