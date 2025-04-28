<!--
Meta Description: # oninvalid: Validação de Formulários em JavaScript ## Sinopse O evento `oninvalid` em JavaScript é utilizado para capturar e gerenciar situações em q...
Meta Keywords: oninvalid, evento, validação, para, que
-->

# oninvalid: Validação de Formulários em JavaScript

## Sinopse
O evento `oninvalid` em JavaScript é utilizado para capturar e gerenciar situações em que um campo de entrada (input) de um formulário não atende às regras de validação definidas, permitindo que desenvolvedores exibam mensagens personalizadas ou realizem ações específicas quando a validação falha.

## Documentação
O evento `oninvalid` é um dos eventos de validação de formulários do HTML5, que pode ser utilizado em elementos `<input>`, `<textarea>`, e `<select>`. Quando um formulário é enviado e um campo não é válido, o evento `oninvalid` é disparado. Este evento pode ser tratado para fornecer feedback ao usuário ou evitar o envio do formulário.

### Propósito
O propósito do `oninvalid` é permitir que desenvolvedores capturem falhas de validação de forma programática, possibilitando uma experiência de usuário mais interativa e personalizada.

### Uso
Para usar o evento `oninvalid`, você pode adicioná-lo diretamente no elemento do formulário ou através de JavaScript. Aqui está a sintaxe básica:

```html
<input type="text" required oninvalid="handleInvalid(event)">
```

Ou usando JavaScript:

```javascript
document.querySelector('input').addEventListener('invalid', handleInvalid);

function handleInvalid(event) {
    // Lógica a ser executada quando o campo é inválido
}
```

### Detalhes
- O evento `oninvalid` é acionado após o evento de submissão do formulário.
- O método `setCustomValidity()` pode ser usado dentro do manipulador para definir mensagens de erro personalizadas.
- Para que o evento funcione corretamente, o campo deve ter algum tipo de validação (como `required`, `type`, `minlength`, etc.).

## Exemplos

### Exemplo 1: Uso Básico
```html
<form id="myForm">
    <label for="name">Nome:</label>
    <input type="text" id="name" required oninvalid="setCustomValidity('Por favor, preencha seu nome.')">
    <input type="submit" value="Enviar">
</form>
```

### Exemplo 2: Manipulação do Evento
```html
<form id="myForm">
    <label for="email">E-mail:</label>
    <input type="email" id="email" required>
    <input type="submit" value="Enviar">
</form>

<script>
document.getElementById('email').addEventListener('invalid', function(event) {
    event.preventDefault(); // Impede o envio do formulário
    alert('Por favor, insira um endereço de e-mail válido.');
});
</script>
```

## Explicação
Alguns pontos a considerar ao usar o evento `oninvalid`:

- **Validação Nativa**: O `oninvalid` é parte da validação nativa do HTML5, o que significa que, em muitos casos, não é necessário escrever código adicional para validação básica.
- **Customização da Mensagem**: Utilize `setCustomValidity()` para definir mensagens de erro personalizadas. Lembre-se de chamar `setCustomValidity('')` em campos válidos para remover a mensagem de erro.
- **Interatividade**: Ao manipular o evento, você pode fornecer feedback visual ao usuário, como destacar campos inválidos ou exibir mensagens de erro em um formato mais amigável.

## Resumo em Uma Linha
O evento `oninvalid` permite que desenvolvedores capturem e tratem falhas de validação em campos de formulários, melhorando a experiência do usuário em JavaScript.