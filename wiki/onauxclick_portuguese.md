<!--
Meta Description: # onauxclick: O Evento de Clique Auxiliar no JavaScript ## Sinopse O `onauxclick` é um evento do JavaScript que é acionado quando um usuário clica em ...
Meta Keywords: que, onauxclick, evento, botão, com
-->

# onauxclick: O Evento de Clique Auxiliar no JavaScript

## Sinopse
O `onauxclick` é um evento do JavaScript que é acionado quando um usuário clica em um elemento com um botão auxiliar do mouse (geralmente o botão do meio ou o botão extra do mouse). Este evento é útil para criar interações personalizadas em páginas da web, especialmente em aplicativos que requerem ações específicas ao usar botões não tradicionais.

## Documentação
### Propósito
O evento `onauxclick` é projetado para capturar cliques que não envolvem os botões primários do mouse (geralmente o botão esquerdo). Isso permite que desenvolvedores implementem funcionalidades que respondem a cliques do botão do meio do mouse ou botões adicionais, como os encontrados em alguns mouses para jogos ou de escritório.

### Uso
O `onauxclick` pode ser utilizado em qualquer elemento HTML que suporte eventos. Para usar o `onauxclick`, você pode adicionar um ouvinte de evento diretamente no elemento ou utilizar métodos de manipulação de eventos do JavaScript.

#### Sintaxe:
```javascript
element.onauxclick = function(event) {
    // Código a ser executado quando o evento ocorre
};
```

### Detalhes
- O evento `onauxclick` é compatível com a maioria dos navegadores modernos.
- O objeto `event` passado para a função manipuladora contém informações sobre o evento, incluindo o botão que foi clicado.
- É importante notar que este evento pode não ser suportado em todos os navegadores ou versões mais antigas, por isso, deve-se verificar a compatibilidade.

## Exemplos

### Exemplo Básico
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de onauxclick</title>
</head>
<body>

<button id="meuBotao">Clique com o botão auxiliar</button>

<script>
    const botao = document.getElementById('meuBotao');
    
    botao.onauxclick = function(event) {
        alert('Você clicou com o botão auxiliar do mouse!');
    };
</script>

</body>
</html>
```

### Exemplo com Detalhes do Evento
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de onauxclick com Detalhes</title>
</head>
<body>

<div id="meuDiv" style="width: 200px; height: 200px; background-color: lightblue;">
    Clique com o botão auxiliar aqui!
</div>

<script>
    const div = document.getElementById('meuDiv');

    div.onauxclick = function(event) {
        console.log('Botão clicado:', event.button);
        alert('Você clicou com o botão auxiliar do mouse. O botão correspondente é: ' + event.button);
    };
</script>

</body>
</html>
```

## Explicação
Um dos erros comuns ao utilizar `onauxclick` é não considerar que esse evento pode não ser suportado em navegadores mais antigos. Portanto, é sempre bom testar a funcionalidade em diferentes ambientes. Outro ponto importante é que o evento pode não ser acionado em dispositivos que não possuem botões auxiliares, como alguns laptops que têm apenas um touchpad. Além disso, é crucial garantir que o comportamento esperado esteja claro para o usuário, já que cliques com botões não tradicionais podem não ter um comportamento intuitivo.

## Resumo em Uma Linha
O `onauxclick` é um evento do JavaScript que permite a captura de cliques realizados com botões auxiliares do mouse, facilitando interações personalizadas em aplicações web.