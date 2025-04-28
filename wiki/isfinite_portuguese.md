<!--
Meta Description: # isFinite: Verificando a Finiteza de Valores em JavaScript ## Sinopse A função `isFinite` em JavaScript é utilizada para verificar se um valor é um n...
Meta Keywords: isfinite, valor, true, console, log
-->

# isFinite: Verificando a Finiteza de Valores em JavaScript

## Sinopse
A função `isFinite` em JavaScript é utilizada para verificar se um valor é um número finito. Essa função é essencial para validações numéricas e manipulações de dados em aplicações web.

## Documentação
A função `isFinite` é uma função global em JavaScript que determina se o valor passado como argumento é um número finito. Um número é considerado finito quando não é `Infinity`, `-Infinity` ou `NaN` (Not a Number).

### Sintaxe
```javascript
isFinite(valor);
```

### Parâmetros
- **valor**: O valor que se deseja verificar. Pode ser de qualquer tipo, incluindo números, strings, objetos, etc.

### Retorno
A função retorna um valor booleano:
- **true**: Se o valor é um número finito.
- **false**: Se o valor é `Infinity`, `-Infinity` ou `NaN`.

### Comportamento
A função `isFinite` primeiro converte o valor para um número, e então verifica se ele é finito.

## Exemplos

### Exemplo 1: Verificando números finitos
```javascript
console.log(isFinite(123)); // true
console.log(isFinite(-456)); // true
console.log(isFinite(0)); // true
```

### Exemplo 2: Valores não finitos
```javascript
console.log(isFinite(Infinity)); // false
console.log(isFinite(-Infinity)); // false
console.log(isFinite(NaN)); // false
```

### Exemplo 3: Strings e outros tipos
```javascript
console.log(isFinite("123")); // true (a string é convertida para número)
console.log(isFinite("abc")); // false (não é um número)
console.log(isFinite(true)); // true (true é convertido para 1)
console.log(isFinite(false)); // true (false é convertido para 0)
```

## Explicação
É importante notar que a função `isFinite` realiza uma conversão de tipo implícita, o que pode levar a resultados inesperados se não for usada com cuidado. Por exemplo, strings que não representam números irão resultar em `false`, enquanto strings numéricas serão convertidas e avaliadas como `true`. Isso pode causar confusão, especialmente ao trabalhar com dados de entrada do usuário.

Além disso, `isFinite` não deve ser confundido com a função `Number.isFinite`, que não realiza conversão de tipo e verifica estritamente se o valor é um número finito.

## Resumo em Uma Linha
A função `isFinite` em JavaScript verifica se um valor é um número finito, retornando `true` ou `false` conforme o caso.