<!--
Meta Description: # onreset: Manipulando o Evento de Reinicialização em Formulários JavaScript ## Sinopse O evento `onreset` em JavaScript é um manipulador de eventos q...
Meta Keywords: onreset, html, evento, formulário, javascript
-->

# onreset: Manipulando o Evento de Reinicialização em Formulários JavaScript

## Sinopse
O evento `onreset` em JavaScript é um manipulador de eventos que permite executar uma função específica quando um formulário HTML é reiniciado, ou seja, quando o usuário clica no botão de "reset". Este evento é útil para restaurar os valores padrão de um formulário.

## Documentação
O `onreset` é um evento que faz parte da interface de formulários em HTML e está associado ao elemento `<form>`. Ele pode ser utilizado para adicionar comportamentos personalizados quando um formulário é reiniciado.

### Propósito
O evento é acionado quando o método `reset()` é chamado ou quando um botão do tipo "reset" é clicado. O propósito principal é permitir que desenvolvedores possam implementar ações específicas antes ou após o formulário ser redefinido.

### Uso
Para utilizar o evento `onreset`, você pode atribuí-lo diretamente no HTML ou usar JavaScript para adicionar um ouvinte de eventos. Aqui está como você pode fazer isso:

**HTML:**
```html
<form onreset="meuManipulador()">
  <input type="text" name="nome" value="Seu Nome">
  <input type="reset" value="Reiniciar">
</form>
```

**JavaScript:**
```javascript
document.getElementById("meuFormulario").onreset = function() {
  meuManipulador();
};
```

## Exemplos
### Exemplo 1: Usando `onreset` em HTML
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de onreset</title>
</head>
<body>
    <form onreset="alert('O formulário foi reiniciado!')">
        <input type="text" name="nome" value="Seu Nome">
        <input type="reset" value="Reiniciar">
    </form>
</body>
</html>
```

### Exemplo 2: Usando `onreset` com JavaScript
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo de onreset com JavaScript</title>
</head>
<body>
    <form id="meuFormulario">
        <input type="text" name="nome" value="Seu Nome">
        <input type="reset" value="Reiniciar">
    </form>

    <script>
        document.getElementById("meuFormulario").onreset = function() {
            console.log("O formulário foi reiniciado!");
        };
    </script>
</body>
</html>
```

## Explicação
Embora o evento `onreset` seja bastante útil, é importante estar ciente de algumas considerações:

1. **Compatibilidade:** O evento é suportado na maioria dos navegadores modernos, mas sempre verifique a compatibilidade se estiver desenvolvendo para um público amplo.
   
2. **Interferência do Navegador:** Alguns navegadores podem não executar scripts se o formulário for reiniciado por meio de um botão de reset padrão. 

3. **Impacto na Experiência do Usuário:** Usar `onreset` para mostrar mensagens pode ser confuso para os usuários, que podem não esperar um alerta ao reiniciar um formulário.

4. **Limitações:** O evento `onreset` não é chamado se o formulário for redefinido por meio de JavaScript, a menos que você o faça manualmente.

## Resumo em Uma Linha
O evento `onreset` em JavaScript permite que desenvolvedores executem funções específicas quando um formulário é reiniciado, melhorando a interação do usuário.