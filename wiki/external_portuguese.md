<!--
Meta Description: # External: Entendendo o Uso de Recursos Externos em JavaScript ## Sinopse O termo "external" em JavaScript refere-se ao uso de recursos externos, com...
Meta Keywords: script, html, javascript, que, externos
-->

# External: Entendendo o Uso de Recursos Externos em JavaScript

## Sinopse
O termo "external" em JavaScript refere-se ao uso de recursos externos, como bibliotecas, scripts e estilos CSS, que podem ser integrados a uma aplicação web para expandir suas funcionalidades e melhorar a organização do código.

## Documentação
### Propósito
O uso de recursos externos em JavaScript permite que desenvolvedores aproveitem bibliotecas e frameworks já existentes, evitando a necessidade de reescrever código. Isso pode incluir bibliotecas de manipulação de DOM, frameworks de frontend, ou até mesmo arquivos CSS.

### Uso
Para incluir arquivos externos em uma aplicação JavaScript, geralmente utilizamos as tags `<script>` e `<link>` dentro do arquivo HTML. Abaixo estão as formas mais comuns de inclusão:

1. **Inclusão de JavaScript Externo:**
   ```html
   <script src="caminho/para/seu/script.js"></script>
   ```

2. **Inclusão de CSS Externo:**
   ```html
   <link rel="stylesheet" href="caminho/para/seu/estilo.css">
   ```

### Detalhes
- **Atributo `async` e `defer`:** Ao incluir scripts externos, é possível usar os atributos `async` e `defer` para controlar o carregamento dos scripts. O atributo `async` permite que o script seja executado assim que estiver carregado, enquanto `defer` garante que o script seja executado apenas após o carregamento completo da página.
  
```html
<script src="script.js" async></script>
<script src="script.js" defer></script>
```

## Exemplos
### Exemplo de Inclusão de JavaScript Externo
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de JavaScript Externo</title>
    <script src="meu-script.js"></script>
</head>
<body>
    <h1>Bem-vindo ao meu site!</h1>
</body>
</html>
```

### Exemplo de Inclusão de CSS Externo
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de CSS Externo</title>
    <link rel="stylesheet" href="meu-estilo.css">
</head>
<body>
    <h1>Bem-vindo ao meu site!</h1>
</body>
</html>
```

## Explicação
### Erros Comuns
- **Caminho Incorreto:** Um erro comum ao incluir arquivos externos é especificar um caminho incorreto para o arquivo. Isso resulta em um erro 404 (arquivo não encontrado).
- **Ordem de Carregamento:** A ordem em que os scripts e estilos são carregados pode afetar o funcionamento do seu código. Scripts que dependem de outros devem ser carregados na ordem correta.
- **Problemas de CORS:** Ao tentar carregar scripts de domínios diferentes, pode haver problemas relacionados ao CORS (Cross-Origin Resource Sharing), que precisa ser configurado adequadamente no servidor.

## Resumo em Uma Linha
O termo "external" em JavaScript refere-se à inclusão de recursos externos, como scripts e estilos, para melhorar a funcionalidade e a organização de uma aplicação web.