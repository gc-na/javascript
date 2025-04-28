<!--
Meta Description: # oncontextmenu: Manipulando o Menu de Contexto em JavaScript ## Sinopse O evento `oncontextmenu` em JavaScript permite que desenvolvedores personaliz...
Meta Keywords: menu, html, oncontextmenu, contexto, evento
-->

# oncontextmenu: Manipulando o Menu de Contexto em JavaScript

## Sinopse
O evento `oncontextmenu` em JavaScript permite que desenvolvedores personalizem o comportamento do menu de contexto que aparece ao clicar com o botão direito do mouse em um elemento HTML.

## Documentação
O `oncontextmenu` é um evento que é disparado quando o usuário tenta abrir o menu de contexto (geralmente através do clique com o botão direito do mouse) em um elemento. Este evento pode ser utilizado para prevenir a exibição do menu padrão e implementar ações personalizadas, como exibir um menu contextual customizado.

### Propósito
O principal propósito do evento `oncontextmenu` é permitir que desenvolvedores controlem a interação do usuário com o menu de contexto, podendo desabilitar ações padrão ou implementar funcionalidades adicionais.

### Uso
Para utilizar o evento `oncontextmenu`, você pode adicionar um listener de evento em um elemento HTML. O evento pode ser usado diretamente no HTML ou configurado via JavaScript.

### Sintaxe
```html
<elemento oncontextmenu="função()">
```
ou
```javascript
elemento.addEventListener('contextmenu', função);
```

## Exemplos

### Exemplo 1: Prevenir o Menu de Contexto Padrão
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo oncontextmenu</title>
    <script>
        function prevenirMenu() {
            alert("O menu de contexto foi desabilitado!");
            return false; // Previne o menu de contexto padrão
        }
    </script>
</head>
<body>
    <div oncontextmenu="return prevenirMenu();">
        Clique com o botão direito aqui para ver o aviso.
    </div>
</body>
</html>
```

### Exemplo 2: Menu Contextual Personalizado
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Menu Contextual Personalizado</title>
    <style>
        #menu {
            display: none;
            position: absolute;
            background: #fff;
            border: 1px solid #ccc;
            padding: 10px;
        }
    </style>
    <script>
        function mostrarMenu(event) {
            event.preventDefault(); // Previne o menu padrão
            const menu = document.getElementById('menu');
            menu.style.display = 'block';
            menu.style.left = `${event.pageX}px`;
            menu.style.top = `${event.pageY}px`;
        }

        function esconderMenu() {
            const menu = document.getElementById('menu');
            menu.style.display = 'none';
        }

        window.addEventListener('click', esconderMenu);
    </script>
</head>
<body>
    <div oncontextmenu="mostrarMenu(event);">
        Clique com o botão direito aqui para abrir o menu contextual.
    </div>
    <div id="menu">
        <p>Opção 1</p>
        <p>Opção 2</p>
    </div>
</body>
</html>
```

## Explicação
Um dos principais erros ao utilizar o `oncontextmenu` é não prevenir o comportamento padrão do menu de contexto. Se o desenvolvedor não usar `event.preventDefault()`, o menu padrão ainda será exibido, tornando a implementação do menu personalizado ineficaz. Além disso, é importante considerar a acessibilidade, pois desabilitar o menu de contexto pode frustrar usuários que dependem dele.

## Resumo em Uma Frase
O `oncontextmenu` em JavaScript permite personalizar ou desabilitar o menu de contexto de elementos HTML, proporcionando interação mais controlada para o usuário.