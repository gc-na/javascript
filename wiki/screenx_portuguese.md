<!--
Meta Description: # screenX: A Propriedade da Posição do Cursor em JavaScript ## Sinopse A propriedade `screenX` em JavaScript fornece a posição horizontal do ponteiro ...
Meta Keywords: screenx, html, posição, propriedade, mouse
-->

# screenX: A Propriedade da Posição do Cursor em JavaScript

## Sinopse
A propriedade `screenX` em JavaScript fornece a posição horizontal do ponteiro do mouse em relação à tela, permitindo que desenvolvedores web capturem a localização exata do cursor em pixels.

## Documentação
A propriedade `screenX` é uma das propriedades do objeto `MouseEvent`. Ela retorna a posição horizontal da localização do ponteiro do mouse em relação à tela do dispositivo, sendo medida em pixels. Essa propriedade é especialmente útil em interações de eventos, como cliques e movimentos do mouse, permitindo que os desenvolvedores implementem funcionalidades baseadas na posição do cursor.

### Uso
A `screenX` pode ser acessada em eventos de mouse, como `click`, `mousemove`, `mousedown` e `mouseup`. Para utilizá-la, geralmente você associará um manipulador de eventos a um elemento HTML e, dentro desse manipulador, acessará a propriedade.

### Sintaxe
```javascript
element.addEventListener('event', function(event) {
    console.log(event.screenX);
});
```

## Exemplos

### Exemplo Básico de Uso
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de screenX</title>
</head>
<body>
    <h1>Movimente o Mouse</h1>
    <script>
        document.addEventListener('mousemove', function(event) {
            console.log("Posição X na tela: " + event.screenX);
        });
    </script>
</body>
</html>
```

### Exemplo de Clique
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de Clique e screenX</title>
</head>
<body>
    <button id="meuBotao">Clique Aqui</button>
    <script>
        document.getElementById('meuBotao').addEventListener('click', function(event) {
            alert("Posição X na tela ao clicar: " + event.screenX);
        });
    </script>
</body>
</html>
```

## Explicação
Embora a `screenX` seja uma ferramenta poderosa, existem algumas considerações importantes:

- **Compatibilidade do Navegador**: A propriedade `screenX` é amplamente suportada em todos os navegadores modernos, mas sempre verifique a compatibilidade para navegadores mais antigos.
- **Interação com outros elementos**: Ao usar `screenX`, considere que a posição do cursor pode ser influenciada por outros elementos da interface de usuário, como barras de rolagem e margens de janela.
- **Unidade de Medida**: Os valores retornados por `screenX` são sempre em pixels, o que pode ser relevante ao implementar lógicas baseadas em dimensões.

## Resumo em Uma Linha
A propriedade `screenX` em JavaScript fornece a posição horizontal do ponteiro do mouse em relação à tela, permitindo interações precisas em eventos de mouse.