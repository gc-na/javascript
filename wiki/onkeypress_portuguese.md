<!--
Meta Description: # onkeypress: Manipulando Eventos de Teclado em JavaScript ## Sinopse O evento `onkeypress` em JavaScript é utilizado para capturar a entrada do tecla...
Meta Keywords: onkeypress, evento, html, event, para
-->

# onkeypress: Manipulando Eventos de Teclado em JavaScript

## Sinopse
O evento `onkeypress` em JavaScript é utilizado para capturar a entrada do teclado, permitindo que os desenvolvedores executem ações específicas quando uma tecla é pressionada.

## Documentação
O `onkeypress` é um evento que ocorre quando uma tecla é pressionada e liberada. Este evento é frequentemente utilizado em formulários e interfaces de usuário para criar interações dinâmicas, como validações em tempo real ou respostas instantâneas a entradas do usuário.

### Propósito
O principal objetivo do evento `onkeypress` é detectar a entrada do teclado, permitindo que scripts JavaScript respondam a ações do usuário.

### Uso
O evento pode ser aplicado a elementos HTML, como `<input>`, `<textarea>`, ou até mesmo ao documento inteiro. A sintaxe básica para utilizar `onkeypress` é a seguinte:

```html
<input type="text" onkeypress="funcaoParaExecutar()">
```

### Detalhes
- O evento `onkeypress` é acionado apenas para teclas que produzem um caractere (como letras e números). Teclas de controle, como `Shift`, `Ctrl`, e `Alt`, não disparam esse evento.
- Para capturar todas as teclas, incluindo teclas de controle, recomenda-se usar `onkeydown` ou `onkeyup`.

## Exemplos

### Exemplo 1: Capturando uma tecla pressionada
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo onkeypress</title>
    <script>
        function mostrarTecla(event) {
            alert("Você pressionou a tecla: " + String.fromCharCode(event.which));
        }
    </script>
</head>
<body>
    <input type="text" onkeypress="mostrarTecla(event)">
</body>
</html>
```

### Exemplo 2: Resposta a uma tecla específica
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Tecla Específica</title>
    <script>
        function verificarTecla(event) {
            if (event.which === 13) { // 13 é o código da tecla "Enter"
                alert("Você pressionou Enter!");
            }
        }
    </script>
</head>
<body>
    <input type="text" onkeypress="verificarTecla(event)">
</body>
</html>
```

## Explicação
Embora `onkeypress` seja útil, existem algumas armadilhas a serem observadas:

1. **Compatibilidade de Navegador**: O evento `onkeypress` não é suportado em todos os navegadores de forma idêntica, especialmente em navegadores mais antigos. Para garantir compatibilidade, considere usar `onkeydown` ou `onkeyup`.
  
2. **Teclas de Controle**: Como mencionado, teclas que não produzem caracteres não disparam o evento `onkeypress`. Para ações que requerem o uso dessas teclas, prefira `onkeydown`.

3. **Uso de event.which**: O valor retornado por `event.which` pode variar entre navegadores. Recomenda-se utilizar `event.key` para uma abordagem mais moderna e consistente.

## Resumo em Uma Linha
O evento `onkeypress` em JavaScript permite que desenvolvedores capturem e respondam a entradas de teclado, oferecendo interatividade em aplicações web.