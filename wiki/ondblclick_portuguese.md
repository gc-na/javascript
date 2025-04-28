<!--
Meta Description: # Ondblclick: O Evento de Duplo Clique em JavaScript ## Sinopse O evento `ondblclick` em JavaScript é um manipulador de eventos que é acionado quando ...
Meta Keywords: ondblclick, html, evento, clique, que
-->

# Ondblclick: O Evento de Duplo Clique em JavaScript

## Sinopse
O evento `ondblclick` em JavaScript é um manipulador de eventos que é acionado quando um usuário clica duas vezes rapidamente em um elemento da página. Este evento é frequentemente utilizado para criar interações dinâmicas e responsivas em aplicações da web.

## Documentação
O evento `ondblclick` faz parte da interface de eventos do DOM (Document Object Model) e pode ser utilizado em quase todos os elementos HTML. Ele é utilizado para capturar a ação de um duplo clique do mouse, permitindo que os desenvolvedores executem funções específicas em resposta a essa ação.

### Propósito
O principal objetivo do evento `ondblclick` é permitir que ações específicas sejam realizadas quando um usuário clica duas vezes em um elemento. Isso pode ser útil, por exemplo, para abrir um diálogo, editar textos ou expandir informações em uma interface.

### Uso
Para utilizar o evento `ondblclick`, você pode atribuí-lo diretamente no HTML ou usar a função `addEventListener` em JavaScript.

#### Atribuição Direta no HTML:
```html
<div ondblclick="minhaFuncao()">Clique duas vezes aqui!</div>
```

#### Atribuição via JavaScript:
```javascript
const elemento = document.getElementById('meuElemento');
elemento.ondblclick = function() {
    minhaFuncao();
};
```

Ou usando `addEventListener`:
```javascript
const elemento = document.getElementById('meuElemento');
elemento.addEventListener('dblclick', minhaFuncao);
```

## Exemplos
### Exemplo 1: Duplo Clique para Alerta
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo Ondblclick</title>
</head>
<body>
    <div ondblclick="alert('Você clicou duas vezes!')">Clique duas vezes aqui!</div>
</body>
</html>
```

### Exemplo 2: Alterar o Texto ao Clicar
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo Ondblclick</title>
</head>
<body>
    <div id="meuElemento">Clique duas vezes para mudar este texto.</div>
    <script>
        document.getElementById('meuElemento').ondblclick = function() {
            this.innerHTML = 'Texto alterado!';
        };
    </script>
</body>
</html>
```

## Explicação
### Armadilhas Comuns
- **Não confundir com `onclick`**: O evento `ondblclick` é acionado apenas após dois cliques rápidos, enquanto `onclick` é acionado em cada clique. Isso pode levar a comportamentos inesperados se ambos os eventos forem usados no mesmo elemento.
- **Tempo Entre Cliques**: O tempo entre os dois cliques deve ser rápido (geralmente menos de 500ms) para que o evento `ondblclick` seja acionado. Um intervalo maior fará com que o evento não seja registrado.
- **Uso em Dispositivos Touch**: Em dispositivos móveis, o evento `ondblclick` pode não se comportar como esperado, já que a interação touch não é a mesma que no desktop.

## Resumo em Uma Linha
O `ondblclick` é um evento JavaScript que permite executar ações em resposta a um duplo clique do mouse em elementos HTML.