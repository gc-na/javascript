<!--
Meta Description: # OnClick: O Evento de Clique em JavaScript ## Sinopse O evento `onclick` em JavaScript é uma propriedade que permite adicionar uma funcionalidade de ...
Meta Keywords: onclick, html, javascript, que, evento
-->

# OnClick: O Evento de Clique em JavaScript

## Sinopse
O evento `onclick` em JavaScript é uma propriedade que permite adicionar uma funcionalidade de clique a elementos HTML, possibilitando a execução de código JavaScript em resposta a interações do usuário.

## Documentação
O `onclick` é um evento fundamental no JavaScript que é acionado quando um elemento é clicado. Esse evento pode ser utilizado em diversos elementos HTML, como botões, links e imagens. A propriedade `onclick` pode ser atribuída diretamente no HTML ou através de JavaScript, permitindo flexibilidade na implementação de interações.

### Uso
Para utilizar o evento `onclick`, você pode definir uma função que será chamada quando o elemento for clicado. Abaixo está a sintaxe básica:

```html
<button onclick="minhaFuncao()">Clique aqui</button>
```

Ou, utilizando JavaScript:

```javascript
const botao = document.getElementById('meuBotao');
botao.onclick = function() {
    alert('Botão clicado!');
};
```

### Detalhes
- O `onclick` pode ser usado em qualquer elemento HTML que possa ser clicado.
- É possível adicionar múltiplos manipuladores de eventos usando `addEventListener`.
- O evento pode ser cancelado usando o método `preventDefault()` caso você esteja lidando com um evento que tem um comportamento padrão (como um link).

## Exemplos

### Exemplo 1: Botão Simples
```html
<button onclick="alert('Você clicou no botão!')">Clique aqui</button>
```

### Exemplo 2: Uso com JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo OnClick</title>
</head>
<body>
    <button id="meuBotao">Clique em mim</button>
    <script>
        document.getElementById('meuBotao').onclick = function() {
            console.log('Botão foi clicado!');
        };
    </script>
</body>
</html>
```

### Exemplo 3: Uso com `addEventListener`
```html
<button id="meuBotao">Clique aqui</button>
<script>
    const botao = document.getElementById('meuBotao');
    botao.addEventListener('click', function() {
        alert('Você usou addEventListener!');
    });
</script>
```

## Explicação
Embora o `onclick` seja uma maneira eficaz de lidar com eventos de clique, existem algumas armadilhas comuns que os desenvolvedores devem evitar:

- **Múltiplos Eventos**: Se você atribuir uma nova função ao `onclick`, a função anterior será sobrescrita. Para adicionar múltiplos manipuladores, use `addEventListener`.
  
- **Eventos em Elementos Não Interativos**: Tentar usar `onclick` em elementos que não são interativos (como `<div>` ou `<span>`) pode levar a comportamentos inesperados se não forem manipulados corretamente.

- **Prevenção de Comportamento Padrão**: Se você estiver lidando com links (`<a>`), lembre-se de usar `event.preventDefault()` se não quiser que a página seja redirecionada quando o link for clicado.

## Resumo em Uma Frase
O evento `onclick` em JavaScript permite que você execute uma função quando um elemento HTML é clicado, proporcionando interatividade em suas aplicações web.