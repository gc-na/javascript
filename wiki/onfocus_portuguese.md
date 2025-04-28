<!--
Meta Description: # onfocus: O Evento de Foco em JavaScript ## Sinopse O evento `onfocus` em JavaScript é utilizado para detectar quando um elemento, como um campo de e...
Meta Keywords: onfocus, foco, html, javascript, quando
-->

# onfocus: O Evento de Foco em JavaScript

## Sinopse
O evento `onfocus` em JavaScript é utilizado para detectar quando um elemento, como um campo de entrada, ganha foco. Isso é particularmente útil para melhorar a experiência do usuário em formulários e interfaces interativas.

## Documentação
O evento `onfocus` é acionado quando um elemento se torna o foco da interação do usuário, permitindo que você execute funções quando o usuário começa a interagir com um campo específico. O foco pode ser dado a elementos de formulário, como `<input>`, `<textarea>`, e `<select>`, bem como a outros elementos que podem receber foco, como `<a>` e `<button>`.

### Propósito
O principal propósito do `onfocus` é melhorar a usabilidade ao proporcionar feedback visual ou funcional quando um elemento está ativo.

### Uso
O evento `onfocus` pode ser adicionado diretamente em um elemento HTML ou através de JavaScript. Aqui estão algumas maneiras de utilizá-lo:

#### Atributo HTML
```html
<input type="text" onfocus="alert('Campo focado!')">
```

#### JavaScript
```javascript
document.getElementById("meuInput").onfocus = function() {
    alert('Campo focado!');
};
```

## Exemplos
### Exemplo 1: Usando `onfocus` em um campo de entrada
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo onfocus</title>
</head>
<body>
    <input type="text" id="meuInput" onfocus="this.style.backgroundColor='yellow'">
    <script>
        // Aqui, quando o campo de entrada ganha foco, sua cor de fundo muda para amarelo.
    </script>
</body>
</html>
```

### Exemplo 2: Usando `onfocus` com JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo onfocus com JavaScript</title>
</head>
<body>
    <input type="text" id="meuInput">
    <script>
        const input = document.getElementById("meuInput");
        input.onfocus = function() {
            console.log('Campo de texto ganhou foco.');
        };
    </script>
</body>
</html>
```

## Explicação
Embora o `onfocus` seja uma ferramenta poderosa, é importante estar ciente de alguns pontos:

- **Elementos Não Focáveis**: Apenas certos elementos podem receber foco. Certifique-se de que o elemento em questão esteja apto para isso.
- **Acessibilidade**: É essencial garantir que as interações de foco não prejudicam a experiência do usuário com deficiência. Use atributos ARIA quando necessário.
- **Compatibilidade com Dispositivos Móveis**: Em dispositivos móveis, o foco pode se comportar de maneira diferente, especialmente em campos de entrada, devido ao teclado virtual que aparece.

## Resumo em Uma Linha
O evento `onfocus` em JavaScript é utilizado para detectar quando um elemento de formulário ganha foco, permitindo interações dinâmicas e responsivas.