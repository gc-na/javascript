<!--
Meta Description: # oninput: O Evento de Entrada para Manipulação em Tempo Real no JavaScript ## Sinopse O evento `oninput` no JavaScript é utilizado para detectar muda...
Meta Keywords: oninput, html, que, evento, entrada
-->

# oninput: O Evento de Entrada para Manipulação em Tempo Real no JavaScript

## Sinopse
O evento `oninput` no JavaScript é utilizado para detectar mudanças em campos de entrada, como `input` e `textarea`, permitindo que desenvolvedores respondam em tempo real às interações do usuário.

## Documentação
O evento `oninput` é acionado sempre que o valor de um elemento de entrada muda. Ao contrário do evento `onchange`, que é disparado apenas quando o elemento perde o foco, o `oninput` é mais responsivo, permitindo uma interação imediata.

### Propósito
O objetivo principal do `oninput` é fornecer uma maneira eficiente e reativa de capturar alterações de dados em campos de entrada, facilitando validações, atualizações de interface e outras ações baseadas no valor atual do usuário.

### Uso
O `oninput` pode ser utilizado em elementos HTML como:

- `<input type="text">`
- `<textarea>`

A sintaxe básica para usar o `oninput` é a seguinte:

```html
<input type="text" oninput="minhaFuncao(this.value)">
```

Onde `minhaFuncao` é a função JavaScript a ser chamada toda vez que o valor do campo de entrada muda.

### Detalhes
- O evento `oninput` é suportado em todos os navegadores modernos.
- Pode ser usado em combinação com outros eventos para criar experiências de usuário mais dinâmicas, como validação instantânea de formulários ou sugestões automáticas.

## Exemplos

### Exemplo 1: Uso Básico de oninput
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemplo de oninput</title>
</head>
<body>
    <input type="text" oninput="document.getElementById('resultado').innerText = this.value">
    <p>Você digitou: <span id="resultado"></span></p>
</body>
</html>
```

### Exemplo 2: Validação em Tempo Real
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validação com oninput</title>
</head>
<body>
    <input type="text" oninput="validarEmail(this.value)">
    <p id="mensagem"></p>

    <script>
        function validarEmail(email) {
            const mensagem = document.getElementById('mensagem');
            const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            mensagem.innerText = regex.test(email) ? "Email válido" : "Email inválido";
        }
    </script>
</body>
</html>
```

## Explicação
Embora o `oninput` seja bastante útil, é importante lembrar que ele pode ser acionado frequentemente durante a digitação, o que pode levar a um desempenho reduzido se a função associada for complexa ou demorada. Para evitar problemas de desempenho, considere debouncing ou throttling nas funções que são chamadas em resposta a este evento.

Além disso, ao usar `oninput`, certifique-se de que o elemento de entrada esteja visível e acessível ao usuário, já que eventos em elementos ocultos ou desativados não serão capturados.

## Resumo em Uma Linha
O evento `oninput` no JavaScript permite capturar mudanças em tempo real em campos de entrada, proporcionando uma experiência interativa para o usuário.