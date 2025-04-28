<!--
Meta Description: # Estilo de Folhas de Estilo (StyleSheet) em JavaScript ## Sinopse O objeto `StyleSheet` em JavaScript permite manipular folhas de estilo CSS de manei...
Meta Keywords: estilo, uma, css, stylesheet, que
-->

# Estilo de Folhas de Estilo (StyleSheet) em JavaScript

## Sinopse
O objeto `StyleSheet` em JavaScript permite manipular folhas de estilo CSS de maneira dinâmica, facilitando a alteração da aparência de elementos em uma página web durante a execução do código.

## Documentação
### O que é o objeto StyleSheet?
O objeto `StyleSheet` é uma representação de uma folha de estilo CSS em um documento. Ele pode ser utilizado para acessar, modificar ou remover regras de estilo em tempo real, proporcionando uma maneira poderosa de alterar a apresentação visual da sua aplicação sem precisar recarregar a página.

### Propósito
O principal propósito do `StyleSheet` é permitir que desenvolvedores façam ajustes dinâmicos no estilo dos elementos da página, influenciando diretamente a experiência do usuário.

### Uso
Para acessar folhas de estilo em um documento HTML, você pode utilizar a propriedade `styleSheets` do objeto `document`. O acesso ao objeto `StyleSheet` é feito através de um índice que representa a ordem das folhas de estilo no documento.

#### Sintaxe:
```javascript
let folhasDeEstilo = document.styleSheets;
```

### Propriedades Comuns
- `cssRules`: Retorna uma lista de regras CSS contidas na folha de estilo.
- `insertRule()`: Insere uma nova regra CSS na folha de estilo.
- `deleteRule()`: Remove uma regra CSS da folha de estilo.

## Exemplos
### Exemplo 1: Acessando e Listando Regras CSS
```javascript
let folhasDeEstilo = document.styleSheets;
for (let i = 0; i < folhasDeEstilo.length; i++) {
    let regras = folhasDeEstilo[i].cssRules;
    console.log(`Folha de Estilo ${i}:`);
    for (let j = 0; j < regras.length; j++) {
        console.log(regras[j].cssText);
    }
}
```

### Exemplo 2: Adicionando uma Nova Regra CSS
```javascript
let folhaDeEstilo = document.styleSheets[0]; // Acessa a primeira folha de estilo
folhaDeEstilo.insertRule("body { background-color: lightblue; }", folhaDeEstilo.cssRules.length);
```

### Exemplo 3: Removendo uma Regra CSS
```javascript
let folhaDeEstilo = document.styleSheets[0]; // Acessa a primeira folha de estilo
folhaDeEstilo.deleteRule(0); // Remove a primeira regra
```

## Explicação
### Armadilhas Comuns
- **Indexação de Folhas de Estilo**: Se você estiver manipulando várias folhas de estilo, lembre-se de que o índice começa em 0. Um erro comum é tentar acessar um índice que não existe.
- **Compatibilidade**: Algumas propriedades e métodos podem não ser suportados em todos os navegadores. Verifique a compatibilidade do navegador ao usar `insertRule()` e `deleteRule()`.
- **Regras de Estilo**: Ao adicionar regras, certifique-se de que a sintaxe CSS está correta para evitar erros que podem não ser facilmente identificáveis.

### Notas Adicionais
O uso do objeto `StyleSheet` pode ser muito útil em aplicações que requerem um ajuste dinâmico de estilo com base na interação do usuário ou em condições específicas.

## Resumo em Uma Linha
O objeto `StyleSheet` em JavaScript permite manipular folhas de estilo CSS dinamicamente, facilitando a customização da aparência de elementos em uma página web.