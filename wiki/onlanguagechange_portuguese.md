<!--
Meta Description: # Evento `onlanguagechange` em JavaScript: Como Detectar Mudanças de Idioma ## Sinopse O evento `onlanguagechange` é uma funcionalidade do JavaScript ...
Meta Keywords: idioma, evento, onlanguagechange, mudanças, usuário
-->

# Evento `onlanguagechange` em JavaScript: Como Detectar Mudanças de Idioma

## Sinopse
O evento `onlanguagechange` é uma funcionalidade do JavaScript que permite detectar mudanças no idioma do usuário no navegador. Isso é especialmente útil para aplicativos e sites multilíngues que precisam se adaptar rapidamente às preferências de idioma do usuário.

## Documentação
O evento `onlanguagechange` é parte da interface `Window` e é acionado sempre que o idioma preferido do usuário for alterado. Esse evento é suportado pela maioria dos navegadores modernos e é uma ferramenta essencial para desenvolvedores que desejam criar experiências de usuário personalizadas.

### Propósito
O principal objetivo do evento `onlanguagechange` é fornecer uma maneira de os desenvolvedores detectarem alterações nas configurações de idioma e responderem a essas mudanças em tempo real. Isso permite que o conteúdo do site ou aplicativo seja atualizado para refletir o idioma selecionado pelo usuário.

### Uso
Para utilizar o evento `onlanguagechange`, você deve adicionar um ouvinte de eventos ao objeto `window`. O código a seguir ilustra como fazer isso:

```javascript
window.onlanguagechange = function() {
    console.log("O idioma do navegador foi alterado.");
    // Adicione sua lógica para atualizar o conteúdo do site aqui.
};
```

## Exemplos
### Exemplo Básico
Aqui está um exemplo simples que demonstra como escutar mudanças de idioma:

```javascript
window.onlanguagechange = function() {
    alert("O idioma do navegador foi alterado para: " + navigator.language);
};
```

### Exemplo com Atualização de Conteúdo
Neste exemplo, vamos atualizar um elemento de texto com base no idioma selecionado:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de mudança de idioma</title>
</head>
<body>
    <h1 id="titulo">Bem-vindo</h1>
    <script>
        window.onlanguagechange = function() {
            const idioma = navigator.language;
            const titulo = document.getElementById("titulo");

            if (idioma.startsWith('en')) {
                titulo.textContent = "Welcome";
            } else if (idioma.startsWith('es')) {
                titulo.textContent = "Bienvenido";
            } else {
                titulo.textContent = "Bem-vindo";
            }
        };
    </script>
</body>
</html>
```

## Explicação
### Armadilhas Comuns
- **Suporte do Navegador**: Embora a maioria dos navegadores modernos suporte o evento `onlanguagechange`, sempre é bom verificar a compatibilidade, especialmente se o seu público-alvo utiliza navegadores mais antigos.
- **Mudanças Manuais vs. Automáticas**: O evento é acionado apenas quando o usuário altera manualmente as configurações de idioma. Mudanças automáticas, como as feitas por meio de scripts ou configurações de sistema, podem não acionar o evento.
- **Desempenho**: Evite realizar operações pesadas dentro do manipulador de eventos, pois isso pode afetar o desempenho do seu aplicativo. Considere debouncing ou throttling se necessário.

## Resumo em Uma Linha
O evento `onlanguagechange` em JavaScript permite detectar e responder a mudanças no idioma do navegador do usuário em tempo real.