<!--
Meta Description: # onmouseover: Manipulando Eventos de Mouse em JavaScript ## Sinopse O evento `onmouseover` é uma propriedade do DOM em JavaScript que permite detecta...
Meta Keywords: onmouseover, html, evento, mouse, que
-->

# onmouseover: Manipulando Eventos de Mouse em JavaScript

## Sinopse
O evento `onmouseover` é uma propriedade do DOM em JavaScript que permite detectar quando o ponteiro do mouse passa sobre um elemento HTML. Este evento é amplamente utilizado para criar interações dinâmicas e visuais em páginas web.

## Documentação
### Propósito
O `onmouseover` é usado para executar uma função ou um bloco de código sempre que o cursor do mouse entra na área de um elemento HTML. Esse evento é útil para melhorar a experiência do usuário, fornecendo feedback visual ou interatividade em elementos como botões, imagens e links.

### Uso
A propriedade `onmouseover` pode ser atribuída diretamente ao elemento HTML ou adicionada via JavaScript. Aqui estão as formas comuns de uso:

#### Atribuição Direta em HTML
```html
<div onmouseover="funcaoExemplo()">Passe o mouse aqui</div>
```

#### Atribuição via JavaScript
```javascript
const elemento = document.getElementById('meuElemento');
elemento.onmouseover = function() {
    // Código a ser executado
};
```

### Detalhes
- O evento `onmouseover` pode ser combinado com outros eventos, como `onmouseout`, para criar efeitos de destaque ou animações.
- É importante lembrar que os eventos de mouse podem ser disparados em elementos filhos, o que pode causar comportamento inesperado se não for tratado corretamente.

## Exemplos
### Exemplo Básico
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de onmouseover</title>
    <style>
        .destacar {
            background-color: yellow;
        }
    </style>
</head>
<body>

<div id="meuElemento" onmouseover="destacar()" onmouseout="removerDestacar()">Passe o mouse aqui</div>

<script>
    function destacar() {
        document.getElementById('meuElemento').classList.add('destacar');
    }

    function removerDestacar() {
        document.getElementById('meuElemento').classList.remove('destacar');
    }
</script>

</body>
</html>
```

### Exemplo com Imagem
```html
<img src="imagem.jpg" alt="Imagem" id="minhaImagem" onmouseover="this.style.opacity=0.5" onmouseout="this.style.opacity=1">
```

## Explicação
### Armadilhas Comuns
1. **Eventos em Elementos Filhos**: O `onmouseover` é acionado quando o mouse entra em qualquer parte do elemento, incluindo filhos. Para evitar comportamentos inesperados, pode ser útil usar `event.stopPropagation()` ou verificar a origem do evento.
   
2. **Performance**: Evite executar funções pesadas dentro do evento `onmouseover`, pois isso pode afetar a performance da página, especialmente se o evento for acionado repetidamente.

3. **Acessibilidade**: Lembre-se de que o evento `onmouseover` não é acessível para usuários que navegam com teclado ou leitores de tela. Considere implementar alternativas que funcionem em diferentes dispositivos.

## Resumo em Uma Linha
O evento `onmouseover` em JavaScript permite a execução de funções quando o mouse passa sobre um elemento HTML, promovendo interatividade e feedback visual na interface do usuário.