<!--
Meta Description: # onkeydown: Capturando Eventos de Teclado em JavaScript ## Sinopse O evento `onkeydown` no JavaScript permite que desenvolvedores capturem e responda...
Meta Keywords: tecla, onkeydown, html, event, evento
-->

# onkeydown: Capturando Eventos de Teclado em JavaScript

## Sinopse
O evento `onkeydown` no JavaScript permite que desenvolvedores capturem e respondam a pressionamentos de tecla dentro de elementos HTML, proporcionando interatividade e controle nas aplicações web.

## Documentação
O `onkeydown` é um evento que é acionado quando uma tecla é pressionada enquanto o elemento que o escuta está em foco. Este evento é útil para implementar funcionalidades como atalhos de teclado, jogos, formulários dinâmicos e navegação.

### Propósito
O propósito do `onkeydown` é permitir que os desenvolvedores detectem qual tecla foi pressionada e realizem ações com base nessa entrada do usuário.

### Uso
O `onkeydown` pode ser utilizado diretamente em um elemento HTML como um atributo, ou pode ser adicionado via JavaScript utilizando o método `addEventListener`.

#### Sintaxe
```html
<input type="text" onkeydown="funcaoAqui(event)">
```

Ou via JavaScript:
```javascript
document.getElementById('meuInput').addEventListener('keydown', function(event) {
    // lógica aqui
});
```

### Detalhes
- O evento `onkeydown` é disparado antes do caractere correspondente ser inserido no campo de entrada.
- Ele é útil para capturar teclas especiais, como `Shift`, `Ctrl`, `Alt` e as teclas de navegação (setas, home, end, etc.).
- O objeto de evento passado para a função contém informações sobre a tecla pressionada, incluindo a propriedade `key`, que retorna o valor da tecla, e `keyCode`, que fornece o código numérico da tecla.

## Exemplos

### Exemplo 1: Capturando uma tecla simples
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo onkeydown</title>
</head>
<body>
    <input type="text" id="meuInput" onkeydown="mostrarTecla(event)">
    <p id="resultado"></p>

    <script>
        function mostrarTecla(event) {
            document.getElementById('resultado').innerText = 'Tecla pressionada: ' + event.key;
        }
    </script>
</body>
</html>
```

### Exemplo 2: Usando addEventListener
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo onkeydown com addEventListener</title>
</head>
<body>
    <input type="text" id="meuInput">
    <p id="resultado"></p>

    <script>
        document.getElementById('meuInput').addEventListener('keydown', function(event) {
            document.getElementById('resultado').innerText = 'Tecla pressionada: ' + event.key;
        });
    </script>
</body>
</html>
```

## Explicação
Um erro comum ao usar `onkeydown` é não verificar se o evento deve ser tratado. Por exemplo, pressionar a tecla `Enter` em um campo de entrada pode acionar um comportamento indesejado, como o envio de um formulário. Para evitar isso, os desenvolvedores devem sempre validar a tecla pressionada e, se necessário, prevenir a ação padrão utilizando `event.preventDefault()`.

Além disso, é importante estar ciente de que o `keyCode` está obsoleto e é recomendado utilizar `event.key` para obter o valor da tecla.

## Resumo em Uma Linha
O evento `onkeydown` em JavaScript permite capturar pressionamentos de tecla para criar interatividade nas aplicações web.