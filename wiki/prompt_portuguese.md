<!--
Meta Description: # prompt em JavaScript: Como Utilizar e Exemplos Práticos ## Sinopse O comando `prompt` em JavaScript é utilizado para solicitar a entrada do usuário ...
Meta Keywords: prompt, usuário, uma, que, javascript
-->

# prompt em JavaScript: Como Utilizar e Exemplos Práticos

## Sinopse
O comando `prompt` em JavaScript é utilizado para solicitar a entrada do usuário por meio de uma caixa de diálogo. Esta função é frequentemente usada em aplicações web para coletar informações simples de forma interativa.

## Documentação
### Propósito
A função `prompt()` serve para exibir uma caixa de diálogo que contém uma mensagem e um campo de entrada, permitindo ao usuário inserir um valor. É uma maneira simples de interagir com o usuário sem a necessidade de criar elementos HTML complexos.

### Uso
A sintaxe básica da função `prompt` é a seguinte:

```javascript
let usuarioInput = prompt(mensagem, valorDefault);
```

- **mensagem**: Uma string que será exibida ao usuário, informando o que deve ser digitado.
- **valorDefault**: (opcional) Uma string que será exibida como valor padrão no campo de entrada.

A função retorna o valor inserido pelo usuário como uma string. Se o usuário cancelar a ação, `prompt` retorna `null`.

### Detalhes
O `prompt` é amplamente utilizado em ambientes de navegador e não está disponível em ambientes de execução de JavaScript em servidor, como Node.js. Além disso, a aparência da caixa de diálogo pode variar entre diferentes navegadores e sistemas operacionais, o que pode afetar a experiência do usuário.

## Exemplos
### Exemplo Básico
```javascript
let nome = prompt("Qual é o seu nome?");
alert("Olá, " + nome + "!");
```

Neste exemplo, o usuário é solicitado a inserir seu nome, e uma caixa de alerta exibe uma mensagem personalizada.

### Exemplo com Valor Padrão
```javascript
let idade = prompt("Quantos anos você tem?", "18");
alert("Você digitou: " + idade);
```

Aqui, o campo de entrada é pré-preenchido com o valor "18", que pode ser alterado pelo usuário.

## Explicação
### Armadilhas Comuns
- **Navegadores Bloqueando o Prompt**: Alguns navegadores têm bloqueadores de pop-ups que podem impedir a exibição do `prompt`. É importante testar em diferentes navegadores para garantir a funcionalidade.
- **Tipo de Dados**: O valor retornado por `prompt` é sempre uma string, mesmo que o usuário insira um número. Portanto, é necessário converter o valor, se necessário, usando `parseInt` ou `parseFloat`.
- **UX (Experiência do Usuário)**: O uso excessivo de `prompt` pode ser intrusivo e prejudicar a experiência do usuário. Considere alternativas como formulários HTML para interações mais complexas.

## Resumo em Uma Linha
A função `prompt` em JavaScript permite solicitar e capturar a entrada do usuário através de uma caixa de diálogo simples.