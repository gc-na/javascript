<!--
Meta Description: # Comentários em JavaScript: Entenda a Importância e o Uso ## Sinopse Comentários em JavaScript são trechos de texto inseridos no código que não são e...
Meta Keywords: comentários, código, javascript, linha, comentário
-->

# Comentários em JavaScript: Entenda a Importância e o Uso

## Sinopse
Comentários em JavaScript são trechos de texto inseridos no código que não são executados pelo interpretador. Eles são utilizados para documentar o código, explicar a lógica por trás de implementações e facilitar a manutenção futura.

## Documentação
Os comentários em JavaScript podem ser de duas formas: comentários de linha única e comentários de múltiplas linhas.

### Comentários de Linha Única
Para criar um comentário de linha única, utiliza-se duas barras (`//`). Tudo que estiver após as barras na mesma linha será ignorado pelo interpretador.

**Exemplo:**
```javascript
// Este é um comentário de linha única
let x = 5; // Inicializa x com o valor 5
```

### Comentários de Múltiplas Linhas
Para criar um comentário que abrange várias linhas, utiliza-se `/*` para iniciar o comentário e `*/` para finalizá-lo. Todo o texto entre esses delimitadores será ignorado.

**Exemplo:**
```javascript
/*
Este é um comentário de múltiplas linhas.
Ele pode se estender por várias linhas.
*/
let y = 10; /* Inicializa y com o valor 10 */
```

## Exemplos
### Exemplo de Comentário de Linha Única
```javascript
// Calcula a soma de dois números
let a = 10; // Primeiro número
let b = 5;  // Segundo número
let soma = a + b; // Soma dos números
```

### Exemplo de Comentário de Múltiplas Linhas
```javascript
/*
Função que calcula a média de dois números
Recebe dois parâmetros: num1 e num2
Retorna a média aritmética
*/
function calcularMedia(num1, num2) {
    return (num1 + num2) / 2;
}
```

## Explicação
É importante usar comentários de forma eficaz. Comentários excessivos podem tornar o código confuso, enquanto a falta de comentários pode dificultar a compreensão do código por outros desenvolvedores ou até mesmo por você no futuro. 

### Armadilhas Comuns
- **Comentários Desatualizados:** Às vezes, os comentários não são atualizados após alterações no código, levando a confusões. Sempre revise os comentários ao modificar o código.
- **Comentários Óbvios:** Evite comentar algo que é evidente apenas pelo nome da variável ou pela lógica do código. Isso pode tornar o código mais difícil de ler.
  
## Resumo em Uma Linha
Comentários em JavaScript são essenciais para documentar o código e facilitar a compreensão, sem interferir na execução.