<!--
Meta Description: # HTMLTextAreaElement: Manipulação de Áreas de Texto em JavaScript ## Sinopse O `HTMLTextAreaElement` é uma interface em JavaScript que representa um ...
Meta Keywords: textarea, texto, html, que, htmltextareaelement
-->

# HTMLTextAreaElement: Manipulação de Áreas de Texto em JavaScript

## Sinopse
O `HTMLTextAreaElement` é uma interface em JavaScript que representa um elemento `<textarea>` em um documento HTML, permitindo a manipulação e interação com campos de texto de múltiplas linhas.

## Documentação
O `HTMLTextAreaElement` é utilizado para criar áreas de texto onde os usuários podem inserir dados. É uma parte fundamental em formulários da web, permitindo que os desenvolvedores capturem entradas de texto mais longas. 

### Propriedades e Métodos Principais
- **value**: Propriedade que obtém ou define o conteúdo textual do `<textarea>`.
- **rows**: Define o número de linhas visíveis no elemento.
- **cols**: Define o número de colunas visíveis no elemento.
- **placeholder**: Texto que aparece quando o campo está vazio, indicando o tipo de informação esperada.
- **disabled**: Propriedade booleana que indica se o campo deve estar desabilitado para interação.
- **focus()**: Método que coloca o foco no campo de texto.
- **select()**: Método que seleciona todo o texto contido no campo.

### Uso
Para usar o `HTMLTextAreaElement`, você deve primeiro referenciar o elemento no seu código JavaScript. Isso pode ser feito utilizando métodos como `document.getElementById()` ou `document.querySelector()`.

## Exemplos
### Exemplo 1: Criando um `<textarea>` e manipulando seu valor
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de HTMLTextAreaElement</title>
</head>
<body>
    <textarea id="meuTextarea" rows="4" cols="50" placeholder="Digite seu texto aqui..."></textarea>
    <button onclick="mostrarTexto()">Mostrar Texto</button>

    <script>
        function mostrarTexto() {
            const textarea = document.getElementById('meuTextarea');
            alert(textarea.value);
        }
    </script>
</body>
</html>
```

### Exemplo 2: Desabilitando um `<textarea>`
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Desabilitar TextArea</title>
</head>
<body>
    <textarea id="textareaDesabilitado" rows="4" cols="50" disabled></textarea>
    <button onclick="habilitarTextarea()">Habilitar Texto</button>

    <script>
        function habilitarTextarea() {
            const textarea = document.getElementById('textareaDesabilitado');
            textarea.disabled = false;
            textarea.focus();
        }
    </script>
</body>
</html>
```

## Explicação
Ao utilizar o `HTMLTextAreaElement`, é importante lembrar que:
- O valor inserido no `<textarea>` pode ser acessado diretamente pela propriedade `value`, mas não atualiza o DOM automaticamente quando o conteúdo é alterado. Para refletir as mudanças, você deve usar métodos como `setAttribute()` ou definir a propriedade `value` diretamente.
- Se um `<textarea>` estiver desabilitado (`disabled`), ele não será enviado com o formulário e não poderá ser editado pelo usuário.
- O uso de placeholders pode melhorar a experiência do usuário, mas deve ser utilizado com cuidado, pois não substitui a necessidade de rótulos claros para acessibilidade.

## Resumo em Uma Linha
O `HTMLTextAreaElement` em JavaScript permite a manipulação de campos de texto de múltiplas linhas em formulários, facilitando a captura de entradas mais longas de usuários.