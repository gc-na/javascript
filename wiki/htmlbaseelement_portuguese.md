<!--
Meta Description: # HTMLBaseElement: A Profundidade no Uso do Elemento Base em JavaScript ## Sinopse O `HTMLBaseElement` é uma interface do DOM que representa o element...
Meta Keywords: base, html, href, url, com
-->

# HTMLBaseElement: A Profundidade no Uso do Elemento Base em JavaScript

## Sinopse
O `HTMLBaseElement` é uma interface do DOM que representa o elemento `<base>` em um documento HTML. Este elemento define uma URL base para todas as URLs relativas contidas no documento, facilitando a navegação em páginas web.

## Documentação
O `HTMLBaseElement` é utilizado para especificar uma URL base que será aplicada a todas as URLs relativas dentro da página. Quando um elemento `<base>` é utilizado, qualquer link ou recurso que não contenha um caminho absoluto será resolvido em relação à URL fornecida no atributo `href` do elemento.

### Propriedades Principais:
- **href**: Uma propriedade que contém a URL base como uma string. Pode ser alterada dinamicamente via JavaScript.
- **target**: Uma propriedade que determina o alvo para onde os links devem ser abertos. Os valores comuns incluem `_self`, `_blank`, `_parent`, e `_top`.

### Uso:
O elemento `<base>` deve ser colocado dentro da seção `<head>` do documento HTML. Somente um elemento `<base>` pode ser definido por documento. Se múltiplos elementos `<base>` forem encontrados, apenas o primeiro será considerado.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de HTMLBaseElement</title>
    <base href="https://example.com/">
</head>
<body>
    <a href="pagina1.html">Link para Página 1</a>
    <a href="pagina2.html">Link para Página 2</a>
</body>
</html>
```

## Exemplos
### Exemplo 1: Definindo a URL Base
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de Base</title>
    <base href="https://meusite.com/">
</head>
<body>
    <a href="sobre.html">Sobre Nós</a>
    <a href="contato.html">Contato</a>
</body>
</html>
```
Neste exemplo, os links "Sobre Nós" e "Contato" serão resolvidos para `https://meusite.com/sobre.html` e `https://meusite.com/contato.html`, respectivamente.

### Exemplo 2: Alterando a URL Base com JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Alterando Base com JavaScript</title>
    <base id="base" href="https://example.com/">
</head>
<body>
    <a href="pagina.html">Página</a>
    <button onclick="alterarBase()">Alterar Base</button>
    
    <script>
        function alterarBase() {
            document.getElementById('base').href = 'https://outrosite.com/';
            alert('URL base alterada!');
        }
    </script>
</body>
</html>
```
Neste exemplo, ao clicar no botão, a URL base é alterada para `https://outrosite.com/`.

## Explicação
Um erro comum ao usar o `<base>` é não colocá-lo dentro da seção `<head>`. Além disso, se a URL base não for definida corretamente, isso pode causar problemas de resolução de links. Outro ponto a ser observado é que a alteração do `<base>` após o carregamento da página afetará apenas os links que são criados ou acessados após a mudança.

## Resumo em Uma Linha
O `HTMLBaseElement` define uma URL base para URLs relativas, facilitando a navegação e a gestão de links em um documento HTML.