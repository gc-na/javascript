<!--
Meta Description: # CSSFontFaceRule: Manipulação de Fontes em JavaScript ## Sinopse O `CSSFontFaceRule` é uma interface que permite a manipulação de regras de fonte den...
Meta Keywords: font, uma, cssfontfacerule, regra, fonte
-->

# CSSFontFaceRule: Manipulação de Fontes em JavaScript

## Sinopse
O `CSSFontFaceRule` é uma interface que permite a manipulação de regras de fonte dentro de um estilo CSS usando JavaScript, possibilitando a adição, remoção e modificação de fontes de forma dinâmica em aplicações web.

## Documentação
O `CSSFontFaceRule` é uma parte do Document Object Model (DOM) que representa uma regra `@font-face` em uma folha de estilo CSS. Essa regra é utilizada para definir fontes personalizadas que podem ser aplicadas a elementos HTML. A interface `CSSFontFaceRule` permite que desenvolvedores acessem e modifiquem propriedades como `font-family`, `src`, `font-style` e `font-weight`.

### Propósito
O principal propósito do `CSSFontFaceRule` é possibilitar a inclusão de fontes personalizadas em uma aplicação web, melhorando a tipografia e a estética visual da interface do usuário.

### Uso
Para utilizar `CSSFontFaceRule`, primeiro é necessário criar uma regra `@font-face` em um objeto `CSSStyleSheet`. Uma vez que a regra é criada, ela pode ser acessada e manipulada através do JavaScript.

Exemplo de estrutura de uma regra `@font-face`:
```css
@font-face {
  font-family: 'MinhaFonte';
  src: url('minha_fonte.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
}
```

### Propriedades
- **fontFamily**: Define o nome da fonte.
- **src**: Especifica a localização dos arquivos da fonte.
- **fontStyle**: Define o estilo da fonte (normal, itálico, etc.).
- **fontWeight**: Define o peso da fonte (normal, bold, etc.).

## Exemplos

### Exemplo Básico de Criação de uma Regra de Fonte
```javascript
const styleSheet = document.styleSheets[0];
const fontFaceRule = `@font-face {
  font-family: 'MinhaFonte';
  src: url('minha_fonte.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
}`;
styleSheet.insertRule(fontFaceRule, styleSheet.cssRules.length);
```

### Exemplo de Acesso e Modificação de uma Regra de Fonte
```javascript
const styleSheet = document.styleSheets[0];
const rule = styleSheet.cssRules[0]; // Acessando a primeira regra

if (rule instanceof CSSFontFaceRule) {
  rule.fontFamily = 'NovaFonte';
  rule.src = "url('nova_fonte.woff2') format('woff2')";
}
```

## Explicação
Uma armadilha comum ao trabalhar com `CSSFontFaceRule` é não verificar se a regra acessada realmente é uma `CSSFontFaceRule`. É importante usar o operador `instanceof` para garantir que você está trabalhando com o tipo correto de regra. Além disso, mudanças nas regras de fonte podem não ser refletidas imediatamente na interface do usuário se o cache do navegador não for atualizado, então, é aconselhável testar em diferentes navegadores.

## Resumo em Uma Linha
`CSSFontFaceRule` permite a manipulação dinâmica de regras de fonte em CSS via JavaScript, facilitando a personalização tipográfica em aplicações web.