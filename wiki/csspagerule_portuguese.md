<!--
Meta Description: # CSSPageRule em JavaScript: Manipulando Regras de Estilos CSS ## Sinopse O `CSSPageRule` é uma interface do JavaScript que permite a manipulação de r...
Meta Keywords: regra, csspagerule, uma, estilos, que
-->

# CSSPageRule em JavaScript: Manipulando Regras de Estilos CSS

## Sinopse
O `CSSPageRule` é uma interface do JavaScript que permite a manipulação de regras de estilo CSS relacionadas a páginas em um documento. Essa interface é especialmente útil em contextos de impressão, onde o layout pode ser ajustado de acordo com diferentes páginas.

## Documentação
### O que é o CSSPageRule?
O `CSSPageRule` representa uma regra de estilo CSS que define o estilo de uma página específica em um documento. Ele é parte da interface CSSOM (CSS Object Model) e é utilizado principalmente em folhas de estilo que contenham regras de páginas, como `@page`.

### Propósito
O objetivo do `CSSPageRule` é permitir que os desenvolvedores manipulem e ajustem estilos de impressão, conferindo controle sobre como o conteúdo é exibido em diferentes páginas de um documento impresso.

### Uso
Um objeto `CSSPageRule` é criado automaticamente quando uma regra `@page` é adicionada a uma folha de estilos. Você pode acessar e modificar suas propriedades através do JavaScript, permitindo ajustes dinâmicos em tempo de execução.

### Propriedades Principais
- **selectorText**: Uma string que contém a representação textual do seletor da regra de página.
- **style**: Um objeto `CSSStyleDeclaration` que representa o conjunto de estilos aplicados a essa regra de página.

### Métodos
O `CSSPageRule` não possui métodos próprios, mas você pode manipular suas propriedades diretamente ao acessar a regra dentro de uma folha de estilos.

## Exemplos
### Exemplo Básico de Uso
```javascript
// Acessando a folha de estilos
let stylesheet = document.styleSheets[0];

// Adicionando uma regra @page
stylesheet.insertRule('@page { margin: 2cm; }', stylesheet.cssRules.length);

// Acessando a regra @page
let pageRule = stylesheet.cssRules[stylesheet.cssRules.length - 1];

// Modificando a margem da regra
pageRule.style.margin = '3cm';
```

### Exemplo de Acesso ao selectorText
```javascript
// Acessando a regra @page
let pageRule = stylesheet.cssRules[0];

// Exibindo o seletor da regra de página
console.log(pageRule.selectorText); // Saída: @page
```

## Explicação
### Armadilhas Comuns
1. **Compatibilidade do Navegador**: Nem todos os navegadores oferecem suporte completo ao `CSSPageRule`, especialmente em versões mais antigas. Sempre verifique a compatibilidade antes de implementar.
2. **Mudanças em tempo de execução**: Alterações feitas em regras de página podem não refletir imediatamente na visualização de impressão. É aconselhável realizar testes apropriados de impressão após modificações.
3. **Limitações de Estilo**: Algumas propriedades CSS podem não ser aplicáveis ou podem ter comportamentos diferentes em contextos de impressão. Verifique a documentação de CSS para estilos específicos.

## Resumo em Uma Frase
O `CSSPageRule` permite que desenvolvedores JavaScript manipulem regras de estilos CSS para impressão, proporcionando controle sobre o layout de páginas em documentos impressos.