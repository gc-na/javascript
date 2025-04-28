<!--
Meta Description: # RegExp em JavaScript: Expressões Regulares para Manipulação de Texto ## Sinopse As expressões regulares (RegExp) em JavaScript são ferramentas poder...
Meta Keywords: javascript, const, expressões, regex, regexp
-->

# RegExp em JavaScript: Expressões Regulares para Manipulação de Texto

## Sinopse
As expressões regulares (RegExp) em JavaScript são ferramentas poderosas para busca e manipulação de textos, permitindo a validação, pesquisa e substituição de padrões em strings de forma eficiente.

## Documentação
As expressões regulares são objetos que permitem descrever padrões de texto. Em JavaScript, a classe `RegExp` é utilizada para criar e manipular essas expressões. Elas podem ser utilizadas para verificar se uma string corresponde a um padrão específico, assim como para substituir partes de uma string.

### Criação de uma RegExp
Em JavaScript, você pode criar uma RegExp de duas maneiras:
1. **Literal**: Usando barras (`/`).
   ```javascript
   const regex = /padrão/;
   ```
2. **Construtor**: Usando a função `RegExp`.
   ```javascript
   const regex = new RegExp('padrão');
   ```

### Métodos Principais
- **test()**: Retorna `true` se a string contém o padrão, `false` caso contrário.
  ```javascript
  const regex = /gato/;
  console.log(regex.test('Eu tenho um gato.')); // true
  ```
  
- **exec()**: Executa uma busca e retorna um array com os resultados ou `null`.
  ```javascript
  const regex = /gato/;
  console.log(regex.exec('Eu tenho um gato.')); // ["gato"]
  ```

### Flags
As expressões regulares podem conter modificadores (flags) que alteram seu comportamento:
- `i`: Ignorar maiúsculas e minúsculas.
- `g`: Busca global.
- `m`: Múltiplas linhas.

Exemplo com flags:
```javascript
const regex = /gato/i;
console.log(regex.test('Eu tenho um Gato.')); // true
```

## Exemplos
1. **Verificação de Email**:
   ```javascript
   const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
   console.log(emailRegex.test('exemplo@dominio.com')); // true
   ```

2. **Substituição de Texto**:
   ```javascript
   const texto = 'O céu é azul';
   const novoTexto = texto.replace(/azul/, 'vermelho');
   console.log(novoTexto); // 'O céu é vermelho'
   ```

3. **Extraindo Números**:
   ```javascript
   const str = 'A temperatura é de 25 graus.';
   const numeros = str.match(/\d+/g);
   console.log(numeros); // ['25']
   ```

## Explicação
Embora as expressões regulares sejam extremamente úteis, elas podem ser complexas e propensas a erros. Alguns dos principais cuidados incluem:

- **Escape de Caracteres Especiais**: Certifique-se de escapar caracteres que têm significados especiais, como `.` ou `*`, se você deseja que eles sejam tratados como literais.
- **Performance**: Expressões regulares complexas podem impactar a performance de sua aplicação, especialmente em strings longas.
- **Compatibilidade**: Algumas expressões podem se comportar de maneira diferente em outros ambientes ou versões do JavaScript, portanto, teste sempre em diferentes cenários.

## Resumo em Uma Linha
As expressões regulares em JavaScript são ferramentas versáteis para busca e manipulação de texto, permitindo validar e transformar strings de maneira eficiente.